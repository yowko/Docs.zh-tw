---
title: 建立使用者定義繫結
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 54a1c8e06991729ea8556d82d31897c522f6d173
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188717"
---
# <a name="creating-user-defined-bindings"></a>建立使用者定義繫結
您有幾種方式可以建立系統不提供的繫結：  
  
-   依據 <xref:System.ServiceModel.Channels.CustomBinding> 類別來建立自訂繫結，此類別是一個容器，可供您填入繫結項目。 接著自訂繫結會新增至服務端點。 您可以程式設計方式，或是透過應用程式組態檔來建立自訂繫結。 若要使用應用程式組態檔的繫結項目，繫結項目必須延伸 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>。 如需有關自訂繫結的詳細資訊，請參閱 <<c0> [ 自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)和<xref:System.ServiceModel.Channels.CustomBinding>。  
  
-   您可以建立衍生自標準繫結的類別。 例如，您可以從 <xref:System.ServiceModel.WSHttpBinding> 衍生類別，並覆寫 <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> 方法來取得繫結項目，並插入自訂繫結項目或是建立特定的安全值。  
  
-   您可以建立新的 <xref:System.ServiceModel.Channels.Binding> 型別以完全掌控整個繫結實作。  
  
## <a name="the-order-of-binding-elements"></a>繫結項目的順序  
 每個繫結項目都代表傳送或接收訊息時的一個處理步驟。 在執行階段，繫結項目會建立通道和接聽項，它們是建立傳出和傳入通道堆疊的必要項目。  
  
 有三種主要的繫結項目：通訊協定繫結項目、 編碼繫結項目和傳輸繫結項目。  
  
 通訊協定繫結項目 – 這些項目代表會處理訊息的較高階處理步驟。 由這些繫結項目所建立的通道與接聽項，可以新增、移除，或是修改訊息內容。 特定繫結可能包含任意數量的通訊協定繫結項目，而這些項目每個都繼承自 <xref:System.ServiceModel.Channels.BindingElement>。 Windows Communication Foundation (WCF) 包含數個通訊協定的繫結項目，包括<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>而<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>。  
  
 編碼繫結程序項目 – 這些項目代表訊息與準備好在網路上進行傳輸的編碼之間的轉換。 典型的 WCF 繫結包含一個編碼繫結項目。 編碼繫結項目範例包含 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>、<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>，和 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>。 如果某個繫結未指定編碼繫結項目，則會使用預設編碼。 當傳輸為 HTTP 和二進位格式，預設為文字。  
  
 傳輸繫結項目 – 這些項目代表傳輸通訊協定上編碼訊息的傳輸。 典型的 WCF 繫結包含一個傳輸繫結項目，繼承自<xref:System.ServiceModel.Channels.TransportBindingElement>。 傳輸繫結項目範例包含 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpTransportBindingElement> 和 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>。  
  
 建立新繫結時，新增的繫結項目順序非常重要。 請務必遵守下列順序加入繫結項目：  
  
|圖層|選項|必要|  
|-----------|-------------|--------------|  
|異動流程|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|否|  
|可靠性|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|否|  
|安全性|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|否|  
|複合雙工|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|否|  
|編碼|文字、二進位、MTOM、自訂|是*|  
|Transport|TCP、具名管道、HTTP、HTTPS、MSMQ、自訂|是|  
  
 * 因為如果未指定的編碼方式，都需要每一個繫結的編碼方式，WCF 會新增預設編碼方式為您。 預設為 Text/XML (適用於 HTTP 和 HTTPS 傳輸) 和 Binary (適用於其他傳輸)。  
  
## <a name="creating-a-new-binding-element"></a>建立新的繫結項目  
 衍生自型別除了<xref:System.ServiceModel.Channels.BindingElement>所提供的 WCF 中，您可以建立自己的繫結項目。 這樣一來，您就可以自訂繫結程序堆疊的建立方式和內含的元件，並使用堆疊中其他系統提供型別共同組成自己的 <xref:System.ServiceModel.Channels.BindingElement>。  
  
 例如，如果您實作了可將訊息記錄至資料庫的 `LoggingBindingElement`，則您必須將其放置到通道堆疊中的傳輸通道上層。 在此情況中，應用程式會建立由 `LoggingBindingElement` 和 `TcpTransportBindingElement` 組成的自訂繫結，如下列範例所示。  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 撰寫新的繫結項目的方式，需視其明確的功能而定。 其中一個範例，[傳輸：UDP](../../../../docs/framework/wcf/samples/transport-udp.md)，提供詳細的說明如何實作某種繫結項目。  
  
