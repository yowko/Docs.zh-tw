---
title: 可靠的工作階段概觀
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: a85a34c5e2ec7928c01586e4b01cdf5e90e896a7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601084"
---
# <a name="reliable-sessions-overview"></a>可靠的工作階段概觀

Windows Communication Foundation （WCF） SOAP 可靠訊息提供 SOAP 端點之間的端對端訊息傳輸可靠性。 它會克服不可靠網路上的傳輸失敗與 SOAP 訊息層級失敗來達到這個目的。 尤其，傳遞透過 SOAP 或傳輸媒介傳送的訊息時，它可讓您採用工作階段架構的方式單次並選擇是否依序進行。 以會話為基礎的傳遞可讓您以選擇性的訊息順序來分組會話中的訊息。

本主題描述可靠的會話、如何及何時使用它們，以及如何保護它們。

## <a name="wcf-reliable-sessions"></a>WCF 可靠會話

WCF 可靠會話是由 WS-RELIABLEMESSAGING 通訊協定所定義的 SOAP 可靠訊息執行。

WCF SOAP 可靠訊息會在兩個端點之間提供端對端可靠會話，而不論分隔訊息端點的媒介數目或類型為何。 這包括不使用 SOAP （例如 HTTP proxy）的任何傳輸媒介，或使用 SOAP 的媒介（例如，以 SOAP 為基礎的路由器或橋接器），這是訊息在端點之間流動所需的。 可靠的會話通道支援*互動式*通訊，讓這類通道所連接的服務同時執行，並在低延遲的情況下（也就是在相對較短的時間間隔內）交換和處理訊息。 這種結合表示這些元件會將進度一起或一起故障，因此不會在兩者之間提供隔離。

可靠工作階段會針對兩種失敗情況進行遮罩處理：

- SOAP 訊息層級的失敗，包括已遺失或重複的訊息，以及以不同於其傳送順序之順序抵達的訊息。

- 傳輸失敗。

可靠工作階段會實作 WS-ReliableMessaging 通訊協定並使用記憶體中傳輸視窗來遮罩 SOAP 訊息層級的失敗，並在發生傳輸失敗時重新建立連線。

TCP 提供給 IP 封包的功能，可靠工作階段也會提供給 SOAP 訊息。 TCP 通訊端連線可在節點之間提供單數、依序的 IP 封包傳輸。 可靠通道會提供同類型的可靠傳輸，但此傳輸在下列情況中會不同於 TCP 通訊端可靠性：

- 可靠性位於 SOAP 訊息層級，且不適用任意大小的位元組封包。

- 可靠性是以傳輸為中性，而不只是透過 TCP 傳輸。

- 可靠性並不會系結至特定的傳輸會話（例如，TCP 連線提供的會話），而且可以在可靠會話的存留期內同時或連續使用多個傳輸會話。

- 可靠工作階段適用於寄件者與接收者 SOAP 端點之間，而不管在兩者之間建立連線所需的傳輸連線數量為何。 簡單地說，TCP 可靠性會在傳輸連線結束的位置結束，而可靠會話會提供端對端的可靠性。

## <a name="reliable-sessions-and-bindings"></a>可靠的會話和系結

如先前所述，可靠會話是傳輸中性的。 此外，您也可以透過許多訊息交換模式（例如要求-回復或雙工）來建立可靠的會話。 WCF 可靠會話會公開為一組系結的屬性。

在使用的端點上使用可靠會話：

- HTTP 傳輸標準繫結：

  - `WsHttpBinding` 並公開要求-回覆或單向合約。

  - 在要求-回復或簡單單向服務合約上使用可靠會話時。

  - `WsDualHttpBinding` 並公開雙工、要求-回覆或單向合約。

  - `WsFederationHttpBinding` 並公開要求-回覆或單向合約。

- TCP 傳輸標準繫結：

  - `NetTcpBinding` 並公開雙工、要求-回覆或單向合約。

藉由建立自訂系結（例如 HTTPS）（如需問題的詳細資訊，請參閱<a href="#reliable-sessions-and-security">可靠會話和安全性</a>）或具名管道系結，在任何其他系結上使用可靠會話。

