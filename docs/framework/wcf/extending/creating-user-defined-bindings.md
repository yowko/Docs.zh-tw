---
title: 建立使用者定義繫結
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 34100569dc5cd5a340abca66fedca40ba21c1e0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185636"
---
# <a name="creating-user-defined-bindings"></a>建立使用者定義繫結
您有幾種方式可以建立系統不提供的繫結：  
  
- 依據 <xref:System.ServiceModel.Channels.CustomBinding> 類別來建立自訂繫結，此類別是一個容器，可供您填入繫結項目。 接著自訂繫結會新增至服務端點。 您可以程式設計方式，或是透過應用程式組態檔來建立自訂繫結。 若要使用應用程式組態檔的繫結項目，繫結項目必須延伸 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>。 有關自訂綁定的詳細資訊，請參閱[自訂綁定](custom-bindings.md)和<xref:System.ServiceModel.Channels.CustomBinding>。  
  
- 您可以建立衍生自標準繫結的類別。 例如，您可以從 <xref:System.ServiceModel.WSHttpBinding> 衍生類別，並覆寫 <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> 方法來取得繫結項目，並插入自訂繫結項目或是建立特定的安全值。  
  
- 您可以建立新的 <xref:System.ServiceModel.Channels.Binding> 型別以完全掌控整個繫結實作。  
  
## <a name="the-order-of-binding-elements"></a>繫結項目的順序  
 每個繫結項目都代表傳送或接收訊息時的一個處理步驟。 在執行階段，繫結項目會建立通道和接聽項，它們是建立傳出和傳入通道堆疊的必要項目。  
  
 繫結項目主要分為三種：通訊協定繫結項目、編碼繫結項目，和傳輸繫結項目。  
  
 通訊協定繫結項目 – 這些項目代表會處理訊息的較高階處理步驟。 由這些繫結項目所建立的通道與接聽項，可以新增、移除，或是修改訊息內容。 特定繫結可能包含任意數量的通訊協定繫結項目，而這些項目每個都繼承自 <xref:System.ServiceModel.Channels.BindingElement>。 Windows 通信基礎 （WCF） 包括多個協定繫結元素<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>，包括<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>和 。  
  
 編碼繫結程序項目 – 這些項目代表訊息與準備好在網路上進行傳輸的編碼之間的轉換。 典型的 WCF 綁定只包括一個編碼繫結元素。 編碼繫結項目範例包含 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>、<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>，和 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>。 如果某個繫結未指定編碼繫結項目，則會使用預設編碼。 當傳輸為 HTTP 和二進位格式，預設為文字。  
  
 傳輸繫結項目 – 這些項目代表傳輸通訊協定上編碼訊息的傳輸。 典型的 WCF 綁定僅包括一個傳輸繫結元素，該元素<xref:System.ServiceModel.Channels.TransportBindingElement>從 繼承。 傳輸繫結項目範例包含 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpTransportBindingElement> 和 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>。  
  
 建立新繫結時，新增的繫結項目順序非常重要。 請務必遵守下列順序加入繫結項目：  
  
|階層|選項。|必要|  
|-----------|-------------|--------------|  
|異動流程|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|否|  
|可靠性|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|否|  
|安全性|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|否|  
|複合雙工|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|否|  
|編碼|文字、二進位、MTOM、自訂|是\*|  
|傳輸|TCP、具名管道、HTTP、HTTPS、MSMQ、自訂|是|  
  
\*由於每個綁定都需要編碼，因此如果未指定編碼，則 WCF 會為您添加預設編碼。 預設為 Text/XML (適用於 HTTP 和 HTTPS 傳輸) 和 Binary (適用於其他傳輸)。  
  
## <a name="creating-a-new-binding-element"></a>建立新的繫結項目  
 除了從<xref:System.ServiceModel.Channels.BindingElement>WCF 提供的類型派生之外，您還可以創建自己的繫結元素。 這樣一來，您就可以自訂繫結程序堆疊的建立方式和內含的元件，並使用堆疊中其他系統提供型別共同組成自己的 <xref:System.ServiceModel.Channels.BindingElement>。  
  
 例如，如果您實作了可將訊息記錄至資料庫的 `LoggingBindingElement`，則您必須將其放置到通道堆疊中的傳輸通道上層。 在此情況中，應用程式會建立由 `LoggingBindingElement` 和 `TcpTransportBindingElement` 組成的自訂繫結，如下列範例所示。  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),
  new TcpTransportBindingElement()  
);  
```  
  
 撰寫新的繫結項目的方式，需視其明確的功能而定。 其中一個示例，[傳輸：UDP](../samples/transport-udp.md)，提供了如何實現一種繫結元素的詳細說明。  
  
## <a name="creating-a-new-binding"></a>建立新繫結  
 您可以透過下列兩種方式運用使用者建立的繫結項目。 上一節說明了第一種方式，亦即透過自訂繫結。 自訂繫結允許使用者根據任意一組繫結項目來建立自己的繫結，包括使用者建立的繫結。  
  
 如果您在一個以上的應用程式中使用繫結，請建立自己的繫結並延伸 <xref:System.ServiceModel.Channels.Binding>。 這樣一來，每次當您想要使用繫結時，都不用重新手動建立自訂繫結。 使用者定義的繫結可讓您定義繫結行為，並包含使用者定義的繫結項目。 它是*預打包的*：您不必每次使用它時都重新生成綁定。  
  
 使用者定義的繫結必須至少實作 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 方法和 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> 屬性。  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 方法會傳回新的 <xref:System.ServiceModel.Channels.BindingElementCollection>，其中包含繫結的繫結項目。 經過排序的集合應該會先包含通訊協定繫結項目，而後包含編碼繫結項目，最後才是包含傳輸繫結項目。 使用 WCF 系統提供的繫結元素時，必須遵循[自訂綁定](custom-bindings.md)中指定的繫結元素排序規則。 此集合一律不得參考使用者定義的繫結類別所參考的物件；如此一來，繫結作者必須在每次呼叫 `Clone()` 時，傳回 <xref:System.ServiceModel.Channels.BindingElementCollection> 的 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>。  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> 屬性代表繫結上正在使用的傳輸通訊協定的 URI 配置。 例如 *，WSHttpBinding*和*NetTcpBinding*從各自的<xref:System.ServiceModel.Channels.Binding.Scheme%2A>屬性返回"HTTP"和"net.tcp"。  
  
 如需使用者定義繫結之選擇性方法與屬性的完整清單，請參閱 <xref:System.ServiceModel.Channels.Binding>。  
  
### <a name="example"></a>範例  
 此範例會在衍生自 `SampleProfileUdpBinding` 的 <xref:System.ServiceModel.Channels.Binding> 中實作設定檔繫結。 中`SampleProfileUdpBinding`最多包含四個繫結元素：一個使用者創建的`UdpTransportBindingElement`繫結元素;和提供三個系統： `TextMessageEncodingBindingElement` `CompositeDuplexBindingElement`、`ReliableSessionBindingElement`和 。  
  
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
 通過將`negotiateServiceCredential`\<消息的屬性>配置元素設置為，可以實現"一次性"安全性，其中所有必要的安全憑據都以一條消息形式發送`false`。  
  
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
- [自訂繫結](custom-bindings.md)
