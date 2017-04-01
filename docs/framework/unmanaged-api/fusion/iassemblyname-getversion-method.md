---
title: "IAssemblyName::GetVersion Method | Microsoft Docs"
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
  - "IAssemblyName.GetVersion"
apilocation: 
  - "fusion.dll"
apitype: "COM"
f1_keywords: 
  - "IAssemblyName::GetVersion"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAssemblyName::GetVersion method [.NET Framework fusion]"
  - "GetVersion method, IAssemblyName interface [.NET Framework fusion]"
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# IAssemblyName::GetVersion Method
Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.  
  
## Syntax  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
#### Parameters  
 `pdwVersionHi`  
 [out] The high 32 bits of the version.  
  
 `pdwVersionLow`  
 [out] The low 32 bits of the version.  
  
## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/getting-started/system-requirements.md).  
  
 **Header:** Fusion.h  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## See Also  
 [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)