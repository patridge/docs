---
title: "&lt;issuer&gt; of &lt;issuedTokenParameters&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
---
# &lt;issuer&gt; of &lt;issuedTokenParameters&gt;
Specifies the Security Token Service (STS) that issues security tokens.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<security>  
\<issuedTokenParameters>  
\<issuer>  
  
## Syntax  
  
```  
  
<issuer address="Uri" />  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements  
  
### Attributes  
  
|Attribute|Description|  
|---------------|-----------------|  
|address|Required string. The URL of the STS.|  
  
### Child Elements  
  
|Element|Description|  
|-------------|-----------------|  
|[\<headers>](../../../../../docs/framework/configuring-apps/file-schema/wcf/headers-element.md)|A collection of address headers for the endpoints that the builder can create.|  
|[\<identity>](../../../../../docs/framework/configuring-apps/file-schema/wcf/identity.md)|When using an issued token, specifies settings that enable the client to authenticate the server.|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configuring-apps/file-schema/wcf/issuedtokenparameters.md)|Specifies the current issued token.|  
  
## See Also  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [Security Capabilities with Custom Bindings](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)   
 [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [Bindings](../../../../../docs/framework/wcf/bindings.md)   
 [Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding>](../../../../../docs/framework/configuring-apps/file-schema/wcf/custombinding.md)   
 [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [Custom Binding Security](../../../../../docs/framework/wcf/samples/custom-binding-security.md)