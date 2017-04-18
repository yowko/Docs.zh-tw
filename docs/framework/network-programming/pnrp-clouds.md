---
title: "PNRP 雲端 | Microsoft Docs"
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
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: 4
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 4
---
# PNRP 雲端
「PNRP Cloud」表示可以彼此通訊網路的節點集。  詞彙「Cloud」與「對等網狀結構」和「\(Peer\-to\-Peer\) 圖形」是同義詞。  
  
 節點之間的通訊不可以跨 Cloud。  <xref:System.Net.PeerToPeer.Cloud> 執行個體是由區分大小寫的名稱唯一識別。  單一對等或節點可以連接至多個 Cloud。  
  
 Cloud 與網路介面緊密的繫結。  在有兩張網路卡指向不同子網路的多重主目錄電腦上，會傳回三個 Cloud：每個介面的每一個連結本機位址各有一個 Cloud，以及一個單一全域範圍 Cloud。  
  
 PNRP 使用三個重疊的「範圍」\(Scope\)，範圍為電腦群組可以互相找到:  
  
-   全域 Cloud 物件對應至全域 IPv6 位址範圍和全域位址及表示整個 IPv6 網際網路的電腦。  只有一個全域 Cloud。  
  
-   連結本機 Cloud 中對應於連結本機位址範圍和 IPv6 連結本機位址。  連結本機 Cloud 是特定連結，通常與本機連接的子網路。  可以有多個連結本機 Cloud。  
  
 第三個 Cloud，網站特定 Cloud，對應於網站 IPv6 位址範圍和站台本機位址。  這個 Cloud 中已被取代，不過，它在 PNRP 仍支援。  
  
## Cloud  
 PNRP Cloud <xref:System.Net.PeerToPeer.Cloud> 由類別其執行個體所表示。  中的群組中使用了對等之可列舉的 <xref:System.Net.PeerToPeer.CloudCollection> 類別的執行個體所表示的。  PNRP Cloud 集合的目前對等已知可以藉由呼叫靜態方法 <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> 取得。  
  
 個別的 Cloud 中有唯一的名稱，表示為 256 個字元的 Unicode 字串。  這些名稱時，使用先前提到的範圍時，用來建構唯一的執行個體 Cloud 類別。  這些執行個體可以用於保存方式序列化並重建。  
  
 一個 Cloud 建立執行個體或衍生自類別，對等名稱可以移至其註冊建立已知的對等網狀結構。  
  
## 請參閱  
 <xref:System.Net.PeerToPeer.Cloud>   
 [對等名稱解析通訊協定](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)