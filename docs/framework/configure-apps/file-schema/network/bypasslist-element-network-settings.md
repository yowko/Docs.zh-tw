---
title: "&lt;bypasslist&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<bypasslist> 項目"
  - "bypasslist 項目"
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# &lt;bypasslist&gt; 項目 (網路設定)
提供一組規則運算式，描述不使用 Proxy 的位址。  
  
## 語法  
  
```  
  
      <bypasslist>   
</bypasslist>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[新增](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|將 IP 位址或 DNS 名稱加入至 Proxy 略過清單。|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|清除略過清單。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|移除 Proxy 略過清單中的 IP 位址或 DNS 名稱。|  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|設定超文字傳輸協定 \(HTTP\) Proxy 伺服器。|  
  
## 備註  
 略過清單包含描述 <xref:System.Net.WebRequest> 執行個體直接 \(而非透過 Proxy 伺服器\) 存取的 URI 的規則運算式。  
  
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