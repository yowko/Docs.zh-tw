---
title: "webRequestModules 的 &lt;clear&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<clear> 項目, webRequestModules"
  - "<webRequestModules>, clear 項目"
  - "clear 項目, webRequestModules"
  - "webRequestModules, clear 項目"
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# webRequestModules 的 &lt;clear&gt; 項目 (網路設定)
移除應用程式中所有已註冊的 Web 要求模組。  
  
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
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|指定向網路主機要求資訊所使用的模組。|  
  
## 備註  
 `clear` 項目會移除先前已在組態檔或組態階層架構更高層級中定義的所有已註冊 Web 要求模組。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例會清除所有的 Web 要求模組，然後註冊 HTTP 的 Web 要求模組。  
  
```  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.WebRequest>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)