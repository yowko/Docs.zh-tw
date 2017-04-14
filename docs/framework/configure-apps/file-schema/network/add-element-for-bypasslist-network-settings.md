---
title: "bypasslist 的 &lt;add&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> 項目, bypasslist"
  - "<bypasslist>, add 項目"
  - "add 項目, bypasslist"
  - "bypasslist, add 項目"
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# bypasslist 的 &lt;add&gt; 項目 (網路設定)
將 IP 位址或 DNS 名稱加入至 Proxy 略過清單。  
  
## 語法  
  
```  
  
      <add   
   address = "regular expression"   
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**描述**|  
|------------|------------|  
|**address**|描述 IP 位址或 DNS 名稱的規則運算式。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|提供一組規則運算式，描述不使用 Proxy 的位址。|  
  
## 備註  
 `add` 項目會將描述 IP 位址或 DNS 伺服器名稱的規則運算式加入至略過 Proxy 伺服器的位址清單。  
  
 `address` 屬性的值必須是描述一組 IP 位址或主機名稱的規則運算式。  
  
 當您針對這個項目指定規則運算式時，應該要使用警告。  規則運算式 "\[a\-z\]\+\\.contoso\\.com" 符合 contoso.com 網域中的任何主機，但是也符合 contoso.com.cpandl.com 網域中的任何主機。  若要只符合 contoso.com 網域中的主機，請使用錨定 \(Anchor\) \("$"\)："\[a\-z\]\+\\.contoso\\.com$"。  
  
 如需規則運算式的詳細資訊，請參閱 [.NET Framework 規則運算式](../../../../../docs/standard/base-types/regular-expressions.md)。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 以下程式碼範例會將兩個位址加入至略過清單。  第一個會略過 contoso.com 網域中所有伺服器的 Proxy；第二個會略過 IP 位址以 192.168 開頭的所有伺服器的 Proxy。  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
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