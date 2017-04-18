---
title: "用戶端通道層級的程式設計 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 用戶端通道層級的程式設計
本主題說明如何撰寫 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端應用程式，而不使用 <xref:System.ServiceModel.ClientBase%601?displayProperty=fullName> 類別及其相關的物件模型。  
  
## 傳送訊息  
 以下為準備傳送訊息及接收和處理回覆所需的步驟：  
  
1.  建立繫結。  
  
2.  建置通道處理站。  
  
3.  建立通道。  
  
4.  傳送要求和讀取回覆。  
  
5.  關閉所有通道物件。  
  
#### 建立繫結。  
 與接收案例類似 \(請參閱[服務通道層級的程式設計](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)\)，傳送訊息也是由建立繫結開始。這個範例會建立新的 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName>，並將 <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=fullName> 加入至其 Elements 集合。  
  
#### 建置 ChannelFactory  
 這次我們不會建立 <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=fullName>，而是藉由在型別參數為 <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=fullName> 的繫結上呼叫 <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=fullName> 的方式建立 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName>。通道接聽項是由等候傳入訊息的一端使用，而通道處理站是由初始化通訊以建立通道的一端使用。就如同通道接聽項，通道處理站也必須先開啟才能使用。  
  
#### 建立通道  
 然後我們會呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=fullName> 建立 <xref:System.ServiceModel.Channels.IRequestChannel>。這個呼叫會使用建立的新通道，採用我們想要進行通訊的端點位址。一旦有了通道，我們就會在通道上呼叫 Open，讓通道進入準備好進行通訊的狀態。根據傳輸的本質，呼叫 Open 可能會初始化與目標端點的連線，或是不在網路上執行任何動作。  
  
#### 傳送要求和讀取回覆  
 一旦開啟了通道，我們就能建立訊息並使用通道的 Request 方法傳送要求，然後等待回覆。當這個方法傳回時，我們會收到可以讀取的回覆訊息，並找出端點的回覆為何。  
  
#### 關閉物件  
 為避免洩漏資源，我們會在不再需要時，關閉通訊中所使用的物件。  
  
 以下程式碼範例會示範使用通道處理站傳送訊息和讀取回覆的基本用戶端。  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]