---
title: "&lt;module&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#module"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<module> 項目"
  - "module 項目"
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;module&gt; 項目 (網路設定)
將新的 Pxory 模組加入至應用程式。  
  
## 語法  
  
```  
  
      <module   
   type = "name", System, Version="version number", Culture="culture", PublicKeyToken="token" "   
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**說明**|  
|------------|------------|  
|`type`|實作 Proxy 的模組的名稱和規格。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|設定超文字傳輸協定 \(HTTP\) Proxy 伺服器。|  
  
## 備註  
 `module` 項目會註冊實作 <xref:System.Net.IWebProxy> 介面的 Proxy 類別。  註冊了 Proxy 類別之後，可以使用 `module`，透過支援的 Proxy 要求資訊。  
  
 `type` 屬性的值必須是有效動態連結程式庫 \(DLL\) 的名稱和模組的類別名稱。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 以下程式碼範例會註冊自訂的 Proxy 類別。  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type = "Test.CustomWebProxy, System, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.IWebProxy?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)