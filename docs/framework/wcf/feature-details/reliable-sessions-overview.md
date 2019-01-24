---
title: 可靠的工作階段概觀
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: 6dd90ef800daf236d77c419d48c0857ac2d78aa2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548020"
---
# <a name="reliable-sessions-overview"></a>可靠的工作階段概觀

Windows Communication Foundation (WCF) SOAP 可信賴傳訊提供 SOAP 端點之間的端對端訊息傳輸可靠性。 它會克服不可靠網路上的傳輸失敗與 SOAP 訊息層級失敗來達到這個目的。 尤其，傳遞透過 SOAP 或傳輸媒介傳送的訊息時，它可讓您採用工作階段架構的方式單次並選擇是否依序進行。 工作階段為基礎的傳遞提供群組和選擇性訊息順序方面的工作階段中的訊息。

本主題描述如何可靠工作階段，和使用時機，以及如何保護其安全。

## <a name="wcf-reliable-sessions"></a>WCF 可靠工作階段

WCF 可靠工作階段是實作 SOAP 可信賴傳訊 WS-ReliableMessaging 通訊協定所定義。

WCF SOAP 可信賴傳訊提供兩個端點，不論分隔傳訊端點的媒介的類型或數目之間的端對端可靠工作階段。 這包括任何傳輸媒介不使用 SOAP (例如，HTTP proxy) 或使用 SOAP （例如，SOAP 為基礎的路由器或橋接器） 所需的訊息，以在端點之間流動的媒介。 支援可靠工作階段通道*互動式*通訊以便同時執行這類通道連接的服務，並在低延遲性的也就是的情況下交換與處理訊息在相對較短時間間隔。 此結合表示同時進行這些元件，或失敗，，因此提供兩者之間沒有隔離。

可靠工作階段會針對兩種失敗情況進行遮罩處理：

- SOAP 訊息層級的失敗，包括已遺失或重複的訊息，以及以不同於其傳送順序之順序抵達的訊息。

- 傳輸失敗。

可靠工作階段會實作 WS-ReliableMessaging 通訊協定並使用記憶體中傳輸視窗來遮罩 SOAP 訊息層級的失敗，並在發生傳輸失敗時重新建立連線。

TCP 提供給 IP 封包的功能，可靠工作階段也會提供給 SOAP 訊息。 TCP 通訊端連線可在節點之間提供單數、依序的 IP 封包傳輸。 可靠通道會提供同類型的可靠傳輸，但此傳輸在下列情況中會不同於 TCP 通訊端可靠性：

- 可靠性位於 SOAP 訊息層級，且不適用任意大小的位元組封包。

- 可靠性是傳輸中立，不只是針對透過 TCP 的傳輸。

- 可靠性未繫結至特定的傳輸工作階段 （例如，TCP 連線提供工作階段），可以使用多個傳輸工作階段並行或連續的可靠工作階段存留期。

- 可靠工作階段適用於寄件者與接收者 SOAP 端點之間，而不管在兩者之間建立連線所需的傳輸連線數量為何。 簡單地說，TCP 可靠性會傳輸連線結束位置，而可靠的工作階段提供端對端可靠性。

## <a name="reliable-sessions-and-bindings"></a>可靠工作階段和繫結

如先前所述，可靠工作階段是傳輸中性的特質。 此外，您也可以透過許多訊息交換模式，例如要求-回覆或雙工建立可靠工作階段。 WCF 可靠工作階段會公開為一組繫結的屬性。

您可以使用可靠工作階段上使用的端點：

- HTTP 傳輸標準繫結：

  - `WsHttpBinding` 並公開要求-回覆或單向合約。

  - 在透過要求-回覆或簡易單向服務合約使用可靠工作階段。

  - `WsDualHttpBinding` 並公開雙工、要求-回覆或單向合約。

  - `WsFederationHttpBinding` 並公開要求-回覆或單向合約。

- TCP 傳輸標準繫結：

  - `NetTcpBinding` 並公開雙工、要求-回覆或單向合約。

