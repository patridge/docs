---
title: "ICorDebugChain::GetActiveFrame Method | Microsoft Docs"
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
  - "ICorDebugChain.GetActiveFrame"
apilocation: 
  - "mscordbi.dll"
apitype: "COM"
f1_keywords: 
  - "ICorDebugChain::GetActiveFrame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICorDebugChain::GetActiveFrame method [.NET Framework debugging]"
  - "GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]"
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# ICorDebugChain::GetActiveFrame Method
Gets the active (that is, most recent) frame on the chain.  
  
## Syntax  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### Parameters  
 `ppFrame`  
 [out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.  
  
## Remarks  
 If no managed stack frame is available, `ppFrame` is set to null.  
  
 If the active frame is not available, the call will succeed and `ppFrame` will be null. Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT. See the CorDebugChainReason enumeration.  
  
## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/getting-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]