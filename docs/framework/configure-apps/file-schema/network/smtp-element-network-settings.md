---
title: "&lt;smtp&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<smtp> 項目"
  - "smtp 項目"
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;smtp&gt; 項目 (網路設定)
設定傳送電子郵件的傳遞格式、傳遞方法和來源地址。  
  
## 語法  
  
```  
  
      <smtp  
  deliveryFormat="format"   
  deliveryMethod="method"   
  from="from address"   
  <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
  <network> … </network>  
/smtp>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`deliveryFormat`|指定發送電子郵件的傳遞格式。  可接受的值為 SevenBit 和 International。|  
|`deliveryMethod`|指定電子郵件的傳遞方法。  可接受值為 network、pickupDirectoryFromIis 和 specifiedPickupDirectory。|  
|`from`|指定發送電子郵件的來源位址。|  
  
### 子項目  
  
|屬性|描述|  
|--------|--------|  
|`specifiedPickupDirectory`|針對 Simple Mail Transport Protocol \(SMTP\) 伺服器設定本機目錄。|  
|`network`|設定外部 SMTP 伺服器的網路選項。|  
  
### 父項目  
  
|**元素**|**描述**|  
|------------|------------|  
|[\<mailSettings\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|設定郵件傳送選項。|  
  
## 範例  
 下列範例中，程式碼會指定適當的 SMTP 參數，使用預設的網路認證傳送電子郵件。  
  
```  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
 <xref:System.Net.Configuration.SmtpSection?displayProperty=fullName>   
 <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>   
 <xref:System.Net.Mail.SmtpDeliveryFormat>   
 <xref:System.Net.Mail.SmtpDeliveryMethod>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)