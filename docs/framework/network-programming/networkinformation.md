---
title: "NetworkInformation | Microsoft Docs"
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
helpviewer_keywords: 
  - "網路"
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# NetworkInformation
<xref:System.Net.NetworkInformation> 命名空間可讓您收集 Web 事件、變更、統計資料和屬性的相關資訊。  您也可以判斷遠端主機是否可使用 <xref:System.Net.NetworkInformation.Ping?displayProperty=fullName> 類別。  
  
## 網路可用性和事件  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=fullName> 類別可讓您判斷網路位址或可用性是否已變更。  若要使用這個類別中，建立事件處理常式處理變更，並將其與 <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> 或 <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>。  如需詳細資訊，請參閱[如何：偵測網路可用性和位址變更](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md)。  
  
## 網路統計資料和屬性。  
 您可以收集網路統計資料和屬性在介面或通訊協定基礎。  而 <xref:System.Net.NetworkInformation.IPInterfaceProperties>、 <xref:System.Net.NetworkInformation.IPGlobalProperties>、 <xref:System.Net.NetworkInformation.IPGlobalStatistics>、 <xref:System.Net.NetworkInformation.TcpStatistics>和 <xref:System.Net.NetworkInformation.UdpStatistics> 類別可提供與圖層和圖層 3 4 封包中的資訊， <xref:System.Net.NetworkInformation.NetworkInterface>、 <xref:System.Net.NetworkInformation.NetworkInterfaceType>和 <xref:System.Net.NetworkInformation.PhysicalAddress> 類別提供有關特定網路介面的相關資訊。  如需詳細資訊，請參閱[如何：取得介面和通訊協定資訊](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md)。  
  
## 判斷遠端主機是否可到達  
 您可以使用 <xref:System.Net.NetworkInformation.Ping> 類別判斷遠端主機是否引發，在網路上，以及可取得。  如需詳細資訊，請參閱[如何：Ping 主機](../../../docs/framework/network-programming/how-to-ping-a-host.md)。  
  
## 請參閱  
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)   
 [網路資訊技術範例](http://go.microsoft.com/fwlink/?LinkID=179564)   
 [NetStat 工具技術範例](http://go.microsoft.com/fwlink/?LinkID=179562)   
 [Ping 用戶端技術範例](http://go.microsoft.com/fwlink/?LinkID=179565)