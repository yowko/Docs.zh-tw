---
title: 使用工作階段
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: fc7b86f3f2c2c6276681c324dbe9a390fdfdafd4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320921"
---
# <a name="using-sessions"></a>使用工作階段
在 Windows Communication Foundation (WCF) 應用程式*工作階段*與一組訊息相互關聯至對話。 WCF 工作階段的不同中可用的工作階段物件[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]應用程式支援不同的行為，以及控制的方式。 本主題描述在 WCF 中的工作階段啟用功能的應用程式，以及如何使用它們。  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Windows Communication Foundation 應用程式中的工作階段  
 當服務合約指定其需要工作階段時，該合約會指定所有的呼叫 (即支援呼叫的基礎訊息交換) 必須是同一個對話的一部分。 如果合約指定其允許使用工作階段，但不需要工作階段，則用戶端可以連線，並選擇是否要建立工作階段。 如果工作階段結束，而且某個訊息已透過相同的通道傳送，就會擲回例外狀況。  
  
 WCF 工作階段具有下列主要概念的功能：  
  
-   工作階段是由呼叫的應用程式 (WCF 用戶端) 明確地啟始及終止。  
  
-   工作階段期間傳遞的訊息是依其接收的順序進行處理。  
  
-   工作階段會將一群訊息互相關聯為對話。 可能會有不同類型的相互關聯。 例如，某個工作階段架構通道可能會根據共用的網路連線將訊息相互關聯，而另一個工作階段架構通道可能會根據訊息本文內的共用標記將訊息相互關聯。 這些可以衍生自工作階段的功能視相互關聯的本質而定。  
  
-   沒有與 WCF 工作階段相關聯的一般資料存放區。  
  
 如果您熟悉<xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType>類別中[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]應用程式和功能提供，您可能會注意到這種種類的工作階段和 WCF 工作階段的下列差異：  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 工作階段一律由伺服器啟動。  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 工作階段具有隱含未排序特性。  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 工作階段提供了跨要求的一般資料儲存機制。  
  
 本主題內容：  
  
-   使用服務模型層中工作階段架構繫結時的預設執行行為。  
  
-   功能，提供 WCF 工作階段架構和系統提供繫結類型。  
  
-   如何建立會宣告工作階段需求的合約。  
  
-   如何了解並控制工作階段的建立與終止，以及工作階段與服務執行個體之間的關係。  
  
## <a name="default-execution-behavior-using-sessions"></a>使用工作階段的預設執行行為  
 會嘗試初始化工作階段的繫結稱為「 *工作階段架構* 」(Session-based) 繫結。 服務合約會指定其需要、允許，或拒絕工作階段架構繫結，方法是將服務合約介面 (或類別) 上的 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> 屬性設為其中一個 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> 列舉值。 根據預設，這個屬性的值是<xref:System.ServiceModel.SessionMode.Allowed>，這表示如果用戶端工作階段為基礎的繫結使用的 WCF 服務實作，服務會建立並使用提供的工作階段。  
  
 當 WCF 服務接受用戶端工作階段時，預設會啟用下列功能：  
  
1. WCF 用戶端物件之間的所有呼叫是由相同的服務執行個體都處理。  
  
2. 不同的工作階段架構繫結會提供額外的功能。  
  
## <a name="system-provided-session-types"></a>系統提供的工作階段類型  
 工作階段架構繫結支援服務執行個體與特定工作階段之間的預設關聯。 然而，除了啟用先前所述的工作階段架構執行個體控制之外，不同的工作階段架構繫結也支援不同的功能。  
  
 WCF 會提供下列類型的工作階段為基礎的應用程式的行為：  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> 支援安全性工作階段，其中通訊兩端均同意特定安全對話。 如需詳細資訊，請參閱 < [Securing Services](../../../docs/framework/wcf/securing-services.md)。 例如， <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> 繫結同時支援安全性工作階段與可靠工作階段，但根據預設，只會使用加密並以數位方式簽署訊息的安全工作階段。  
  
-   <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> 繫結支援 TCP/IP 架構工作階段，可確保所有訊息都在通訊端層級由連線建立相互關聯。  
  
