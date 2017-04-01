---
title: "IInstallReferenceEnum Interface | Microsoft Docs"
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
  - "IInstallReferenceEnum"
apilocation: 
  - "fusion.dll"
apitype: "COM"
f1_keywords: 
  - "IInstallReferenceEnum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IInstallReferenceEnum interface [.NET Framework fusion]"
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# IInstallReferenceEnum Interface
Represents an enumerator for the referenced assemblies installed in the global assembly cache.  
  
## Syntax  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|[GetNextInstallReferenceItem Method](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.|  
  
## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/getting-started/system-requirements.md).  
  
 **Header:** Fusion.h  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## See Also  
 [Fusion Interfaces](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)   
 [IInstallReferenceItem Interface](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)