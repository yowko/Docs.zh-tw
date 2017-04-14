---
title: "&lt;customCookieHandler&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# &lt;customCookieHandler&gt;
設定自訂的 cookie 的處理常式型別。  這個項目可能只會顯示如果`mode`屬性的`<cookieHandler>`項目是 \[自訂\]。  自訂型別必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。  
  
## 語法  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode=”Custom”>  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|type|指定的自訂型別是衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。  如需有關如何指定`type`屬性，請參閱[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。|  
  
### 子項目  
 None  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<cookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|設定<xref:System.IdentityModel.Services.CookieHandler> ， <xref:System.IdentityModel.Services.SessionAuthenticationModule>用來讀取和寫入 cookie。|  
  
## 備註  
 當您藉由設定指定自訂的 cookie 的處理常式時`mode`屬性的`<cookieHandler>`項目為 \[自訂\]，您必須指定自訂的 cookie 處理常式的型別，藉由加入`<customCookieHandler>`參考 cookie 的處理常式類型的子項目。  這個項目不能指定何時`mode`屬性設定為 「 區塊 」 或 \[預設\]。  自訂的 cookie 的處理常式必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。  
  
 `<customCookieHandler>`項目會以<xref:System.IdentityModel.Configuration.CustomTypeElement>類別。  
  
## 範例  
 以下範例將設定使用自訂的 cookie 的處理常式型別的 SAM `MyNamespace.MyCustomCookieHandler`。  
  
```  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Services.CookieHandler>