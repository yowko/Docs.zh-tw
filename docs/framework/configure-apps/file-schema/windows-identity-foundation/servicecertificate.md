---
title: "&lt;serviceCertificate&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;serviceCertificate&gt;
設定用來加密和解密語彙基元的 X.509 憑證。  
  
## 語法  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 None  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<certificateReference\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|指定用來找出並驗證 x.509 憑證存放區中的設定。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|包含設定的<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\)。|  
  
## 範例  
 下列 XML 程式碼會顯示 \<serviceCertificate\> 的使用方式 項目。  XML 來自`CustomToken`範例。  
  
```  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```