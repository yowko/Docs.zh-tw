---
title: "可靠的工作階段概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
caps.latest.revision: 30
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 30
---
# 可靠的工作階段概觀
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] SOAP 可信賴傳訊會在 SOAP 端點之間提供端對端訊息傳輸可靠性。它會克服不可靠網路上的傳輸失敗與 SOAP 訊息層級失敗來達到這個目的。尤其，傳遞透過 SOAP 或傳輸媒介傳送的訊息時，它可讓您採用工作階段架構的方式單次並選擇是否依序進行。採用工作階段架構的傳遞方式會透過 \(選用\) 訊息排序方式將工作階段中的訊息分組。  
  
 下列討論內容說明何謂可靠的工作階段、其使用方式與時機，以及如何保護其安全。  
  
## WCF 可靠工作階段  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可靠工作階段會依據 WS\-ReliableMessaging 通訊協定定義來實作 SOAP 可信賴傳訊。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SOAP 可信賴傳訊會在兩個端點之間提供端對端可靠工作階段，而不管用來分隔傳訊端點的媒介數量或型別為何。這包括不是使用 SOAP 的任何傳輸媒介 \(例如，HTTP Proxy\) 或使用 SOAP 的媒介 \(例如，SOAP 架構的路由器或橋接器\)，而訊息在端點之間流動時需要這些媒介。可靠工作階段通道支援「互動式」通訊，讓透過此類通道連接的服務可以同時執行並在低延遲性的條件下 \(亦即在相對較短的時間間隔內\) 交換與處理訊息。這種結合方式代表這些組件會同時進行或失敗，而且之間沒有任何隔離。  
  
 可靠工作階段會針對兩種失敗情況進行遮罩處理：  
  
-   SOAP 訊息層級的失敗，包括已遺失或重複的訊息，以及以不同於其傳送順序之順序抵達的訊息。  
  
-   傳輸失敗。  
  
 可靠工作階段會實作 WS\-ReliableMessaging 通訊協定並使用記憶體中傳輸視窗來遮罩 SOAP 訊息層級的失敗，並在發生傳輸失敗時重新建立連線。  
  
 TCP 提供給 IP 封包的功能，可靠工作階段也會提供給 SOAP 訊息。TCP 通訊端連線可在節點之間提供單數、依序的 IP 封包傳輸。可靠通道會提供同類型的可靠傳輸，但此傳輸在下列情況中會不同於 TCP 通訊端可靠性：  
  
-   可靠性位於 SOAP 訊息層級，且不適用任意大小的位元組封包。  
  
-   可靠性具有傳輸中性的特質，但不僅適用透過 TCP 的傳輸。  
  
-   可靠性與特定的傳輸通訊協定 \(例如，TCP 連線所提供的工作階段\) 沒有密切的關係，並可在可靠工作階段的存留期內並行或連續使用多個傳輸工作階段。  
  
-   可靠工作階段適用於寄件者與接收者 SOAP 端點之間，而不管在兩者之間建立連線所需的傳輸連線數量為何。簡單地說，TCP 可靠性會在傳輸連線結束的地方結束，而可靠工作階段則是提供端對端可靠性。  
  
## 可靠工作階段與繫結  
 如先前所述，可靠工作階段具有傳輸中性的特質，因此可以在許多傳輸上實作。同時，可靠工作階段也可在許多訊息交換模式中建立，例如要求\-回覆或雙工模式。因此，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可靠工作階段會公開為一組繫結的屬性。  
  
 您可以在使用下列項目的端點上使用可靠工作階段：  
  
-   HTTP 傳輸標準繫結：  
  
    -   `WsHttpBinding` 並公開要求\-回覆或單向合約。  
  
    -   可在透過要求\-回覆或簡易單向服務合約使用可靠工作階段時加以使用。  
  
    -   `WsDualHttpBinding` 並公開雙工、要求\-回覆或單向合約。  
  
    -   `WsFederationHttpBinding` 並公開要求\-回覆或單向合約。  
  
-   TCP 傳輸標準繫結：  
  
    -   `NetTcpBinding` 並公開雙工、要求\-回覆或單向合約。  
  
 您也可以建立 HTTPS \(如需相關問題的詳細資訊，請參閱本主題稍後的「可靠工作階段與安全性」一節\) 或是具名管道繫結之類的自訂繫結，以便在其他任何繫結上使用可靠工作階段。  
  
 您可以在不同的基礎通道型別上堆疊可靠工作階段，如此產生的可靠工作階段通道形狀也會不一樣。在用戶端與伺服器上，所支援的可靠工作階段通道型別取決於使用的基礎通道型別。下表列出用戶端上支援做為基礎通道型別功能的工作階段通道型別。  
  
