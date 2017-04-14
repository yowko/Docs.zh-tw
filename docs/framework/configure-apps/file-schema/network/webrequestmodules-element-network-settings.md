---
title: "&lt;webRequestModules&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<webRequestModules> 項目"
  - "webRequestModules 項目"
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;webRequestModules&gt; 項目 (網路設定)
指定向網路主機要求資訊所使用的模組。  
  
## 語法  
  
```  
  
      <webRequestModules>   
</webRequestModules>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[加入](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|將自訂 Web 要求模組加入至應用程式。|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|移除應用程式中所有已註冊的 Web 要求模組。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|移除應用程式中的自訂 Web 要求模組。|  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含指定 .NET Framework 如何連接至網路的設定。|  
  
## 備註  
 `webRequestModules` 項目會註冊 <xref:System.Net.WebRequest> 類別的子系，以處理網路主機的資訊要求。  Web 要求模組必須實作 <xref:System.Net.IWebRequestCreate> 介面。  
  
 .NET Framework 包含以 http:\/\/、https:\/\/ 和 file:\/\/ 開頭之 URI 的 Web 要求模組。  您只能利用在組態檔中註冊自訂模組的方式覆寫預設的模組。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 以下程式碼範例會註冊預設的 HTTP 模組。  您應該將 Version 和 PublicKeyToken 的值取代成指定之模組的正確值。  
  
```  
<configuration>  
  <system.net>  
    <webRequestModules>  
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
 <xref:System.Net.IWebRequestCreate>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)