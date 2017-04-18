---
title: "&lt;certificateValidator&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;certificateValidator&gt;
指定為憑證驗證的自訂型別。  只有當使用這個型別`certificateValidationMode`屬性的[\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)元素設為 \[自訂\]。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|type|指定的自訂型別是衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>類別。  設定`certificateValidationMode`屬性的[\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)為 \[自訂\]，若要使用這種類型的項目。  如需有關如何指定`type`屬性，請參閱[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。  選擇項。|  
  
### 子項目  
 None  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|控制的設定，用來驗證憑證的語彙基元的處理常式。|  
  
## 範例  
  
```  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```