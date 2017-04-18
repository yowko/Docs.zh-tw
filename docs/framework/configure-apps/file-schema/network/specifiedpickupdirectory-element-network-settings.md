---
title: "&lt;specifiedPickupDirectory&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<specifiedPickupDirectory> 項目"
  - "specifiedPickupDirectory 項目"
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# &lt;specifiedPickupDirectory&gt; 項目 (網路設定)
針對 Simple Mail Transport Protocol \(SMTP\) 伺服器設定本機目錄。  
  
## 語法  
  
```  
  
      <specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`pickupDirectoryLocation`|應用程式儲存電子郵件的目錄，讓 SMTP 伺服器稍後可以處理這些郵件。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|[\<smtp\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|設定 Simple Mail Transport Protocol \(SMTP\) 郵件傳送選項。|  
  
## 備註  
 `specifiedPickupDirectory` 屬性會設定目錄，讓應用程式儲存郵件以供 SMTP 伺服器稍後處理。  
  
## 範例  
 下列程式碼範例指定 c:\\maildrop 做為郵件收取目錄。  
  
```  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="specifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>   
 <xref:System.Net.Configuration.SmtpSection?displayProperty=fullName>   
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)