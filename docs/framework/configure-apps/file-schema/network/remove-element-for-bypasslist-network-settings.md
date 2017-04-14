---
title: "bypasslist 的 &lt;remove&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<bypasslist>, remove 項目"
  - "bypasslist, remove 項目"
  - "remove 項目, bypasslist"
  - "remove 項目, bypasslist"
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
caps.latest.revision: 16
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 16
---
# bypasslist 的 &lt;remove&gt; 項目 (網路設定)
移除 Proxy 略過清單中的 IP 位址或 DNS 名稱。  
  
## 語法  
  
```  
  
      <remove   
   name = "regular expression"   
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**描述**|  
|------------|------------|  
|`name`|描述 IP 位址或 DNS 名稱的規則運算式。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|提供一組規則運算式，描述不使用 Proxy 的位址。|  
  
## 備註  
 `remove` 項目會將描述 IP 位址或 DNS 伺服器名稱的規則運算式從略過 Proxy 伺服器的位址清單中移除。  位址先前已定義於組態檔或組態階層架構的更高層級中。  
  
 `name` 屬性的值必須是描述一組 IP 位址或主機名稱的規則運算式。  
  
 如需規則運算式的詳細資訊，請參閱 [.NET Framework 規則運算式](../../../../../docs/standard/base-types/regular-expressions.md)。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 以下程式碼範例會移除 adventure\-works.com 網域先前的任何定義，然後將 contoso.com 網域加入至略過清單。  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <remove name = "[a-z]+\.adventure-works\.com$" />  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)