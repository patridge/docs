---
title: "Numeric and Comparison Operators | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Numeric and Comparison Operators
Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:  
  
-   SQL does not support the modulus operator on floating-point numbers.  
  
-   SQL does not support unchecked arithmetic.  
  
-   Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.  
  
## Supported Operators  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports the following operators.  
  
-   Basic arithmetic operators:  
  
    -   `+`  
  
    -   `-` (subtraction)  
  
    -   `*`  
  
    -   `/`  
  
    -   Visual Basic integer division (`\`)  
  
    -   `%` (Visual Basic `Mod`)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` (unary negation)  
  
-   Basic comparison operators:  
  
    -   Visual Basic `=` and C# `==`  
  
    -   Visual Basic `<>` and C# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## See Also  
 [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)   
 [C# Operators](../Topic/C%23%20Operators.md)   
 [Operators](../Topic/Operators%20\(Visual%20Basic\).md)