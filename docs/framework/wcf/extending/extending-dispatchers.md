---
title: 擴充發送器
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: ac20e24eb9148ed9d403b7a9c2c260009f39d492
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335026"
---
# <a name="extending-dispatchers"></a>擴充發送器
發送器負責從基礎通道提取傳入訊息，將訊息轉譯成應用程式程式碼中的方法叫用，然後將結果傳回給呼叫者。 發送器擴充可讓您修改這個處理。  您可以實作可檢查或修改訊息或參數之內容的訊息或參數偵測器。  您可以變更訊息路由傳送到作業的方式，或提供其他特定功能。  
  
 本主題描述如何使用<xref:System.ServiceModel.Dispatcher.DispatchRuntime>和<xref:System.ServiceModel.Dispatcher.DispatchOperation>類別中的 Windows Communication Foundation (WCF) 服務來修改發送器的預設執行行為，或是攔截或修改訊息、 參數或傳回的應用程式之前或之後傳送，或從通道層擷取這些值。 如需有關對等用戶端執行階段訊息處理的詳細資訊，請參閱[擴充用戶端](../../../../docs/framework/wcf/extending/extending-clients.md)。 若要了解角色，<xref:System.ServiceModel.IExtensibleObject%601>型別中存取各種執行階段自訂物件之間的共用的狀態播放，請參閱 <<c2> [ 可擴充物件](../../../../docs/framework/wcf/extending/extensible-objects.md)。  
  
