---
title: "LINQ Considerations (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, LINQ"
  - "querying the data service [WCF Data Services]"
  - "WCF Data Services, querying"
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
---
# LINQ Considerations (WCF Data Services)
This topic provides information about the way in which LINQ queries are composed and executed when you are using the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client and limitations of using LINQ to query a data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] composing and executing queries against an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based data service, see [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## Composing LINQ Queries  
 LINQ enables you to compose queries against a collection of objects that implements <xref:System.Collections.Generic.IEnumerable%601>. Both the **Add Service Reference** dialog box in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and the DataSvcUtil.exe tool are used to generate a representation of an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>, as well as objects that represent the entities returned in feeds. These tools also generate properties on the entity container class for the collections that are exposed as feeds by the service. Each of these properties of the class that encapsulates the data service return a <xref:System.Data.Services.Client.DataServiceQuery%601>. Because the <xref:System.Data.Services.Client.DataServiceQuery%601> class implements the <xref:System.Linq.IQueryable%601> interface defined by LINQ, you can compose a LINQ query against feeds exposed by the data service, which are translated by the client library into a query request URI that is sent to the data service on execution.  
  
> [!IMPORTANT]
>  The set of queries expressible in the LINQ syntax is broader than those enabled in the URI syntax that is used by [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] data services. A <xref:System.NotSupportedException> is raised when the query cannot be mapped to a URI in the target data service. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] the [Unsupported LINQ Methods](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods) in this topic.  
  
 The following example is a LINQ query that returns `Orders` that have a freight cost of more than $30 and sorts the results by the shipping date, starting with the latest ship date:  
  