|支援的可靠工作階段通道型別 \(在指定的基礎通道型別前提下，支援的 `TChannel` 值\)|`IRequestChannel`|`IRequestSessionChanne`l|`IDuplexChannel`|`IDuplexSessionChannel`|  
|------------------------------------------------------|-----------------------|------------------------------|----------------------|-----------------------------|  
|`IOutputSessionChannel`|是|是|是|是|  
|`IRequestSessionChannel`|是|是|否|否|  
|`IDuplexSessionChannel`|否|否|是|是|  
  
 支援的通道型別即是傳入 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> 方法之泛型 `TChannel` 參數值的可用值。  
  
 下表列出伺服器上支援做為基礎通道型別功能的工作階段通道型別。  
  
|支援的可靠工作階段通道型別 \(在指定的基礎通道型別前提下，支援的 `TChannel` 值\)|`IReplyChannel`|`IReplySessionChannel`|`IDuplexChannel`|`IDuplexSessionChannel`|  
|------------------------------------------------------|---------------------|----------------------------|----------------------|-----------------------------|  
|`IInputSessionChannel`|是|是|是|是|  
|`IReplySessionChannel`|是|是|否|否|  
|`IDuplexSessionChannel`|否|否|是|是|  
  
 支援的通道型別即是傳入 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> 方法之泛型 `TChannel` 參數值的可用值。  
  
## 可靠工作階段與安全性  
 保護可靠工作階段的安全很重要，以確保進行通訊的各方 \(服務與用戶端\) 都能受到驗證，而且在工作階段中交換的訊息也不會遭到竄改。此外，還需要確保每個個別可靠工作階段的完整性。您可以將可靠工作階段繫結至由安全性工作階段通道所代表與管理的安全性內容來保護其安全。安全性通道會提供安全性工作階段。在工作階段的建立期間所交換的安全性權杖會接著用來保護可靠工作階段中的訊息安全。  
  
 當可靠工作階段為透過 TCP\-S 時，TCP 工作階段會與可靠工作階段有密切的關係，這樣一來傳輸安全性就可以確保安全性也與可靠工作階段有密切的關係。在此情況下，會關閉連線的重新建立作業。  
  
 唯一的例外是在使用 HTTPS 時。Secure Sockets Layer \(SSL\) 工作階段不會繫結至可靠工作階段。這樣會帶來威脅，因為共用安全性內容的工作階段 \(SSL 工作階段\) 彼此並未受到保護；對於不同的應用程式來說，這可能是 \(也可能不是\) 一項真正的威脅。  
  
## 使用可靠工作階段  
 若要使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可靠工作階段，請使用支援可靠工作階段的繫結來建立端點。使用其中一個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所提供且啟用可靠工作階段的系統提供繫結，或是自行建立會啟用可靠工作階段的自訂繫結。根據預設，支援且啟用可靠工作階段的系統定義繫結包括：  
  
-   <xref:System.ServiceModel.WSDualHttpBinding>  
  
 根據預設，選擇性支援可靠工作階段，但並未加以啟用的系統提供繫結包括：  
  
-   <xref:System.ServiceModel.WSHttpBinding>  
  
-   <xref:System.ServiceModel.WSFederationHttpBinding>  
  
-   <xref:System.ServiceModel.NetTcpBinding>  
  
 如需如何建立自訂繫結的範例，請參閱 [HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)。  
  
 如需支援可靠工作階段的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結討論，請參閱[系統提供的繫結](../../../../docs/framework/wcf/system-provided-bindings.md)。  
  
## 使用可靠工作階段的時機  
 了解何時可以在應用程式中使用可靠工作階段很重要。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援同時為作用中和執行中之端點間的可靠工作階段。如果您的應用程式需要在一段時間內讓其中一個端點無法使用，則您可以使用佇列來達到可靠性。  
  
 如果情況需要兩個透過 TCP 連接的端點，則 TCP 應該就足以提供可靠訊息交換 \(儘管不需要使用可靠工作階段\)；TCP 會確保封包依序抵達且只抵達一次。  
  
 如果您的情況具有下列任何一項特徵，則您必須慎重考慮使用可靠工作階段：  
  
-   SOAP 媒介，例如 SOAP 路由器。  
  
-   Proxy 媒介或傳輸橋接器。  
  
-   斷斷續續的連線。  
  
-   透過 HTTP 的工作階段。  
  
## 請參閱  
 [使用繫結來設定服務和用戶端](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
 [WS 可靠工作階段](../../../../docs/framework/wcf/samples/ws-reliable-session.md)