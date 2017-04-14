---
title: "建立 BindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 建立 BindingElement
繫結和繫結項目 \(分別延伸 <xref:System.ServiceModel.Channels.Binding?displayProperty=fullName> 和 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName> 的物件\) 就是 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式模型與通道處理站和通道接聽程式建立關聯的位置。如果沒有繫結，就必須在通道層級進行程式設計才能使用自訂通道，詳細資訊請參閱[服務通道層級的程式設計](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)和[用戶端通道層級的程式設計](../../../../docs/framework/wcf/extending/client-channel-level-programming.md)。本主題將討論使您的通道能夠在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中啟用的最低需求、開發您通道的 <xref:System.ServiceModel.Channels.BindingElement>，以及如何從應用程式啟用 \(如[開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)中的步驟 4 所述\)。  
  
## 概觀  
 為您的通道建立 <xref:System.ServiceModel.Channels.BindingElement>，便可讓開發人員在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式中使用您的通道。<xref:System.ServiceModel.Channels.BindingElement> 物件可從 <xref:System.ServiceModel.ServiceHost?displayProperty=fullName> 類別用來將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式連接至您的通道，而不需要精確輸入您的通道資訊。  
  
 建立 <xref:System.ServiceModel.Channels.BindingElement> 之後，您就可以根據需求，依照[開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)中所述的其餘通道開發步驟來啟用更多功能。  
  
## 新增繫結項目  
 若要實作自訂 <xref:System.ServiceModel.Channels.BindingElement>，請撰寫繼承自 <xref:System.ServiceModel.Channels.BindingElement> 的類別。例如，如果已開發出可以將大型訊息切割為區塊並在另一端重新組合的 `ChunkingChannel`，您就可以在實作 <xref:System.ServiceModel.Channels.BindingElement> 並設定繫結使用此項目後所產生的任何繫結中使用這個通道。本主題的其餘部分將使用 `ChunkingChannel` 做為範例，示範實作繫結項目的需求。  
  
 `ChunkingBindingElement` 會負責建立 `ChunkingChannelFactory` 和 `ChunkingChannelListener`。它會覆寫 <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> 和 <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> 實作，並檢查型別參數是否為 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> \(在我們的範例中，這是 `ChunkingChannel` 唯一支援的通道形狀\)，以及繫結中的其他繫結項目是否支援這個通道形狀。  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> 會先檢查是否能建置要求的通道形狀，接著會取得要分成區塊的訊息動作清單。然後它會建立新的 `ChunkingChannelFactory`，並將此處理站傳遞至內部通道處理站 \(如果是要建立傳輸繫結項目，由於該項目是繫結堆疊中的最後一個項目，因此必須建立通道接聽程式或通道處理站\)。  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> 擁有會建立 `ChunkingChannelListener` 並傳遞至內部通道接聽程式的相似實作。  
  
 在另一個使用傳輸通道的範例中，[傳輸：UDP](../../../../docs/framework/wcf/samples/transport-udp.md) 範例提供下列覆寫。  
  
 在此範例中，繫結項目為 `UdpTransportBindingElement`，其衍生自 <xref:System.ServiceModel.Channels.TransportBindingElement>。它會覆寫下列方法來建置與通道關聯的處理站。  
  
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
  
 它還包含可以用來複製 `BindingElement` 以及傳回我們的結構描述 \(soap.udp\) 的成員。  
  
#### 通訊協定繫結項目  
 新的繫結項目可以取代或擴充任何已包含的繫結項目、新增新的傳輸、編碼，或更高層級的通訊協定。若要建立新的通訊協定繫結項目，一開始要先擴充 <xref:System.ServiceModel.Channels.BindingElement> 類別。接下來，您必須至少要實作 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=fullName>，並且使用 <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=fullName> 實作 `ChannelProtectionRequirements`。這會傳回這個繫結項目的 <xref:System.ServiceModel.Security.ChannelProtectionRequirements>。如需詳細資訊，請參閱 <xref:System.ServiceModel.Security.ChannelProtectionRequirements>。  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> 應該會傳回這個繫結項目的全新複本。在最佳做法中，我們建議繫結項目作者使用複製建構函式 \(其呼叫基底複製建構函式\) 來實作 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>，然後複製在此類別中的任何其他欄位。  
  
#### 傳輸繫結項目  
 若要建立新的傳輸繫結項目，請擴充 <xref:System.ServiceModel.Channels.TransportBindingElement> 介面。接下來，您必須至少實作 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> 方法和 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=fullName> 屬性。  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> 應該會傳回這個繫結項目的全新複本。在最佳做法中，我們建議繫結項目作者使用複製建構函式 \(其呼叫基底複製建構函式\) 來實作該複製品，然後複製在此類別中的任何其他欄位。  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> –<xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> get 屬性會傳回繫結項目所表示之傳輸通訊協定所適用的 URI 結構描述。例如，<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=fullName> 和 <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=fullName> 會從它們各自的 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> 屬性傳回 “http” 和 “net.tcp”。  
  
#### 編碼繫結項目  
 若要建立新的編碼繫結項目，一開始要先擴充 <xref:System.ServiceModel.Channels.BindingElement> 類別，並實作 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=fullName> 類別。接下來，您必須至少實作 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=fullName> 方法和 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=fullName> 屬性。  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>.傳回這個繫結項目的全新複本。在最佳做法中，我們建議繫結項目作者使用複製建構函式 \(其呼叫基底複製建構函式\) 來實作 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>，然後複製在此類別中的任何其他欄位。  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>.傳回 <xref:System.ServiceModel.Channels.MessageEncoderFactory>，它會提供實作新編碼器 \(應該會擴充 <xref:System.ServiceModel.Channels.MessageEncoder>\) 之實際類別的控制代碼。如需詳細資訊，請參閱 <xref:System.ServiceModel.Channels.MessageEncoderFactory> 和 <xref:System.ServiceModel.Channels.MessageEncoder>。  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>.傳回這個編碼所使用的 <xref:System.ServiceModel.Channels.MessageVersion>，其代表正在使用的 SOAP 和 WS\-Addressing 版本。  
  
 如需以及使用者定義之編碼繫結項目之選擇性方法和屬性的完整清單，請參閱 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>。  
  
 如需建立新繫結項目的詳細資訊，請參閱[建立使用者定義繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)。  
  
 當為您的通道建立了繫結項目之後，請回到[開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)主題，看看您是否要在繫結項目中新增組態檔支援、是否要新增中繼資料發行支援及其新增方式，以及是否要建構將使用您的繫結項目的使用者定義繫結及其建構方式。  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.BindingElement>   
 [開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)   
 [傳輸：UDP](../../../../docs/framework/wcf/samples/transport-udp.md)