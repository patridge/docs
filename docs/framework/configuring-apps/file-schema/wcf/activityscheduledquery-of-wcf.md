---
title: "&lt;activityScheduledQuery&gt; of WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
---
# &lt;activityScheduledQuery&gt; of WCF
Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity. The query is necessary for a tracking participant to subscribe to activity scheduled records.  
  
 For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/wf/tracking-profiles.md)  
  
 \<system.serviceModel>  
\<tracking>  
\<trackingProfile>  
\<workflow>  
\<activityScheduledQueries>  
\<activityScheduledQuery>  
  
## Syntax  
  
```vb  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Description|  
|---------------|-----------------|  
|activityName|A string that specifies the name of the activity that is requesting the cancellation.|  
|childActivityName|A string that specifies the name of the child activity for which cancellation was requested.|  
  
### Child Elements  
 None.  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](../../../../../docs/framework/configuring-apps/file-schema/wf/activityscheduledquery.md)|A query that is used to track an activity scheduled for execution by a parent activity.|  
  
## See Also  
 [System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement](assetId:///System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?qualifyHint=False&amp;autoUpgrade=True)   
 [System.Activities.Tracking.ActivityScheduledQuery](assetId:///System.Activities.Tracking.ActivityScheduledQuery?qualifyHint=False&amp;autoUpgrade=True)   
 [Workflow Tracking and Tracing](../../../../../docs/framework/wf/workflow-tracking-and-tracing.md)   
 [Tracking Profiles](../../../../../docs/framework/wf/tracking-profiles.md)