-   <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> 項目會實作 WS-ReliableMessaging 規格，支援可在其中將訊息設定為依序傳遞且只傳遞一次的可靠工作階段，確保即使訊息在對話期間行經多個節點仍會收到訊息。 如需詳細資訊，請參閱 <<c0> [ 可靠工作階段](../../../docs/framework/wcf/feature-details/reliable-sessions.md)。  
  
-   <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> 繫結提供 MSMQ 資料包工作階段。 如需詳細資訊，請參閱 < [WCF 中的佇列](../../../docs/framework/wcf/feature-details/queues-in-wcf.md)。  
  
 設定 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> 屬性不會指定合約所需的工作階段類型，只代表它需要工作階段。  
  
## <a name="creating-a-contract-that-requires-a-session"></a>建立需要工作階段的合約  
 建立需要工作階段的合約表示服務合約所宣告的作業群組必須都在同一個工作階段中執行，而且必須依序傳遞訊息。 若要對服務合約所需要的工作階段支援層級進行判斷提示，請將您服務合約介面或類別的 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> 屬性設為 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> 列舉的值，以指定合約是否：  
  
-   需要工作階段。  
  
-   允許用戶端建立工作階段。  
  
-   禁止工作階段。  
  
 但是，設定 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> 屬性不會指定合約所需的工作階段架構行為類型， 它會指示 WCF 在執行階段確認的服務不會則否，或可以建立工作階段設定繫結 （這會建立通訊通道） 時實作的服務。 同時，繫結可以其選擇的任何工作階段架構行為類型 (安全性、傳輸、可靠或某種組合) 滿足該需求， 實際的行為則視選取的 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> 值而定。 如果設定的服務繫結不符合 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>的值，就會擲回例外狀況。 支援工作階段的繫結及其建立的通道都稱為工作階段架構繫結和通道。  
  
 下列服務合約指定 `ICalculatorSession` 中的所有作業必須在工作階段中交換。 除了 `Equals` 方法以外，任何作業都不會將值傳回呼叫者。 然而， `Equals` 方法不會採用任何參數，因此只能在工作階段中傳回非零的值，而其中資料已經傳遞至其他作業。 此合約需要工作階段才能正確運作， 如果缺乏與特定用戶端關聯的工作階段，服務執行個體便無法得知此用戶端先前傳送了哪些資料。  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 如果服務允許使用工作階段，則會在用戶端初始化工作階段後建立一個工作階段並加以使用；否則，將不會建立任何工作階段。  
  
## <a name="sessions-and-service-instances"></a>工作階段與服務執行個體  
 如果您使用預設的執行個體在 WCF 中的行為，WCF 用戶端物件之間的所有呼叫都會都處理由相同的服務執行個體。 因此，在應用程式層級，您可以將工作階段視為一個類似本機呼叫行為的啟用應用程式行為。 例如，當您建立本機物件時：  
  
-   會呼叫建構函式。  
  
-   對 WCF 用戶端物件參考的所有後續的呼叫會由相同的物件執行個體處理。  
  
-   會在終結物件參考時呼叫解構函式 (Destructor)。  
  
 只要是使用預設的服務執行個體行為，工作階段就會在用戶端與服務之間啟用類似的行為。 如果服務合約需要或支援工作階段，您可以設定 <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> 和 <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> 屬性，將一或多個合約作業標示為初始化工作階段或終止工作階段。  
  
 「*初始化作業* 」(Initiating Operation) 是指必須當做新工作階段第一個作業呼叫的作業。 只有在已呼叫至少一個初始化作業後才能呼叫非初始化作業。 因此，您可以宣告設計用來接收服務執行個體開頭適用之用戶端輸入的初始化作業，為服務建立一種工作階段建構函式 (但是，狀態會與工作階段而非服務物件相關聯)。  
  
 相反地，「*終止作業*」(Terminating Operation) 則必須當做現有工作階段的最後一則訊息來呼叫。 在預設案例中，WCF 會在其中關聯著服務的工作階段關閉後回收服務物件及其內容。 因此，您可以宣告設計用來執行服務執行個體結尾適用之函式的終止作業，藉此建立一種解構函式。  
  
