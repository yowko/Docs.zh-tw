---
title: "啟用和停用 IPv6 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 啟用和停用 IPv6
若要使用 IPv6 通訊協定，請確定您執行支援 IPv6 作業系統版本並確保執行適當地設定作業系統和網路類別。  
  
## 組態步驟。  
 下表列出各種設定  
  
|啟用 IPv6 的作業系統?|啟用 IPv6 之網路類別?|描述|  
|--------------------|--------------------|--------|  
|否|否|可以剖析 IPv6 位址。|  
|否|是|可以剖析 IPv6 位址。|  
|是|否|使用名稱解析方法未標記為過時，可以剖析和解析 IPv6 位址 IPv6 位址。|  
|是|是|使用所有方法 \(包括標記為過時，可以剖析和解析 IPv6 位址。|  
  
 請注意啟用 IPv6 支援 System.Net 命名空間中的所有類別，您必須修改電腦組態檔或組態檔的應用程式。  應用程式的組態檔會在電腦組態檔的優先順序。  
  
 示範如何修改電腦組態檔， *machine.config*，啟用 Ipv6 的支援，請參閱 [HOW TO:修改電腦組態檔中啟用 Ipv6 支援](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)。  此外，也請確定的 IPv6 支援的作業系統中啟用。  
  
 .NET Framework 有所設定的組態參數在組態檔  
  
```  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 在 .NET Framework 1.1 版以前， **ipv6 enabled** 設定參數的值是指定 <xref:System.Net.Dns?displayProperty=fullName> 類別傳回 IPv6 位址的成員。  
  
 如需 <xref:System.Net.Dns?displayProperty=fullName> 類別的 .NET Framework 2.0 \(含\) 以後版本，則為，如果視窗支援 IPv6，則成員， <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName> 方法 \(例如，\)，便會傳回 IPv6 具有限制的位址。  DNS <xref:System.Net.Dns?displayProperty=fullName> 過時成員 \(例如， <xref:System.Net.Dns.Resolve%2A?displayProperty=fullName> 方法\) 會讀取並識別組態檔中的值 ipv6 啟用的設定。  
  
## 請參閱  
 [網際網路通訊協定第 6 版](../../../docs/framework/network-programming/internet-protocol-version-6.md)   
 [通訊端](../../../docs/framework/network-programming/sockets.md)   
 [網路設定結構描述](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<ipv6\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)