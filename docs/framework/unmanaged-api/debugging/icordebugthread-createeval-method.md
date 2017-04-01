---
title: "ICorDebugThread::CreateEval Method | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: 
  - "ICorDebugThread.CreateEval"
apilocation: 
  - "mscordbi.dll"
apitype: "COM"
f1_keywords: 
  - "ICorDebugThread::CreateEval"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateEval method [.NET Framework debugging]"
  - "ICorDebugThread::CreateEval method [.NET Framework debugging]"
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# ICorDebugThread::CreateEval Method
Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.  
  
## Syntax  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### Parameters  
 `ppEval`  
 [out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.  
  
## Remarks  
 The evaluation object will push a new chain on the thread before doing its computation. This interrupts the computation currently being performed on the thread until the evaluation completes.  
  
## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/getting-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]