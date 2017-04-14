---
title: "&lt;authenticationModules&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<authenticationModules> 項目"
  - "authenticationModules 項目"
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# &lt;authenticationModules&gt; 項目 (網路設定)
指定用於驗證網路要求的模組。  
  
## 語法  
  
```  
  
      <authenticationModules>   
</authenticationModules>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[加入](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|加入驗證模組至應用程式。|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|從應用程式清除所有驗證模組。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|從應用程式移除驗證模組。|  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含指定 .NET Framework 如何連接至網路的設定。|  
  
## 備註  
 `authenticationModule` 項目指定使用伺服器執行驗證處理的驗證模組。  驗證模組必須實作 <xref:System.Net.IAuthenticationModule> 介面。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例啟用驗證模組。  您應該將 Version 和 PublicKeyToken 的值取代成指定之模組的正確值。  
  
```  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.IAuthenticationModule>   
 <xref:System.Net.AuthenticationManager>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)