---
title: "ICorPublishEnum::Skip Method | Microsoft Docs"
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
  - "ICorPublishEnum.Skip"
apilocation: 
  - "mscordbi.dll"
apitype: "COM"
f1_keywords: 
  - "ICorPublishEnum::Skip"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICorPublishEnum::Skip method [.NET Framework debugging]"
  - "Skip method, ICorDebugEnum interface [.NET Framework debugging]"
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# ICorPublishEnum::Skip Method
Moves the cursor forward in the enumeration by the specified number of items.  
  
## Syntax  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### Parameters  
 `celt`  
 [in] The number of items by which to move the cursor forward.  
  
## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/getting-started/system-requirements.md).  
  
 **Header:** CorPub.idl, CorPub.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## See Also  
 [ICorPublishEnum Interface](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)