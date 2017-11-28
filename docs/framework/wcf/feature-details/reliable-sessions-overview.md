---
title: "可靠的工作階段概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ddec86fac46da7a93d17ecd55f292471fac2ee5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-sessions-overview"></a>可靠的工作階段概觀

[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] SOAP 可信賴傳訊會在 SOAP 端點之間提供端對端訊息傳輸可靠性。 它會克服不可靠網路上的傳輸失敗與 SOAP 訊息層級失敗來達到這個目的。 尤其，傳遞透過 SOAP 或傳輸媒介傳送的訊息時，它可讓您採用工作階段架構的方式單次並選擇是否依序進行。 提供在含有選擇性排序訊息的工作階段中群組訊息工作階段為基礎的傳遞。

本主題描述如何可靠工作階段，和使用時機，以及如何保護它們。

## <a name="wcf-reliable-sessions"></a>WCF 可靠工作階段

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可靠工作階段會依據 WS-ReliableMessaging 通訊協定定義來實作 SOAP 可信賴傳訊。

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SOAP 可信賴傳訊會在兩個端點之間提供端對端可靠工作階段，而不管用來分隔傳訊端點的媒介數量或型別為何。 這包括任何傳輸不使用 SOAP 的媒介 (例如，HTTP proxy) 或使用 SOAP 的媒介 （例如，SOAP 架構的路由器或橋接器） 所需的訊息在端點之間流動。 可靠工作階段通道支援*互動式*通訊，而這類通道連接的服務同時執行的低延遲，也就是狀況下的交換與處理訊息在相對較短時間間隔。 這種結合方式這些元件同時進行或失敗，因此沒有提供兩者之間的隔離。

可靠工作階段會針對兩種失敗情況進行遮罩處理：

- SOAP 訊息層級的失敗，包括已遺失或重複的訊息，以及以不同於其傳送順序之順序抵達的訊息。

- 傳輸失敗。

可靠工作階段會實作 WS-ReliableMessaging 通訊協定並使用記憶體中傳輸視窗來遮罩 SOAP 訊息層級的失敗，並在發生傳輸失敗時重新建立連線。

TCP 提供給 IP 封包的功能，可靠工作階段也會提供給 SOAP 訊息。 TCP 通訊端連線可在節點之間提供單數、依序的 IP 封包傳輸。 可靠通道會提供同類型的可靠傳輸，但此傳輸在下列情況中會不同於 TCP 通訊端可靠性：

- 可靠性位於 SOAP 訊息層級，且不適用任意大小的位元組封包。

- 可靠性是傳輸中性，不只是用於透過 TCP 傳輸。

- 可靠性未繫結至特定的傳輸工作階段 （例如，TCP 連線提供工作階段），可以使用多個傳輸工作階段並行或連續的可靠工作階段存留期。

- 可靠工作階段適用於寄件者與接收者 SOAP 端點之間，而不管在兩者之間建立連線所需的傳輸連線數量為何。 簡單地說，TCP 可靠性會結束傳輸連線結束位置，而可靠的工作階段提供端對端可靠性。

## <a name="reliable-sessions-and-bindings"></a>可靠工作階段與繫結

如先前所述，可靠工作階段是傳輸中性的特質。 此外，您可以透過許多訊息交換模式，例如要求-回覆或雙工建立可靠工作階段。 A[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]可靠工作階段會公開為一組繫結的屬性。

使用端點上使用可靠工作階段：

- HTTP 傳輸標準繫結：

  - `WsHttpBinding` 並公開要求-回覆或單向合約。

  - 當透過要求-回覆或簡易單向服務合約使用可靠工作階段。

  - `WsDualHttpBinding` 並公開雙工、要求-回覆或單向合約。

  - `WsFederationHttpBinding` 並公開要求-回覆或單向合約。

- TCP 傳輸標準繫結：

  - `NetTcpBinding` 並公開雙工、要求-回覆或單向合約。

