---
title: "如何：修改電腦設定檔案以啟用 IPv6 支援 | Microsoft Docs"
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
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: 18
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# 如何：修改電腦設定檔案以啟用 IPv6 支援
下列程式碼範例將示範如何修改電腦組態檔， *machine.config*，啟用 IPv6 支援。  *machine.config* 檔案位於 Windows 安裝目錄的 *%Windir% \\ Microsoft.NET \\ Framework* 資料夾中。  在資料夾中的個別 *machine.config* 檔在電腦上安裝 .NET Framework \(例如， *C:\\WINDOWS\\Microsoft.NET\\Framework\\v2.0 .50727 \\ machine.config*\) 的每個版本的 *%Windir% \\ Microsoft.NET \\ Framework* 之下。  
  
 這些設定可以在應用程式的組態檔可以進行，和在電腦組態檔的優先順序。  
  
 在 .NET Framework 1.1 版以前， **ipv6 enabled** 設定參數的值是指定 <xref:System.Net.Dns?displayProperty=fullName> 類別傳回 IPv6 位址的成員。  
  
 對於 .NET Framework 2.0 \(含\) 以後版本，則為，如果視窗支援 IPv6，然後 <xref:System.Net.Dns?displayProperty=fullName> 類別的所有成員 \(例如， <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName> 方法\)，則將會傳回 IPv6 具有限制的位址。  <xref:System.Net.Dns?displayProperty=fullName> 類別過時成員 \(例如， <xref:System.Net.Dns.Resolve%2A?displayProperty=fullName> 方法\) 會讀取並識別組態檔中的值。  
  
> [!NOTE]
>  預設會針對 .NET Framework 2.0 \(含\) 以後版本中，啟用 IPv6。  預設會針對 .NET Framework 1.1 \(含\) 以前版本中，如果停用。  
  
## 範例  
  
```  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## 請參閱  
 [IPv6 定址](../../../docs/framework/network-programming/ipv6-addressing.md)   
 [網路設定結構描述](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<ipv6\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)