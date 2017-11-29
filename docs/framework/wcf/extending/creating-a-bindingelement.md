---
title: "建立 BindingElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6fa68698c6c343b29ca39e66150753502cb8f673
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-bindingelement"></a>建立 BindingElement
繫結和繫結項目 (分別延伸 <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> 和 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> 的物件) 就是 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式模型與通道處理站和通道接聽程式建立關聯的位置。 不繫結，使用自訂通道，需要在通道層級的程式設計中所述[服務通道層級程式設計](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)和[用戶端通道層級程式設計](../../../../docs/framework/wcf/extending/client-channel-level-programming.md)。 本主題討論的最低需求，以便使用您的通道中[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，開發<xref:System.ServiceModel.Channels.BindingElement>為您的通道，並從應用程式的步驟 4 中所述的啟用使用[開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)。  
  
## <a name="overview"></a>概觀  
 為您的通道建立 <xref:System.ServiceModel.Channels.BindingElement>，便可讓開發人員在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式中使用您的通道。 <xref:System.ServiceModel.Channels.BindingElement> 物件可從 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 類別用來將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式連接至您的通道，而不需要精確輸入您的通道資訊。  
  
 一次<xref:System.ServiceModel.Channels.BindingElement>已建立，您可以啟用更多的功能取決於您的需求而定的其餘通道開發步驟所述的下列[開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)。  
  
## <a name="adding-a-binding-element"></a>新增繫結項目  
 若要實作自訂 <xref:System.ServiceModel.Channels.BindingElement>，請撰寫繼承自 <xref:System.ServiceModel.Channels.BindingElement> 的類別。 例如，如果已開發出可以將大型訊息切割為區塊並在另一端重新組合的 `ChunkingChannel`，您就可以在實作 <xref:System.ServiceModel.Channels.BindingElement> 並設定繫結使用此項目後所產生的任何繫結中使用這個通道。 本主題的其餘部分將使用 `ChunkingChannel` 做為範例，示範實作繫結項目的需求。  
  
 `ChunkingBindingElement` 會負責建立 `ChunkingChannelFactory` 和 `ChunkingChannelListener`。 它會覆寫 <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> 和 <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> 實作，並檢查型別參數是否為 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (在我們的範例中，這是 `ChunkingChannel` 唯一支援的通道形狀)，以及繫結中的其他繫結項目是否支援這個通道形狀。  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> 會先檢查是否能建置要求的通道形狀，接著會取得要分成區塊的訊息動作清單。 然後它會建立新的 `ChunkingChannelFactory`，並將此處理站傳遞至內部通道處理站  (如果是要建立傳輸繫結項目，由於該項目是繫結堆疊中的最後一個項目，因此必須建立通道接聽程式或通道處理站)。  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> 擁有可建立 `ChunkingChannelListener` 並傳遞至內部通道接聽程式的相似實作。  
  
 另一個範例是使用傳輸通道，[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例提供下列的覆寫。  
  
 在此範例中，繫結項目為 `UdpTransportBindingElement`，其衍生自 <xref:System.ServiceModel.Channels.TransportBindingElement>。 它會覆寫下列方法來建置與通道關聯的處理站。  
  
```  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
            return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
            return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 它還包含可以用來複製 `BindingElement` 以及傳回我們的結構描述 (soap.udp) 的成員。  
  
#### <a name="protocol-binding-elements"></a>通訊協定繫結項目  
 新的繫結項目可以取代或擴充任何已包含的繫結項目、新增新的傳輸、編碼，或更高層級的通訊協定。 若要建立新的通訊協定繫結項目，一開始要先擴充 <xref:System.ServiceModel.Channels.BindingElement> 類別。 最少，接下來您必須實作<xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType>並實作`ChannelProtectionRequirements`使用<xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>。 這會傳回這個繫結項目的 <xref:System.ServiceModel.Security.ChannelProtectionRequirements>。  如需詳細資訊，請參閱<xref:System.ServiceModel.Security.ChannelProtectionRequirements>。  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> 應該會傳回這個繫結項目的全新複本。 在最佳做法中，我們建議繫結項目作者使用複製建構函式 (其呼叫基底複製建構函式) 來實作 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>，然後複製在此類別中的任何其他欄位。  
  
#### <a name="transport-binding-elements"></a>傳輸繫結項目  
 若要建立新的傳輸繫結項目，請擴充 <xref:System.ServiceModel.Channels.TransportBindingElement> 介面。 接下來，您必須至少實作 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> 方法和 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> 屬性。  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> 應該會傳回這個繫結項目的全新複本。  在最佳做法中，我們建議繫結項目作者使用複製建構函式 (其呼叫基底複製建構函式) 來實作該複製品，然後複製在此類別中的任何其他欄位。  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> –<xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> get 屬性會傳回繫結項目所表示之傳輸通訊協定所適用的 URI 結構描述。 例如，<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>和<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>從其各自傳回"http"和"net.tcp"<xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A>屬性。  
  
#### <a name="encoding-binding-elements"></a>編碼繫結項目  
 若要建立新的編碼繫結項目，一開始要先擴充 <xref:System.ServiceModel.Channels.BindingElement> 類別，並實作 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> 類別。 接下來，您必須至少實作 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> 方法和 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> 屬性。  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. 傳回這個繫結項目的全新複本。 在最佳做法中，我們建議繫結項目作者使用複製建構函式 (其呼叫基底複製建構函式) 來實作 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>，然後複製在此類別中的任何其他欄位。  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. 傳回 <xref:System.ServiceModel.Channels.MessageEncoderFactory>，它會提供實作新編碼器 (應該會擴充 <xref:System.ServiceModel.Channels.MessageEncoder>) 之實際類別的控制代碼。 如需詳細資訊，請參閱 <xref:System.ServiceModel.Channels.MessageEncoderFactory> 與 <xref:System.ServiceModel.Channels.MessageEncoder>。  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. 傳回這個編碼所使用的 <xref:System.ServiceModel.Channels.MessageVersion>，其代表正在使用的 SOAP 和 WS-Addressing 版本。  
  
 如需以及使用者定義之編碼繫結項目之選擇性方法和屬性的完整清單，請參閱 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>。  
  
 如需有關如何建立新的繫結元素的詳細資訊，請參閱[Creating User-Defined 繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)。  
  
 一旦您已經建立您的通道繫結項目，返回到[開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)主題，查看是否要將組態檔支援新增至您的繫結項目，如果以及如何新增發行集支援中繼資料，以及是否及如何使用您的繫結項目來建構使用者定義的繫結。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)  
 [傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
