---
title: "&lt;ipv6&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<ipv6> 項目"
  - "ipv6 項目"
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
caps.latest.revision: 19
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 19
---
# &lt;ipv6&gt; 項目 (網路設定)
啟用來自 <xref:System.Net.Dns> 類別過時成員的網際網路通訊協定第 6 版 \(IPv6\) 回應。  
  
## 語法  
  
```  
  
      <ipv6  
  enabled="true|false"  
/ipv6>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**描述**|  
|------------|------------|  
|`enabled`|指定 <xref:System.Net.Dns> 類別的成員是否會傳回網際網路通訊協定第 6 版 \(IPv6\) 位址。  預設值是 `false`。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## 備註  
 這項設定會針對 <xref:System.Net.Dns> 類別的過時成員啟用 IPv6 支援：<xref:System.Net.Dns.BeginGetHostByName%2A>、<xref:System.Net.Dns.BeginResolve%2A>、<xref:System.Net.Dns.EndGetHostByName%2A>、<xref:System.Net.Dns.EndResolve%2A>、<xref:System.Net.Dns.GetHostByAddress%2A>、<xref:System.Net.Dns.GetHostByName%2A> 和 <xref:System.Net.Dns.Resolve%2A>。  至於 <xref:System.Net?displayProperty=fullName> 命名空間的其他成員，如果作業系統中已啟用 IPv6，則可能會傳回 IPv6 位址。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例說明如何啟用 <xref:System.Net.Dns> 類別的 IPv6 支援。  
  
```  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net?displayProperty=fullName>   
 <xref:System.Net.Dns?displayProperty=fullName>   
 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)