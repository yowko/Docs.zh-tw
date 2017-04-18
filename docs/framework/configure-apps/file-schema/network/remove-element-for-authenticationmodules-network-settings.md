---
title: "authenticationModules 的 &lt;remove&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<authenticationModules>, remove 項目"
  - "<remove> 項目, authenticationModules"
  - "authenticationModules, remove 項目"
  - "remove 項目, authenticationModules"
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# authenticationModules 的 &lt;remove&gt; 項目 (網路設定)
從應用程式移除驗證模組。  
  
## 語法  
  
```  
  
      <remove   
   name = "authentication module name"   
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**說明**|  
|------------|------------|  
|**name**|要移除的驗證模組的名稱。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[authenticationModules](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|指定用於驗證網路要求的模組。|  
  
## 備註  
 `remove` 項目會移除在組態檔之前或組態階層中更高層級定義的驗證模組。  
  
 `name` 屬性的值必須是有效的類別名稱。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例會移除驗證模組。  
  
```  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove name = "System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.IAuthenticationModule>   
 <xref:System.Net.AuthenticationManager>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)