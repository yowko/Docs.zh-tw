---
title: "authenticationModules 的 &lt;clear&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<authenticationModules>, clear 項目"
  - "<clear> 項目, authenticationModules"
  - "authenticationModules, clear 項目"
  - "clear 項目, authenticationModules"
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# authenticationModules 的 &lt;clear&gt; 項目 (網路設定)
從應用程式清除所有驗證模組。  
  
## 語法  
  
```  
  
<clear/>  
  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[authenticationModules](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|指定用於驗證網路要求的模組。|  
  
## 備註  
 `clear` 項目會移除在組態檔之前或組態階層中更高層級定義的所有驗證模組。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例會移除所有設定的驗證模組。  
  
```  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.IAuthenticationModule>   
 <xref:System.Net.AuthenticationManager>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)