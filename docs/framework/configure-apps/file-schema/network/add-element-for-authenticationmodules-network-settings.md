---
title: "authenticationModules 的 &lt;add&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#add"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> 項目, authenticationModules"
  - "<authenticationModules>, add 項目"
  - "add 項目, authenticationModules"
  - "authenticationModules, add 項目"
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# authenticationModules 的 &lt;add&gt; 項目 (網路設定)
加入驗證模組至應用程式。  
  
## 語法  
  
```  
  
      <add   
   type = "client type", System, Version="version number", Culture="culture", PublicKeyToken="token"   
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**說明**|  
|------------|------------|  
|`type`|實作驗證之模組的類別名稱和規格。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[authenticationModules](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|指定用於驗證網路要求的模組。|  
  
## 備註  
 `add` 項目會將驗證模組加入至已註冊之驗證模組清單的尾端。  驗證模組會以其加入至清單的順序依序呼叫。  
  
 `type` 屬性的值必須是有效的 DLL 名稱和對應的類別名稱，並且以逗號分隔。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例啟用預設的驗證模組。  您應該將 Version 和 PublicKeyToken 的值取代成指定之模組的正確值。  
  
```  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.IAuthenticationModule>   
 <xref:System.Net.AuthenticationManager>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)