任何其他繫結上使用可靠工作階段，藉由建立自訂繫結，例如 HTTPS (如需問題的詳細資訊，請參閱<a href="#reliable-sessions-and-security">可靠工作階段與安全性</a>) 或具名的管道繫結。

您可以堆疊可靠工作階段上不同基礎通道型別，並產生的可靠工作階段通道形狀而有所不同。 用戶端和伺服器所支援的可靠工作階段通道型別取決於所使用的基礎通道型別。 下表列出用戶端上支援做為基礎通道型別功能的工作階段通道型別。

| 支援的可靠工作階段通道型別 &#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | 是               | 是                      | 是              | 是                     |
| `IRequestSessionChannel`                        | 是               | 是                      | 否               | 否                      |
| `IDuplexSessionChannel`                         | 否                | 否                       | 是              | 是                     |

&#8224;支援的通道型別是供泛型值`TChannel`參數值傳遞到<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29>方法。

下表列出伺服器上支援做為基礎通道型別功能的工作階段通道型別。

| 支援的可靠工作階段通道型別 &#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | 是             | 是                    | 是              | 是                     |
| `IReplySessionChannel`                          | 是             | 是                    | 否               | 否                      |
| `IDuplexSessionChannel`                         | 否              | 否                     | 是              | 是                     |

&#8225;支援的通道型別是供泛型值`TChannel`參數值傳遞到<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29>方法。

## <a name="reliable-sessions-and-security"></a>可靠工作階段與安全性

保護可靠工作階段，請務必確保通訊方 （服務與用戶端） 進行驗證，且工作階段中交換之訊息未遭竄改。 此外，務必確保每個個別可靠工作階段的完整性。 受保護可靠工作階段繫結至具有代表並由安全性工作階段通道的安全性內容。 安全性通道會提供安全性工作階段。 在工作階段的建立期間所交換的安全性權杖會接著用來保護可靠工作階段中的訊息安全。

透過可靠工作階段時，TCP 工作階段繫結可靠工作階段。 因此，傳輸安全性可確保安全性也會繫結至可靠工作階段。 在此情況下，會關閉連線的重新建立作業。

唯一的例外是在使用 HTTPS 時。 安全通訊端層 (SSL) 工作階段沒有繫結至可靠工作階段。 這會加諸的威脅，因為共用安全性內容 （SSL 工作階段） 的工作階段未受保護與彼此;這可能會或可能無法真正的威脅，不同的應用程式。

## <a name="using-reliable-sessions"></a>使用可靠工作階段

若要使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可靠工作階段，請使用支援可靠工作階段的繫結來建立端點。 使用其中一個系統提供的繫結的[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]提供啟用可靠工作階段，或建立自己的自訂繫結此。

根據預設，支援且啟用可靠工作階段的系統定義繫結包括：

- <xref:System.ServiceModel.WSDualHttpBinding>

支援可靠工作階段的選項，但不啟用預設的系統提供繫結包括：

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

如需如何建立自訂繫結的範例，請參閱[How to： 使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)。

如需討論[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]支援可靠工作階段，繫結，請參閱[之繫結](../../../../docs/framework/wcf/system-provided-bindings.md)。

## <a name="when-to-use-reliable-sessions"></a>使用可靠工作階段的時機

請務必了解您的應用程式中使用可靠工作階段。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援同時為作用中和執行中之端點間的可靠工作階段。 如果您的應用程式需要下列其中一個端點無法使用的一段時間，然後使用佇列來達到可靠性。

如果情況需要透過 TCP 連接的兩個端點，則 TCP 可能足以提供可靠的訊息交換。 雖然不需要使用可靠工作階段，因為 TCP 時，可確保在封包到達的順序和只能出現一次。

如果您的案例會有任何下列特性，則您必須慎重考慮使用可靠工作階段。

- SOAP 媒介，例如 SOAP 路由器

- Proxy 媒介或傳輸橋接器

- 間歇性連線

- 透過 HTTP 工作階段

## <a name="see-also"></a>請參閱

[使用繫結來設定服務和用戶端](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
[WS 可靠工作階段](../../../../docs/framework/wcf/samples/ws-reliable-session.md)
