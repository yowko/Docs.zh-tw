---
title: "&lt;defaultProxy&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<defaultProxy> 項目"
  - "defaultProxy 項目"
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
caps.latest.revision: 21
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 21
---
# &lt;defaultProxy&gt; 項目 (網路設定)
設定超文字傳輸協定 \(HTTP\) 的 Proxy 伺服器。  
  
## 語法  
  
```  
  
        <defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false"  
  <bypasslist> … </bypasslist>  
  <proxy> … </proxy>  
  <module> … </module>  
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|**項目**|**描述**|  
|------------|------------|  
|`enabled`|指定是否使用 Web Proxy。  預設值是 `true`。|  
|`useDefaultCredentials`|指定此主機的預設認證是否用來存取 Web Proxy。  預設值是 `false`。|  
  
### 子項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|提供一組位址的規則運算式，說明不使用 Proxy。|  
|[module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|將新的 Proxy 模組加入至應用程式。|  
|[Proxy](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|定義 Proxy 伺服器。|  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[系統。  net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## 備註  
 如果 defaultProxy 項目是空的，則會使用來自 Internet Explorer 的 Proxy 設定。  這個行為與 .NET Framework 1.1 版的不同。  
  
 如果[模組](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)項目指定非公用類型、類型並非衍生自 <xref:System.Net.IWebProxy> 類別、發生來自此物件預設建構函式的例外狀況，或是在擷取系統指定的預設 Proxy 時發生例外狀況，則擲回例外狀況。  例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。  
  
## 組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例會使用來自 Internet Explorer Proxy 的預設值，指定 Proxy 位址，並略過本機存取及 contoso.com 的 Proxy。  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist  
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)