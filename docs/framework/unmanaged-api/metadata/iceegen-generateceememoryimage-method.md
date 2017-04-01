---
title: "ICeeGen::GenerateCeeMemoryImage Method | Microsoft Docs"
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
  - "ICeeGen.GenerateCeeMemoryImage"
apilocation: 
  - "mscoree.dll"
apitype: "COM"
f1_keywords: 
  - "ICeeGen::GenerateCeeMemoryImage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICeeGen::GenerateCeeMemoryImage method [.NET Framework metadata]"
  - "GenerateCeeMemoryImage method [.NET Framework metadata]"
ms.assetid: b3847495-0ae6-4a72-b496-65ce2424afc6
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# ICeeGen::GenerateCeeMemoryImage Method
Generates an image in memory for the code base.  
  
 This method is obsolete and should not be used.  
  
## Syntax  
  
```  
HRESULT GenerateCeeMemoryImage (  
    [out] void    **ppImage  
);  
```  
  
#### Parameters  
 `ppImage`  
 [out] A pointer to the generated image.  
  
## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/getting-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## See Also  
 [ICeeGen Interface](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)