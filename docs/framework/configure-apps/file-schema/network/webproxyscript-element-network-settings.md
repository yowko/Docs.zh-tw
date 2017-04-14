---
title: "&lt;webProxyScript&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<webProxyScript> 項目"
  - "webProxyScript 項目"
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;webProxyScript&gt; 項目 (網路設定)
設定用來探索 Web Proxy 的指令碼的特性。  
  
## 語法  
  
```  
  
      <webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`downloadTimeout`|指定下載指令碼的時間上限，以小時、分鐘和秒鐘為單位。  預設值為 1 分鐘。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## 備註  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 請參閱  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)