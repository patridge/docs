---
title: "ISymUnmanagedBinder Interface | Microsoft Docs"
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
  - "ISymUnmanagedBinder"
apilocation: 
  - "diasymreader.dll"
apitype: "COM"
f1_keywords: 
  - "ISymUnmanagedBinder"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISymUnmanagedBinder interface [.NET Framework debugging]"
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# ISymUnmanagedBinder Interface
Represents a symbol binder for unmanaged code.  
  
> [!IMPORTANT]
>  It is a security risk to open a program database (PDB) file from an untrusted source.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|[GetReaderForFile Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|Given a metadata interface and a file name, returns the correct <xref:ISymUnmanagedReader> structure that will read the debugging symbols associated with the module.|  
|[GetReaderFromStream Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|Given a metadata interface and a stream that contains the symbol store, returns the correct <xref:ISymUnmanagedReader> structure that will read the debugging symbols from the given symbol store.|  
  
## Requirements  
 **Header:** CorSym.idl, CorSym.h  
  
## See Also  
 [Diagnostics Symbol Store Interfaces](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)   
 [ISymUnmanagedBinder2 Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)   
 [ISymUnmanagedBinder3 Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)