## <a name="creating-a-new-binding"></a>建立新繫結  
 您可以透過下列兩種方式運用使用者建立的繫結項目。 上一節說明了第一種方式，亦即透過自訂繫結。 自訂繫結允許使用者根據任意一組繫結項目來建立自己的繫結，包括使用者建立的繫結。  
  
 如果您在一個以上的應用程式中使用繫結，請建立自己的繫結並延伸 <xref:System.ServiceModel.Channels.Binding>。 這樣一來，每次當您想要使用繫結時，都不用重新手動建立自訂繫結。 使用者定義的繫結可讓您定義繫結行為，並包含使用者定義的繫結項目。 而且很*預先封裝*： 您就不必在每次您使用它重建繫結。  
  
 使用者定義的繫結必須至少實作 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 方法和 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> 屬性。  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 方法會傳回新的 <xref:System.ServiceModel.Channels.BindingElementCollection>，其中包含繫結的繫結項目。 經過排序的集合應該會先包含通訊協定繫結項目，而後包含編碼繫結項目，最後才是包含傳輸繫結項目。 當使用 WCF 系統提供繫結項目時，您必須遵循排序規則中指定的繫結項目[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。 此集合一律不得參考使用者定義的繫結類別所參考的物件；如此一來，繫結作者必須在每次呼叫 `Clone()` 時，傳回 <xref:System.ServiceModel.Channels.BindingElementCollection> 的 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>。  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> 屬性代表繫結上正在使用的傳輸通訊協定的 URI 配置。 例如， *WSHttpBinding*並*NetTcpBinding*從其各自傳回"http"和"net.tcp"<xref:System.ServiceModel.Channels.Binding.Scheme%2A>屬性。  
  
 如需使用者定義繫結之選擇性方法與屬性的完整清單，請參閱 <xref:System.ServiceModel.Channels.Binding>。  
  
### <a name="example"></a>範例  
 此範例會在衍生自 `SampleProfileUdpBinding` 的 <xref:System.ServiceModel.Channels.Binding> 中實作設定檔繫結。 `SampleProfileUdpBinding`包含在其中最多四個繫結項目： 一個使用者建立`UdpTransportBindingElement`; 中，系統提供的三個： `TextMessageEncodingBindingElement`， `CompositeDuplexBindingElement`，和`ReliableSessionBindingElement`。  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
## <a name="security-restrictions-with-duplex-contracts"></a>雙工合約的安全性限制  
 並非所有繫結程序項目都能彼此相容。 具體來說，安全性繫結項目一旦與雙工合約併用，會有一些限制。  
  
### <a name="one-shot-security"></a>單次安全性  
 您可以實作 「 單次 」 安全性，其中所有必要的安全性認證來傳送單一訊息，藉由設定`negotiateServiceCredential`的屬性\<訊息 > 組態項目`false`。  
  
 單次驗證無法與雙工合約一起使用。  
  
 對於要求-回覆合約來說，只有當安全性繫結項目底下的繫結堆疊支援建立 <xref:System.ServiceModel.Channels.IRequestChannel> 或 <xref:System.ServiceModel.Channels.IRequestSessionChannel> 執行個體時，才能使用單次驗證。  
  
 對於單向合約來說，如果安全性繫結項目底下的繫結堆疊支援建立 <xref:System.ServiceModel.Channels.IRequestChannel>、<xref:System.ServiceModel.Channels.IRequestSessionChannel>、<xref:System.ServiceModel.Channels.IOutputChannel> 或 <xref:System.ServiceModel.Channels.IOutputSessionChannel> 執行個體時，就能使用單次驗證。  
  
### <a name="cookie-mode-security-context-tokens"></a>Cookie 模式的安全性內容權杖  
 Cookie 模式的安全性內容權杖無法搭配雙工合約一起使用。  
  
 對於要求-回覆合約來說，只有當安全性繫結項目底下的繫結堆疊支援建立 <xref:System.ServiceModel.Channels.IRequestChannel> 或 <xref:System.ServiceModel.Channels.IRequestSessionChannel> 執行個體時，才能使用 Cookie 模型的安全性內容權杖。  
  
 對於單向合約來說，如果安全性繫結項目底下的繫結堆疊支援建立 <xref:System.ServiceModel.Channels.IRequestChannel> 或 <xref:System.ServiceModel.Channels.IRequestSessionChannel> 執行個體時，就能使用 Cookie 模型的安全性內容權杖。  
  
### <a name="session-mode-security-context-tokens"></a>工作階段模式的安全性內容權杖  
 如果安全性繫結項目底下的繫結堆疊支援建立 <xref:System.ServiceModel.Channels.IDuplexChannel> 或 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 執行個體，就能在雙工合約上使用工作階段模式 SCT。  
  
 如果安全性繫結項目底下的繫結堆疊支援建立 <xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IDuplexSessionChannel>、<xref:System.ServiceModel.Channels.IRequestChannel> 或 <xref:System.ServiceModel.Channels.IRequestSessionChannel> 執行個體，就能在要求-回覆合約上使用工作階段模式 SCT。  
  
 如果安全性繫結項目底下的繫結堆疊支援建立 <xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IDuplexSessionChannel>、<xref:System.ServiceModel.Channels.IRequestChannel> 或 <xref:System.ServiceModel.Channels.IRequestSessionChannel> 執行個體，就能在單向合約上使用工作階段模式 SCT。  
  
## <a name="deriving-from-a-standard-binding"></a>衍生自標準繫結  
 您可以不建立全新的繫結類別，而改為擴充其中一個現有的系統提供繫結。 與先前的情況非常類似，這次您必須覆寫 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 屬性的 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> 方法。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.Binding>
- [自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)