您可以在不同的基礎通道類型上堆疊可靠會話，而產生的可靠會話通道圖形會有所不同。 在用戶端和伺服器上，支援的可靠會話通道類型取決於所使用的基礎通道類型。 下表列出用戶端上支援做為基礎通道型別功能的工作階段通道型別。

| 支援的可靠會話通道類型&#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | 是               | 是                      | 是              | 是                     |
| `IRequestSessionChannel`                        | 是               | 是                      | 否               | 否                      |
| `IDuplexSessionChannel`                         | 否                | 否                       | 是              | 是                     |

&#8224;支援的通道類型是 `TChannel` 傳遞至方法之泛型參數值的可用值 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> 。

下表列出伺服器上支援做為基礎通道型別功能的工作階段通道型別。

| 支援的可靠會話通道類型&#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | 是             | 是                    | 是              | 是                     |
| `IReplySessionChannel`                          | 是             | 是                    | 否               | 否                      |
| `IDuplexSessionChannel`                         | 否              | 否                     | 是              | 是                     |

&#8225;支援的通道類型是 `TChannel` 傳遞至方法之泛型參數值的可用值 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> 。

## <a name="reliable-sessions-and-security"></a>可靠的會話和安全性

保護可靠會話的安全，是為了確保通訊方（服務和用戶端）經過驗證，而且會話中交換的訊息不會遭到篡改。 此外，請務必確保每個個別可靠會話的完整性。 可靠會話的保護方式是將它系結至安全性會話通道所表示和管理的安全性內容。 安全性通道會提供安全性工作階段。 在工作階段的建立期間所交換的安全性權杖會接著用來保護可靠工作階段中的訊息安全。

當可靠會話透過 TCP 時，TCP 會話會系結至可靠會話。 因此，傳輸安全性可確保安全性也會系結到可靠的會話。 在此情況下，會關閉連線的重新建立作業。

唯一的例外是在使用 HTTPS 時。 安全通訊端層（SSL）會話未系結至可靠會話。 這會造成威脅，因為共用安全性內容（SSL 會話）的會話不會彼此保護;這可能是根據應用程式而定，可能不是真正的威脅。

## <a name="using-reliable-sessions"></a>使用可靠會話

若要使用 WCF 可靠會話，請使用支援可靠會話的系結來建立端點。 使用 WCF 提供的其中一個系統提供系結，並啟用可靠會話，或建立您自己的自訂系結來執行這項工作。

根據預設，支援且啟用可靠工作階段的系統定義繫結包括：

- <xref:System.ServiceModel.WSDualHttpBinding>

系統提供的系結，支援可靠會話作為選項，但預設為不啟用，其中包括：

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

如需如何建立自訂系結的範例，請參閱[如何：使用 HTTPS 建立自訂可靠會話](how-to-create-a-custom-reliable-session-binding-with-https.md)系結。

如需支援可靠會話之 WCF 系結的討論，請參閱[系統提供](../system-provided-bindings.md)的系結。

## <a name="when-to-use-reliable-sessions"></a>使用可靠會話的時機

請務必瞭解在應用程式中使用可靠會話的時機。 WCF 支援同時處於作用中狀態和作用中的端點之間的可靠會話。 如果您的應用程式要求其中一個端點在一段時間內無法使用，則請使用佇列來達到可靠性。

如果案例需要透過 TCP 連線的兩個端點，則 TCP 可能就足以提供可靠的訊息交換。 雖然不一定要使用可靠會話，因為 TCP 會確保封包只會依序送達一次。

如果您的案例具有下列任何特性，則您必須認真考慮使用可靠會話。

- SOAP 媒介，例如 SOAP 路由器

- Proxy 媒介或傳輸橋接器

- 間歇連線能力

- 透過 HTTP 的會話

## <a name="see-also"></a>請參閱

- [使用繫結設定服務與用戶端](../using-bindings-to-configure-services-and-clients.md)
- [WS 可靠工作階段](../samples/ws-reliable-session.md)
