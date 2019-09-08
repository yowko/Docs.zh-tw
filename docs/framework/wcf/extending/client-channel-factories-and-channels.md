---
title: 用戶端：通道處理站與通道
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 3dfcca0d5492a3fa376ec184f4bdd9bfa03b53c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795869"
---
# <a name="client-channel-factories-and-channels"></a>用戶端：通道處理站與通道
這個主題會討論通道處理站和通道的建立方面。  
  
## <a name="channel-factories-and-channels"></a>通道處理站與通道  
 通道處理站會負責建立通道。 而通道處理站所建立的通道會用於傳送訊息。 這些通道會負責從上層取得訊息、執行必須的處理動作，然後將訊息傳送至下層。 下圖會說明這個程序。  
  
 ![用戶端工廠和通道](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
通道處理站會建立通道。  
  
 關閉時，通道處理站會負責關閉所建立但尚未關閉的任何通道。 請注意，此處的模型為非對稱，這是因為關閉通道接聽項時，只會停止接受新通道，但會讓現有的通道保持為開啟，這樣才可以繼續接收訊息。  
  
 WCF 會為此程式提供基類 helper。 （如需本主題中所討論之通道協助程式類別的圖表，請參閱[通道模型總覽](channel-model-overview.md)）。  
  
- 類別會執行[開發通道](developing-channels.md)的步驟2中所述的狀態機器，並加以強制執行。<xref:System.ServiceModel.ICommunicationObject> <xref:System.ServiceModel.Channels.CommunicationObject>  
  
- <xref:System.ServiceModel.Channels.ChannelManagerBase> 類別會實作 <xref:System.ServiceModel.Channels.CommunicationObject>，並為 <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> 和 <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType> 提供統一的基底類別。 <xref:System.ServiceModel.Channels.ChannelManagerBase> 類別可以和 <xref:System.ServiceModel.Channels.ChannelBase> 一起運作，而後者是實作 <xref:System.ServiceModel.Channels.IChannel> 的基底類別。
  
- <xref:System.ServiceModel.Channels.ChannelFactoryBase> `OnCreateChannel`類別會執行`CreateChannel`和，<xref:System.ServiceModel.Channels.IChannelFactory>並將多載合併為單一抽象方法。 <xref:System.ServiceModel.Channels.ChannelManagerBase>
  
- <xref:System.ServiceModel.Channels.ChannelListenerBase> 類別會實作 <xref:System.ServiceModel.Channels.IChannelListener>。 它會負責基礎的狀態管理。 
  
 下列討論是以[傳輸為基礎：UDP](../samples/transport-udp.md)範例。  
  
### <a name="creating-a-channel-factory"></a>建立通道處理站y  
 `UdpChannelFactory` 是衍生自 <xref:System.ServiceModel.Channels.ChannelFactoryBase>。 範例會覆寫 <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A>，以提供訊息編碼器之訊息版本的存取權。 當狀態電腦進行轉換時，該範例也會覆寫 <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> 以終止 <xref:System.ServiceModel.Channels.BufferManager> 的執行個體。  
  
#### <a name="the-udp-output-channel"></a>UDP 輸出通道  
 `UdpOutputChannel` 會實作 <xref:System.ServiceModel.Channels.IOutputChannel>。 建構函式會驗證引數，並根據傳進的 <xref:System.Net.EndPoint> 建構目的地 <xref:System.ServiceModel.EndpointAddress> 物件。  
  
 覆寫 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> 後會建立用於將訊息傳送至此 <xref:System.Net.EndPoint> 的通訊端 (Socket)。  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 可以依正常程序或非正常程序關閉通道。 如果依正常程序關閉通道，將會關閉通訊端，並且會呼叫基底類別 `OnClose` 方法。 如果因此發生例外狀況，則基礎結構會呼叫 `Abort`，確保已清除通道。  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 執行`Send()`和`BeginSend()`。 / `EndSend()` 這分成兩個主要區段。 首先，將訊息序列化為位元組陣列：  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 然後在 Wire 上傳送產生的資料：  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>另請參閱

- [開發通道](developing-channels.md)
