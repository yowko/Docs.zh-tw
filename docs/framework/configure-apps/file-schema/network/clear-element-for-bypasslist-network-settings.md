---
title: "bypasslist 的 &lt;clear&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<bypasslist>, clear 項目"
  - "<clear> 項目, bypasslist"
  - "bypasslist, clear 項目"
  - "clear 項目, bypasslist"
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# bypasslist 的 &lt;clear&gt; 項目 (網路設定)
清除 Proxy 略過清單。  
  
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
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|提供一組規則運算式，描述不使用 Proxy 的位址。|  
  
## 備註  
 `clear` 項目 \(Element\) 會清除略過清單中的所有項目 \(Entry\)。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 以下程式碼範例會清除略過清單，然後將兩個位址加入至略過清單。  第一個會略過 contoso.com 網域中所有伺服器的 Proxy；第二個會略過 IP 位址以 192.168 開頭的所有伺服器的 Proxy。  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## 請參閱  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)