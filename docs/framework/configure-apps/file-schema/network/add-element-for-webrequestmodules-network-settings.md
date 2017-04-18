---
title: "webRequestModules 的 &lt;add&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> 項目, webRequestModules"
  - "<webRequestModules>, add 項目"
  - "add 項目, webRequestModules"
  - "webRequestModules, add 項目"
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
caps.latest.revision: 16
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 16
---
# webRequestModules 的 &lt;add&gt; 項目 (網路設定)
將自訂 Web 要求模組加入至應用程式。  
  
## 語法  
  
```  
  
      <add   
  prefix = "URI prefix"   
  type = "module name, Version, Culture, PublicKeyToken"   
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**描述**|  
|------------|------------|  
|`prefix`|這個 Web 要求模組所處理之要求的 URI 前置詞。|  
|`type`|實作這個 Web 要求模組之模組的組件和類別名稱。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|指定向網路主機要求資訊所使用的模組。|  
  
## 備註  
 `prefix` 屬性會定義使用指定之 Web 要求模組的 URI 前置詞。  Web 要求模組通常是註冊成處理特定的通訊協定 \(例如 HTTP 或 FTP\)，但是也可以註冊成處理對特定伺服器或伺服器路徑的要求。  
  
 URI 相符的前置詞傳遞至 <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName> 方法後，就會建立 Web 要求模組。  
  
 `prefix` 屬性的值必須是有效 UR 的前置字元，例如 "http" 或 "http:\/\/www.contoso.com"。  
  
 `type` 屬性的值必須是有效的 DLL 名稱和對應的類別名稱，並且以逗號分隔。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例會註冊 HTTP 的自訂 Web 要求模組。  您應該將 Version 和 PublicKeyToken 的值取代成指定之模組的正確值。  
  
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
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)