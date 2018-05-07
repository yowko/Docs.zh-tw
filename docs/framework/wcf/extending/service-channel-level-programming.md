---
title: 服務通道層級的程式設計
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
ms.openlocfilehash: e48c519f6e10be4521d75345845eb5c019ec342c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="service-channel-level-programming"></a>服務通道層級的程式設計
本主題說明如何撰寫 Windows Communication Foundation (WCF) 服務應用程式，而不使用<xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>和其相關聯的物件模型。  
  
## <a name="receiving-messages"></a>接收訊息  
 以下為準備接收和處理訊息時所需的步驟：  
  
1.  建立繫結。  
  
2.  建置通道接聽程式。  
  
3.  開啟通道接聽程式。  
  
4.  讀取要求並傳送回覆。  
  
5.  關閉所有通道物件。  
  
#### <a name="creating-a-binding"></a>建立繫結。  
 接聽與接收訊息的第一步，就是建立繫結。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 隨附幾個內建或系統提供的繫結，您可以具現化其中一個來直接使用。 此外，您也可以產生 CustomBinding 類別來建立自己的自訂繫結 (清單 1 中的程式碼也會執行相同作業)。  
  
 下列的程式碼範例會建立 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> 的執行個體，並將 <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> 新增至其項目集合 (用來建置通道堆疊的繫結項目集合)。 在此範例中，由於項目集合只具有 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>，因此結果通道堆疊也只有 HTTP 傳輸通道。  
  
#### <a name="building-a-channellistener"></a>建置 ChannelListener  
 建立繫結之後, 我們呼叫<!--zz<xref:System.ServiceModel.Channels.Binding.BuildChannelListener%601%2A?displayProperty=nameWithType>-->`System.ServiceModel.Channels.Binding.BuildChannelListener`來建置通道接聽程式，其中型別參數是要建立的通道。 在此範例中，我們會使用 <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType>，因為我們想要以要求/回覆訊息交換模式來接聽傳入訊息。  
  
 <xref:System.ServiceModel.Channels.IReplyChannel> 會被用來接收要求訊息與傳回回覆訊息。 呼叫 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> 會傳回 <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>，以便用來接收要求訊息並傳回回覆訊息。  
  
 在建立接聽程式時，我們會傳送接聽程式所接聽的網路位址，在此範例為 `http://localhost:8080/channelapp`。 一般來說，每個傳輸通道都支援一到數個位址配置，例如，HTTP 傳輸同時支援 http 和 https 配置。  
  
 在建立接聽程式時，我們同時會傳送空的 <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType>。 繫結參數機制會負責將控制接聽程式建置方式的參數傳送出去。 我們的範例並未使用此類參數，因此我們會傳送空的集合。  
  
#### <a name="listening-for-incoming-messages"></a>接聽傳入訊息  
 接著，我們會在接聽程式上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 並開始接受通道。 <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> 的行為將視傳輸為連線導向還是沒有連線模式而定。 如果是連線導向傳輸，<xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> 會在新的連線要求進入時才停止封鎖，這時它會傳回一個代表該項新連線的新通道。 如果是沒有連線的傳輸，例如 HTTP，則 <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> 會立即傳回由傳輸接聽程式所建立，且是唯一的通道。  
  
 在此範例中，接聽程式會傳回可實作 <xref:System.ServiceModel.Channels.IReplyChannel> 的通道。 為了在此通道上接收訊息，首先我們必須在其上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>，以將之轉換成準備通訊的狀態。 接著我們會呼叫 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 並在訊息抵達之前進行封鎖。  
  
#### <a name="reading-the-request-and-sending-a-reply"></a>讀取要求並傳送回覆  
 當 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 傳回 <xref:System.ServiceModel.Channels.RequestContext>，我們會透過其 <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> 屬性來取回接收的訊息。 我們會寫出訊息的行動與本文內容 (我們假定是字串)。  
  
 在此情況下，為了傳送回覆，我們會建立新的回覆訊息並傳回要求中所收到的字串資料。 接著，我們會呼叫 <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> 來傳送回覆訊息。  
  
#### <a name="closing-objects"></a>關閉物件  
 為避免洩漏資源，請在不再需要時，關閉通訊期間所使用的物件，這點請您務必注意。 在此範例中，我們會關閉要求訊息、要求內容、通道和接聽程式。  
  
 下列程式碼範例示範基本服務，其中的通道接聽程式只會收到一個訊息。 真實的服務會在服務結束之前持續接受通道並接收訊息。  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]
