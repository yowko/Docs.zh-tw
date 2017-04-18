---
title: "IPv6 自動設定 | Microsoft Docs"
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
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# IPv6 自動設定
IPv6 的重要目標是支援隨插即用的節點。  也就是可以外掛節點至 IPv6 網路並自動設定，而不需要使用者介入的應該是可能的。  
  
## 自動配置的型別。  
 IPv6 支援自動配置類型如下:  
  
-   **Stateful auto\-configuration**。  這種類型的組態需求人員的干擾程度，因為它需要 IPv6 \(DHCPv6\) 伺服器上項目動態主機設定通訊協定 \(DHCP\) 節點的安裝和執行。  DHCPv6 伺服器保存它提供組態資訊節點的清單。  它也會維護狀態資訊，因此伺服器知道每個位址仍然是在使用中，所以，以及何時會為了重新配置行為。  
  
-   **Stateless auto\-configuration**。  這種類型的組態適合小型組織和個別。  在此情況下，每個主應用程式判斷其位址從收到的"路由器通告內容。  使用定義 EUI\-64 IEEE Standard 位址的網路部分 ID，假設主機位址的唯一在連結的是合理的作法。  
  
 不論這個位址是如何決定的，節點必須驗證其可能的位址到本機連結是唯一的。  這是由傳送"近鄰請求"訊息設為這個可能的位址。  如果節點收到任何回應，它知道這個位址已經在使用中，且必須判斷另一個位址。  
  
## IPv6 行動性  
 行動裝置的擴充會引入新的需求:裝置必須能夠選擇性地變更 IPv6 網際網路的位置和仍維持現有的連接。  若要提供這個功能，一個行動指派給它一定已到達主要位址。  當行動 Home 節點時，會連接至首頁連結並使用其主要位址。  當行動節點離開的首頁，一個代理程式，通常是路由器、中間的訊息會在目前的節點和它之間的通訊。  
  
## 請參閱  
 [網際網路通訊協定第 6 版](../../../docs/framework/network-programming/internet-protocol-version-6.md)   
 [通訊端](../../../docs/framework/network-programming/sockets.md)