<!-- TODO: review snippet reference  [!CODE [Astoria NorthwindClient#AddQueryOptionsLinqSpecific](Astoria NorthwindClient#AddQueryOptionsLinqSpecific)]  -->  
  
 This LINQ query is translated into the following query URI that is executed against the Northwind-based [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) data service:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 For more general information about LINQ, see [LINQ (Language-Integrated Query)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  
  
 LINQ enables you to compose queries by using both the language-specific declarative query syntax, shown in the previous example, as well as a set of query methods known as standard query operators. An equivalent query to the previous example can be composed by using only the method-based syntax, as shown the following example:  
  
<!-- TODO: review snippet reference  [!CODE [Astoria NorthwindClient#AddQueryOptionsLinqExpressionSpecific](Astoria NorthwindClient#AddQueryOptionsLinqExpressionSpecific)]  -->  
  
 The [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client is able to translate both kinds of composed queries into a query URI, and you can extend a LINQ query by appending query methods to a query expression. When you compose LINQ queries by appending method syntax to a query expression or a <xref:System.Data.Services.Client.DataServiceQuery%601>, the operations are added to the query URI in the order in which methods are called. This is equivalent to calling the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method to add each query option to the query URI.  
  
## Executing LINQ Queries  
 Certain LINQ query methods, such as <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> or <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, when appended to the query, cause the query to be executed. A query is also executed when results are enumerated implicitly, such as during a `foreach` loop or when the query is assigned to a `List` collection. For more information, see [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 The client executes a LINQ query in two parts. Whenever possible, LINQ expressions in a query are first evaluated on the client, and then a URI-based query is generated and sent to the data service for evaluation against data in the service. For more information, see the section [Client versus Server Execution](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries) in [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 When a LINQ query cannot be translated in an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-compliant query URI, an exception is raised when execution is attempted. For more information, see [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## LINQ Query Examples  
 The examples in the following sections demonstrate the kinds of LINQ queries that can be executed against an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service.  
  
<a name="filtering"></a>   
### Filtering  
 The LINQ query examples in this section filter data in the feed returned by the service.  
  
 The following examples are equivalent queries that filter the returned `Orders` entities so that only orders with a freight cost greater than $30 are returned:  
  
-   Using LINQ query syntax:  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#LinqWhereClauseSpecific](Astoria NorthwindClient#LinqWhereClauseSpecific)]  -->  
  
-   Using LINQ query methods:  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#LinqWhereMethodSpecific](Astoria NorthwindClient#LinqWhereMethodSpecific)]  -->  
  
-   The URI query string `$filter` option:  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#ExplicitQueryWhereMethodSpecific](Astoria NorthwindClient#ExplicitQueryWhereMethodSpecific)]  -->  
  
 All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>   
### Sorting  
 The following examples show equivalent queries that sort returned data both by the company name and by postal code, descending:  
  
-   Using LINQ query syntax:  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#LinqOrderByClauseSpecific](Astoria NorthwindClient#LinqOrderByClauseSpecific)]  -->  
  
-   Using LINQ query methods:  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#LinqOrderByMethodSpecific](Astoria NorthwindClient#LinqOrderByMethodSpecific)]  -->  
  
-   URI query string `$orderby` option):  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#ExplicitQueryOrderByMethodSpecific](Astoria NorthwindClient#ExplicitQueryOrderByMethodSpecific)]  -->  
  
 All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### Projection  
 The following examples show equivalent queries that project returned data into the narrower `CustomerAddress` type:  
  
-   Using LINQ query syntax:  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#LinqSelectClauseSpecific](Astoria NorthwindClient#LinqSelectClauseSpecific)]  -->  
  
-   Using LINQ query methods:  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#LinqSelectMethodSpecific](Astoria NorthwindClient#LinqSelectMethodSpecific)]  -->  
  
> [!NOTE]
>  The `$select` query option cannot be added to a query URI by using the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method. We recommend that you use the LINQ <xref:System.Linq.Enumerable.Select%2A> method to have the client generate the `$select` query option in the request URI.  
  
 Both of the previous examples are translated to the query URI: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### Client Paging  
 The following examples show equivalent queries that request a page of sorted order entities that includes 25 orders, skipping the first 50 orders:  
  
-   Applying query methods to a LINQ query:  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#LinqSkipTakeMethodSpecific](Astoria NorthwindClient#LinqSkipTakeMethodSpecific)]  -->  
  
-   URI query string `$skip` and `$top` options):  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#ExplicitQuerySkipTakeMethodSpecific](Astoria NorthwindClient#ExplicitQuerySkipTakeMethodSpecific)]  -->  
  
 Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### Expand  
 When you query an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] data service, you can request that entities related to the entity targeted by the query be included the returned feed. The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is called on the <xref:System.Data.Services.Client.DataServiceQuery%601> for the entity set targeted by the LINQ query, with the related entity set name supplied as the `path` parameter. For more information, see [Loading Deferred Content](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 The following examples show equivalent ways to use the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method in a query:  
  
-   In LINQ query syntax:  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#LinqQueryExpandSpecific](Astoria NorthwindClient#LinqQueryExpandSpecific)]  -->  
  
-   With LINQ query methods:  
  
<!-- TODO: review snippet reference      [!CODE [Astoria NorthwindClient#LinqQueryExpandMethodSpecific](Astoria NorthwindClient#LinqQueryExpandMethodSpecific)]  -->  
  
 Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## Unsupported LINQ Methods  
 The following table contains the classes of LINQ methods are not supported and cannot be included in a query executed against an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service:  
  
|Operation Type|Unsupported Method|  
|--------------------|------------------------|  
|Set operators|All set operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, which included the following:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Ordering operators|The following ordering operators that require <xref:System.Collections.Generic.IComparer%601> are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Projection and filtering operators|The following projection and filtering operators that accept a positional argument are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Grouping operators|All grouping operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Grouping operations must be performed on the client.|  
|Aggregate operators|All aggregate operations are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Aggregate operations must either be performed on the client or be encapsulated by a service operation.|  
|Paging operators|The following paging operators are not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A> **Note:**  Paging operators that are executed on an empty sequence return null.|  
|Other operators|The following other operators are not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## Supported Expression Functions  
 The following common-language runtime (CLR) methods and properties are supported because they can be translated in a query expression for inclusion in the request URI to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service:  
  
|<xref:System.String> Member|Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<xref:System.DateTime> Member<sup>1</sup>|Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup>The equivalent date and time properties of <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=fullName>, as well as the <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> method in Visual Basic are also supported.  
  
|<xref:System.Math> Member|Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:> System.Linq.Expressions.Expression?qualifyHint=False&autoUpgrade=True Member|Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 The client may also be able to evaluate additional CLR functions on the client. A <xref:System.NotSupportedException> is raised for any expression that cannot be evaluated on the client and cannot be translated into a valid request URI for evaluation on the server.  
  
## See Also  
 [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)   
 [Query Projections](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)   
 [Object Materialization](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)   
 [OData: URI Conventions](http://go.microsoft.com/fwlink/?LinkID=185564)