在其他任何繫結上使用可靠工作階段，方法是建立自訂繫結，例如 HTTPS (如需問題的詳細資訊，請參閱<a href="#reliable-sessions-and-security">可靠工作階段與安全性</a>) 或具名的管道繫結。

您可以堆疊上不同基礎通道型別，可靠工作階段，並產生的可靠工作階段通道類型而有所不同。 用戶端和伺服器所支援的可靠工作階段通道型別取決於所使用的基礎通道型別。 下表列出用戶端上支援做為基礎通道型別功能的工作階段通道型別。

| 支援可靠工作階段通道型別&#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | 是               | 是                      | 是              | 是                     |
| `IRequestSessionChannel`                        | 是               | 是                      | 否               | 否                      |
| `IDuplexSessionChannel`                         | 否                | 否                       | 是              | 是                     |

&#8224;支援的通道型別是泛型所提供的值`TChannel`傳入的參數值<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29>方法。

下表列出伺服器上支援做為基礎通道型別功能的工作階段通道型別。

| 支援可靠工作階段通道型別&#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | 是             | 是                    | 是              | 是                     |
| `IReplySessionChannel`                          | 是             | 是                    | 否               | 否                      |
| `IDuplexSessionChannel`                         | 否              | 否                     | 是              | 是                     |

&#8225;支援的通道型別是泛型所提供的值`TChannel`傳入的參數值<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29>方法。

## <a name="reliable-sessions-and-security"></a>可靠工作階段與安全性

保護可靠工作階段務必要確定通訊雙方 （服務與用戶端） 會驗證和交換工作階段中的訊息未遭竄改。 此外，務必確保每個個別可靠工作階段的完整性。 保護可靠工作階段繫結至具有代表並由安全性工作階段通道的安全性內容。 安全性通道會提供安全性工作階段。 在工作階段的建立期間所交換的安全性權杖會接著用來保護可靠工作階段中的訊息安全。

透過 TCP-S 可靠工作階段時，TCP 工作階段會繫結可靠工作階段。 因此，傳輸安全性可確保安全性也會繫結至可靠工作階段。 在此情況下，會關閉連線的重新建立作業。

唯一的例外是在使用 HTTPS 時。 安全通訊端層 (SSL) 工作階段沒有繫結可靠工作階段。 這會造成威脅，因為共用安全性內容 （SSL 工作階段） 的工作階段不會受到保護彼此;這可能會或可能不是真正的威脅，根據應用程式。

## <a name="using-reliable-sessions"></a>使用可靠工作階段

若要使用 WCF 可靠工作階段，建立支援可靠工作階段的繫結的端點。 使用 WCF 提供可靠的工作階段的系統提供繫結的其中一個已啟用，或建立您自己自訂的繫結此。

根據預設，支援且啟用可靠工作階段的系統定義繫結包括：

- <xref:System.ServiceModel.WSDualHttpBinding>

支援可靠工作階段，但未啟用其中一個預設的系統提供繫結包括：

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

如需如何建立自訂繫結的範例，請參閱[How to:使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)。

如需支援可靠工作階段的 WCF 繫結的討論，請參閱 < [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md)。

## <a name="when-to-use-reliable-sessions"></a>使用可靠工作階段的時機

請務必了解應用程式中使用可靠工作階段的時機。 WCF 支援同時為作用中和執行的端點之間的可靠工作階段。 如果您的應用程式需要有一個端點無法使用一段時間，然後使用佇列來達到可靠性。

如果情況需要透過 TCP 連接的兩個端點，TCP 可能就足以提供可靠的訊息交換。 雖然不需要使用可靠工作階段，因為 TCP 可確保封包抵達順序，以及一次。

如果您的案例會有任何下列特性，則您必須認真考慮使用可靠工作階段。

- SOAP 媒介，例如 SOAP 路由器

- Proxy 媒介或傳輸橋接器

- 間歇性連線

- 透過 HTTP 工作階段

## <a name="see-also"></a>另請參閱

- [使用繫結設定服務與用戶端](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [WS 可靠工作階段](../../../../docs/framework/wcf/samples/ws-reliable-session.md)