## <a name="dispatchers"></a>發送器  
 服務模型層會在開發人員的程式設計模型與一般稱為通道層的基礎訊息交換之間執行轉換。 在 WCF 通道和端點調派程式 (<xref:System.ServiceModel.Dispatcher.ChannelDispatcher>和<xref:System.ServiceModel.Dispatcher.EndpointDispatcher>分別) 是負責接受新通道、 接收訊息、 作業分派和叫用，以及回應處理的服務元件。 發送器物件是指接收物件，但是雙工服務中的回呼合約實作也會公開其發送器物件，以進行檢查、修改或擴充。  
  
 通道發送器和隨附的 <xref:System.ServiceModel.Channels.IChannelListener> 會從基礎通道中提取訊息，並將訊息傳遞至個別的端點發送器。 每個端點發送器都有一個 <xref:System.ServiceModel.Dispatcher.DispatchRuntime>，可將訊息傳送至適當的 <xref:System.ServiceModel.Dispatcher.DispatchOperation> (負責呼叫可實作作業的方法)。 過程中需要各種選擇性及必要的延伸類別。 本主題說明這些部分如何互相配合，以及如何修改屬性並插入您自己的程式碼以擴充基礎功能。  
  
 發送器屬性與修改的自訂物件可透過服務、端點、合約，或作業行為物件來插入。 本主題未說明這些行為的用法。 如需用來插入發送器修改的類型的詳細資訊，請參閱[設定和擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  
  
 下圖提供服務中架構項目的高階檢視。  
  
 ![分派執行階段架構](../../../../docs/framework/wcf/extending/media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")  
  
### <a name="channel-dispatchers"></a>通道發送器  
 <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> 物件是建立用來將服務執行個體與位於特定 URI (稱為接聽 URI) 的 <xref:System.ServiceModel.Channels.IChannelListener> 產生關聯。 每個 <xref:System.ServiceModel.ServiceHost> 物件都可以擁有許多 <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> 物件，而其中每一個物件只會與一個接聽項和接聽 URI 產生關聯。 當訊息抵達時，<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> 會查詢每個關聯的 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 物件來判定該端點是否可以接受此訊息，然後將該訊息傳遞至可以接受的端點。  
  
 所有控制通道工作階段之存留期及行為的屬性都可以用來檢查或修改 <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> 物件， 這些屬性包括自訂通道初始設定式、通道接聽項、主機與關聯的 <xref:System.ServiceModel.InstanceContext> 等等。  
  
### <a name="endpoint-dispatchers"></a>端點發送器  
 當訊息的目的端位址符合 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>，而且訊息動作符合 <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> 屬性時，<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> 物件就會負責處理來自 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> 的訊息。 如果有兩個 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 物件可以接受訊息，<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> 屬性值會決定使用較高優先順序的端點。  
  
 使用 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 即可取得兩個主要的服務模型擴充點 (<xref:System.ServiceModel.Dispatcher.DispatchRuntime> 和 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別)，以便您用來自訂發送器的處理。 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別可讓使用者在合約範圍內 (亦即針對合約內的所有訊息) 攔截與擴充發送器， <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別則可讓使用者在作業範圍內 (亦即針對作業內的所有訊息) 攔截與擴充發送器。  
  
## <a name="scenarios"></a>案例  
 發送器會因為下列某些原因而需要擴充：  
  
-   自訂訊息驗證。 使用者可以強制訊息對特定結構描述有效， 實作訊息攔截器介面即可達到這個目的。 如需範例，請參閱[訊息偵測器](../../../../docs/framework/wcf/samples/message-inspectors.md)。  
  
-   自訂訊息記錄。 使用者可以檢查和記錄某個流經端點的應用程式訊息集合， 使用訊息攔截器介面也可以完成這個動作。  
  
-   自訂訊息轉換。 使用者可以將特定轉換套用至執行階段中的訊息 (例如用來進行版本控制)， 使用訊息攔截器介面同樣可以完成這個動作。  
  
-   自訂資料模型。 使用者可以擁有以外 WCF 中的預設支援的資料序列化模型 (亦即<xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>， <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>，和未經處理的訊息)。 實作訊息格式器介面即可達到這個目的。 如需範例，請參閱[作業格式器和作業選取器](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md)。  
  
-   自訂參數驗證。 使用者可以強制型別參數都是有效的參數 (相對於 XML)， 使用參數偵測器介面即可達到這個目的。  
  
-   自訂作業分派。 使用者可以針對動作以外的項目 (例如主體項目或自訂訊息屬性) 實作分派， 使用 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 介面即可達到這個目的。 如需範例，請參閱[作業格式器和作業選取器](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md)。  
  
-   物件共用。 使用者可以共用執行個體，而不為每個呼叫分配一個新的執行個體， 使用執行個體提供者介面即可實作這個動作。 如需範例，請參閱[共用](../../../../docs/framework/wcf/samples/pooling.md)。  
  
-   執行個體租用。 使用者可以實作執行個體存留期的租用模式，方法與實作 .NET Framework 遠端處理的租用模式類似。 使用執行個體內容存留期介面即可達到這個目的。  
  
-   自訂錯誤處理。 使用者可以控制如何同時處理本機錯誤，以及如何將錯誤傳回用戶端。 使用 <xref:System.ServiceModel.Dispatcher.IErrorHandler> 介面即可實作這個動作。  
  
-   自訂授權行為。 使用者可以擴充「合約」或「作業」執行階段片段，並根據訊息中存在的權杖新增安全性檢查，以實作自訂存取控制。 使用訊息攔截器或參數攔截器介面即可達到這個目的。 如需範例，請參閱[安全性擴充性](../../../../docs/framework/wcf/samples/security-extensibility.md)。  
  
    > [!CAUTION]
    >  由於改變安全性屬性有可能會危及安全性的 WCF 應用程式，因此強烈建議您進行有關安全性的修改，請小心，並在部署之前徹底測試。  
  
-   自訂 WCF 執行階段驗證器。 您可以安裝自訂的驗證程式檢查服務、 合約和繫結，來強制執行 WCF 應用程式相關的企業層級原則。 (例如，請參閱[How to:鎖定在企業中的端點](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)。)  
  
### <a name="using-the-dispatchruntime-class"></a>使用 DispatchRuntime 類別  
 使用 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別即可修改服務或個別端點的預設行為，或是將實作自訂修改的物件插入下列其中一個或所有服務處理序 (或雙工用戶端情況下的用戶端處理序)：  
  
-   將傳入訊息轉換成物件，並且在針對服務物件叫用方法時釋放這些物件。  
  
-   將回應叫用服務作業時收到的物件轉換成傳出訊息。  
  
 即使無法辨識訊息，<xref:System.ServiceModel.Dispatcher.DispatchRuntime> 仍可讓您為特定合約上的所有訊息攔截及擴充通道或端點發送器。 當抵達的訊息不符合在合約中宣告的任何訊息時，該訊息會被分派至由 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> 屬性傳回的作業。 若要針對特定作業在所有訊息上進行攔截或擴充，請參閱 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別。  
  
 發送器擴充性的四個主要區域是由 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別所公開：  
  
1. 通道元件會使用 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 的屬性以及由 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> 屬性傳回之相關通道發送器的屬性，以自訂通道發送器如何接受及關閉通道。 這個分類包括 <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> 和 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> 屬性。  
  
2. 訊息元件會針對所處理的各個訊息進行自訂。 這個分類包括 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>、<xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>、<xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> 和 <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> 屬性。  
  
3. 執行個體元件會自訂服務類型執行個體的建立、存留期和處置。 如需服務物件存留期的詳細資訊，請參閱 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性。 這個分類包括 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> 和 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 屬性。  
  
4. 安全性相關的元件可以使用下列屬性：  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A> 表示稽核事件會寫入其中。  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A> 控制服務是否會嘗試模擬使用內送訊息所提供的認證。  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A> 控制是否成功的訊息驗證事件寫入事件記錄檔所指定<xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>。  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A> 控制項如何<xref:System.Threading.Thread.CurrentPrincipal%2A>屬性設定。  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A> 指定如何執行授權事件的稽核。  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A> 指定是否要隱藏在記錄處理期間發生的非嚴重例外狀況。  
  
 一般來說，自訂延伸物件會指派給 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 屬性，或由服務行為 (實作 <xref:System.ServiceModel.Description.IServiceBehavior> 的物件)、合約行為 (實作 <xref:System.ServiceModel.Description.IContractBehavior> 的物件) 或端點行為 (實作 <xref:System.ServiceModel.Description.IEndpointBehavior> 的物件) 插入集合中。 接著，安裝行為物件會透過程式設計的方式或實作自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 物件的方式新增至適當的行為集合，讓該行為可以透過應用程式組態檔插入。  
  
 雙工用戶端 (實作由雙工服務指定之回呼合約的用戶端) 也有一個 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 物件，您可以使用 <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> 屬性來存取該物件。  
  
### <a name="using-the-dispatchoperation-class"></a>使用 DispatchOperation 類別  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別是進行執行階段修改的位置，以及範圍僅限一項服務作業之自訂延伸的插入點。 若要修改合約中所有訊息的服務執行階段行為，請使用 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別。  
  
 使用自訂服務行為物件即可安裝 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 修改。  
  
 您可以使用 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> 屬性找出表示特定服務作業的 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 物件。  
  
 下列屬性控制作業層級的執行階段執行：  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>、<xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>、<xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A>、<xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>、<xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A> 和 <xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> 屬性會各自取得該作業的值。  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> 和 <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> 會指定異動行為。  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> 和 <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> 屬性會控制與 <xref:System.ServiceModel.InstanceContext> 相關之使用者定義服務物件的存留期。  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>、<xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A> 和 <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> 屬性可以用來明確控制訊息與物件之間的相互轉換。  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> 屬性會指定作業模擬層級。  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> 屬性會插入作業的自訂呼叫內容延伸。  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> 屬性會控制何時要終結參數物件。  
  
-   要插入自訂 Invoker 物件的 <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> 屬性。  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> 屬性可以讓您插入可用來檢查或修改參數和傳回值的自訂參數偵測器。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Dispatcher.DispatchRuntime>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation>
- [HOW TO：檢查及修改服務中的訊息](../../../../docs/framework/wcf/extending/how-to-inspect-and-modify-messages-on-the-service.md)
- [HOW TO：檢查或修改參數](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
- [HOW TO：鎖定企業的端點](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)
