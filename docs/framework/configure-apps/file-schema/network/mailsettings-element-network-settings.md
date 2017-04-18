---
title: "&lt;mailSettings&gt; 項目 (網路設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<mailSettings> 項目"
  - "mailSettings 項目"
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;mailSettings&gt; 項目 (網路設定)
設定郵件傳送選項。  
  
## 語法  
  
```  
  
      <mailSettings  
  <smtp> … </smtp>  
/mailsettings>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|屬性|描述|  
|--------|--------|  
|[\<smtp\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|設定 Simple Mail Transport Protocol 選項。|  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[\<system.net\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含指定 .NET Framework 如何連接至網路的設定。|  
  
## 範例  
 下列範例中，程式碼會指定適當的 SMTP 參數，使用預設的網路認證傳送電子郵件。  
  
```  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.Mail.SmtpClient>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)