> [!NOTE]
>  雖然預設行為與本機建構函式和解構函式有相似之處，但也只是相似而已。 初始化或終止作業，或同時在相同的時間，可以是任何 WCF 服務作業。 此外，在預設案例中，您可以不按次序且不限次數地呼叫啟始作業。一旦建立工作階段並使其與執行個體產生關聯，就不能再建立其他工作階段，除非您明確地控制服務執行個體的存留期 (管理 <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> 物件)。 最後，狀態會與工作階段而非服務物件相關聯。  
  
 例如，`ICalculatorSession`在上述範例中使用的合約需要 WCF 用戶端物件第一次呼叫`Clear`此 WCF 用戶端物件的工作階段的作業之前的任何其他作業，應該終止時它會呼叫`Equals`作業。 下列程式碼範例示範強制執行這些要求的合約。 必須先呼叫`Clear` ，才能起始工作階段，而該工作階段會在呼叫 `Equals` 時結束。  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 服務不會啟動用戶端的工作階段。 在 WCF 用戶端應用程式，工作階段架構通道的存留期和工作階段本身的存留期之間存在直接的關聯性。 因此，用戶端會藉由建立新的工作階段架構通道來建立新工作階段，然後適當地關閉工作階段架構通道來終止現有的工作階段。 用戶端會呼叫下列其中一項，藉此啟動服務端點的工作階段：  
  
-   通道上藉由呼叫<xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 所傳回的 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>。  
  
-   <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> 所產生 WCF 用戶端物件上[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  
  
-   在任一種 WCF 用戶端物件上的初始化作業 （根據預設，所有作業會都起始）。 呼叫第一項作業時，WCF 用戶端物件會自動開啟通道，並起始工作階段。  
  
 一般來說，用戶端會呼叫下列其中一項，藉此結束服務端點的工作階段：  
  
-   通道上藉由呼叫<xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> 所傳回的 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>。  
  
-   <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> 在 Svcutil.exe 所產生的 WCF 用戶端物件。  
  
-   在任一種 WCF 用戶端物件上的終止作業 （根據預設，就會終止任何作業; 合約必須明確指定終止作業）。 呼叫第一項作業時，WCF 用戶端物件會自動開啟通道，並起始工作階段。  
  
 如需範例，請參閱[如何：建立 Service That Requires Sessions](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) ，以及[Default Service Behavior](../../../docs/framework/wcf/samples/default-service-behavior.md)並[Instancing](../../../docs/framework/wcf/samples/instancing.md)範例。  
  
 如需有關用戶端和工作階段的詳細資訊，請參閱 <<c0> [ 使用 WCF 用戶端存取服務](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)。  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>與 InstanceContext 設定互動的工作階段  
 合約內的 <xref:System.ServiceModel.SessionMode> 列舉與 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> 屬性之間會進行互動，以控制通道和特定服務物件之間的關聯。 如需詳細資訊，請參閱 <<c0> [ 工作階段，Instancing，and Concurrency](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)。  
  
### <a name="sharing-instancecontext-objects"></a>共用 InstanceContext 物件  
 您也可以自行執行該關聯，以控制哪個工作階段架構通道或呼叫與哪個 <xref:System.ServiceModel.InstanceContext> 物件關聯。 
  
## <a name="sessions-and-streaming"></a>工作階段和資料流  
 您有大量的資料傳輸，在 WCF 中的資料流傳輸模式時，緩衝處理與在完整的記憶體內處理訊息的預設行為是可行替代方案。 使用工作階段架構繫結對呼叫進行資料流處理時，可能會遇到未預期的行為。 即使使用的繫結已設定為使用工作階段，所有資料流處理呼叫還是會透過不支援工作階段的單一通道 (資料包通道) 來進行。 如果多個用戶端透過工作階段架構繫結對同一個服務物件進行資料流處理呼叫，而且服務物件的並行模式已設為單一且其執行個體內容模式已設為 `PerSession`，則所有呼叫必須經過資料包通道，所以一次只能處理一個呼叫。 一或多個用戶端可能會因此逾時。您可以將服務物件的 `InstanceContextMode` 設為 `PerCall` 或是將並行模式設為多重來解決這個問題。  
  
> [!NOTE]
>  此時 MaxConcurrentSessions 沒有作用，因為只有一個可用的「工作階段」。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
