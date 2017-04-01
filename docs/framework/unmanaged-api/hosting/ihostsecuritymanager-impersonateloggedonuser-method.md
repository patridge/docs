---
title: "IHostSecurityManager::ImpersonateLoggedOnUser Method | Microsoft Docs"
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
  - "IHostSecurityManager.ImpersonateLoggedOnUser"
apilocation: 
  - "mscoree.dll"
apitype: "COM"
f1_keywords: 
  - "IHostSecurityManager::ImpersonateLoggedOnUser"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ImpersonateLoggedOnUser method [.NET Framework hosting]"
  - "IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]"
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# IHostSecurityManager::ImpersonateLoggedOnUser Method
Requests that code be executed using the credentials of the current user identity.  
  
## Syntax  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
#### Parameters  
 `hToken`  
 [in] A token representing the credentials of the user to be impersonated.  
  
## Return Value  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ImpersonateLoggedOnUser` returned successfully.|  
|HOST_E_CLRNOTAVAILABLE|The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.|  
|HOST_E_TIMEOUT|The call timed out.|  
|HOST_E_NOT_OWNER|The caller does not own the lock.|  
|HOST_E_ABANDONED|An event was canceled while a blocked thread or fiber was waiting on it.|  
|E_FAIL|An unknown catastrophic failure occurred. When a method returns E_FAIL, the CLR is no longer usable within the process. Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.|  
  
## Remarks  
 Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.  
  
 The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling. Thus, this token is for use only within the process, between the CLR and the host.  
  
## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/getting-started/system-requirements.md).  
  
 **Header:** MSCorEE.h  
  
 **Library:** Included as a resource in MSCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## See Also  
 [IHostSecurityContext Interface](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)   
 [IHostSecurityManager Interface](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)   
 [RevertToSelf Method](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)