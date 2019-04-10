---
title: 用戶端通道層級的程式設計
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: ea56c99d7d122dd20fc217f8ecb2937bcf81bec3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324122"
---
# <a name="client-channel-level-programming"></a>用戶端通道層級的程式設計
本主題描述如何撰寫 Windows Communication Foundation (WCF) 用戶端應用程式，而不需使用<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>類別和其相關聯的物件模型。  
  
## <a name="sending-messages"></a>傳送訊息  
 以下為準備傳送訊息及接收和處理回覆所需的步驟：  
  
1. 建立繫結。  
  
2. 建置通道處理站。  
  
3. 建立通道。  
  
4. 傳送要求和讀取回覆。  
  
5. 關閉所有通道物件。  
  
#### <a name="creating-a-binding"></a>建立繫結。  
 接收案例類似 (請參閱[服務通道層級程式設計](../../../../docs/framework/wcf/extending/service-channel-level-programming.md))，以建立繫結傳送的訊息啟動。 這個範例會建立新的 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>，並將 <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> 加入至其 Elements 集合。  
  
#### <a name="building-a-channelfactory"></a>建置 ChannelFactory  
 這次我們不會建立 <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>，而是藉由在型別參數為 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 的繫結上呼叫 <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> 的方式建立 <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>。 通道接聽項是由等候傳入訊息的一端使用，而通道處理站是由初始化通訊以建立通道的一端使用。 就如同通道接聽項，通道處理站也必須先開啟才能使用。  
  
#### <a name="creating-a-channel"></a>建立通道  
 然後我們會呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> 建立 <xref:System.ServiceModel.Channels.IRequestChannel>。 這個呼叫會使用建立的新通道，採用我們想要進行通訊的端點位址。 一旦有了通道，我們就會在通道上呼叫 Open，讓通道進入準備好進行通訊的狀態。 根據傳輸的本質，呼叫 Open 可能會初始化與目標端點的連線，或是不在網路上執行任何動作。  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>傳送要求和讀取回覆  
 一旦開啟了通道，我們就能建立訊息並使用通道的 Request 方法傳送要求，然後等待回覆。 當這個方法傳回時，我們會收到可以讀取的回覆訊息，並找出端點的回覆為何。  
  
#### <a name="closing-objects"></a>關閉物件  
 為避免洩漏資源，我們會在不再需要時，關閉通訊中所使用的物件。  
  
 以下程式碼範例會示範使用通道處理站傳送訊息和讀取回覆的基本用戶端。  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
