---
title: "&lt;serviceTokenResolver&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;serviceTokenResolver&gt;
註冊服務權杖解析程式所使用的語彙基元的處理常式集合中的處理常式。  權杖解析程式服務用來解析加密上的語彙基元連入的語彙基元和訊息。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|type|指定服務權杖解析的型別。  不論是哪一<xref:System.IdentityModel.Selectors.SecurityTokenResolver>型別或衍生自型別<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類別。  如需有關如何指定`type`屬性，請參閱[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。  必要項。|  
  
### 子項目  
 None  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供組態集合的安全性語彙基元的處理常式。|  
  
## 備註  
 權杖解析程式服務可用來解決加密上的語彙基元連入的語彙基元和訊息。  它用來擷取的機碼，應該用來解密連入的語彙基元。  您必須指定`type`屬性。  指定的型別可以是<xref:System.IdentityModel.Selectors.SecurityTokenResolver>或自訂的型別衍生自<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類別。  
  
 某些語彙基元的處理常式可讓您在組態中指定服務權杖解析程式設定。  在個別的語彙基元處理常式的設定會覆寫安全性語彙基元的處理常式集合上指定。  
  
> [!NOTE]
>  指定`<serviceTokenResolver>`項目做為子項目， [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍然支援回溯相容性。  設定在`<securityTokenHandlerConfiguration>`項目會覆寫那些在`<identityConfiguration>`項目。  
  
## 範例  
  
```  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```