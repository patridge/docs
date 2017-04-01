---
title: "ICorProfilerCallback::ThreadCreated Method | Microsoft Docs"
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
  - "ICorProfilerCallback.ThreadCreated"
apilocation: 
  - "mscorwks.dll"
apitype: "COM"
f1_keywords: 
  - "ICorProfilerCallback::ThreadCreated"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]"
  - "ThreadCreated method [.NET Framework profiling]"
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# ICorProfilerCallback::ThreadCreated Method
Notifies the profiler that a thread has been created.  
  
## Syntax  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
#### Parameters  
 `threadId`  
 [in] The ID of the thread that has been created.  
  
## Remarks  
 The `threadId` value is immediately valid.  
  
## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/getting-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## See Also  
 [ICorProfilerCallback Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)   
 [ThreadDestroyed Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)