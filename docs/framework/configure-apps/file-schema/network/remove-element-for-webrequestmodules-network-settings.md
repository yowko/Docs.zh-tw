---
title: "webRequestModules 的 &lt;remove&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<remove> 項目, webRequestModules"
  - "<webRequestModules>, remove 項目"
  - "remove 項目, webRequestModules"
  - "webRequestModules, remove 項目"
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# webRequestModules 的 &lt;remove&gt; 項目 (網路設定)
移除應用程式中的自訂 Web 要求模組。  
  
## 語法  
  
```  
  
      <remove   
  name = "URI prefix"   
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**描述**|  
|------------|------------|  
|`name`|這個 Web 要求模組所處理之要求的 URI 前置詞。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|指定向網路主機要求資訊所使用的模組。|  
  
## 備註  
 `remove` 項目會針對指定的 URI 前置詞移除已註冊的 Web 要求模組。  
  
 `prefix` 屬性的值必須是有效 URI 的前置字元，例如 "http" 或 "http:\/\/www.contoso.com"。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例會移除 HTTP 的現有 Web 要求模組，然後將 HTTP 的自訂 Web 要求模組註冊為 www.contoso.com。  
  
```  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix = "http">  
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