---
title: 相互關聯概觀
ms.date: 03/30/2017
ms.assetid: edcc0315-5d26-44d6-a36d-ea554c418e9f
ms.openlocfilehash: 7128ff531bb81fb6de526092513d5525ca138735
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512771"
---
# <a name="correlation-overview"></a>相互關聯概觀
相互關聯是一種機制，可將工作流程服務訊息彼此產生關聯性、將工作流程服務訊息與應用程式執行個體狀態 (例如針對初始要求的回覆) 產生關聯性，或者是將特定的訂單 ID 與訂單處理工作流程的保存狀態產生關聯性。 本主題提供相互關聯的概觀。 本節的其他主題則會提供各種相互關聯類型的其他資訊。  
  
## <a name="types-of-correlation"></a>相互關聯的類型  
 相互關聯可以以通訊協定為主或以內容為主。 以通訊協定為主的相互關聯會使用訊息傳遞基礎結構提供的資料，提供訊息之間的對應。 利用以通訊協定為主之相互關聯功能彼此產生關聯性的訊息，會使用記憶體中的物件 (例如 <xref:System.ServiceModel.Channels.RequestContext>)，或者使用傳輸通訊協定提供的權杖彼此相互關聯。 以內容為基礎的相互關聯則會利用指定應用程式的資料產生訊息與訊息之間的關聯性。 利用以內容為主之相互關聯功能彼此產生關聯性的訊息，是透過訊息中某些應用程式定義的資料 (如客戶編號) 而彼此產生關聯性的。  
  
 參與相互關聯的活動會使用 <xref:System.ServiceModel.Activities.CorrelationHandle> 將傳訊活動結合在一起。 例如，用於呼叫服務的 <xref:System.ServiceModel.Activities.Send>，以及後續用於接收服務所傳回之回呼的 <xref:System.ServiceModel.Activities.Receive>，兩者會共用相同的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 無論是以通訊協定為主或以內容為主的相互關聯，都會採用這個基本模式。 相互關聯控制代碼可在每個活動明確設定，或者可將所有活動包含在一個 <xref:System.ServiceModel.Activities.CorrelationScope> 活動中。 包含在 <xref:System.ServiceModel.Activities.CorrelationScope> 中的活動會將其相互關聯控制代碼交由 <xref:System.ServiceModel.Activities.CorrelationScope> 管理，而不需明確設定 <xref:System.ServiceModel.Activities.CorrelationHandle>。 <xref:System.ServiceModel.Activities.CorrelationScope> 範圍針對要求-回覆相互關聯及一個其他相互關聯類型提供 <xref:System.ServiceModel.Activities.CorrelationHandle> 管理。 使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載的工作流程服務與 <xref:System.ServiceModel.Activities.CorrelationScope> 活動具有相同的預設相互關聯管理。 這個預設相互關聯管理功能通常表示在許多情況下，<xref:System.ServiceModel.Activities.CorrelationScope> 或工作流程服務中的傳訊活動不需設定其 <xref:System.ServiceModel.Activities.CorrelationHandle>，除非有多個傳訊活動平行或重疊，例如兩個 <xref:System.ServiceModel.Activities.Receive> 活動平行，或者兩個 <xref:System.ServiceModel.Activities.Send> 活動之後緊接著兩個 <xref:System.ServiceModel.Activities.Receive> 活動。 本節中的主題提供更多關於預設相互關聯的資訊，其中包含相互關聯的每種特定類型。 如需訊息活動的詳細資訊請參閱[訊息活動](../../../../docs/framework/wcf/feature-details/messaging-activities.md)和[How to:使用訊息活動建立工作流程服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)。  
  
## <a name="protocol-based-correlation"></a>以通訊協定為主的相互關聯

以通訊協定為主的相互關聯會使用傳輸機制將訊息彼此產生關聯性，以及將訊息與適當的執行個體產生關聯性。 某些由系統提供的通訊協定相互關聯會包含要求-回覆相互關聯，以及以內容為主的相互關聯。 要求-回覆相互關聯用於將單獨一組的傳訊活動相互關聯，以形成雙向作業，例如 <xref:System.ServiceModel.Activities.Send> 搭配 <xref:System.ServiceModel.Activities.ReceiveReply>，或是 <xref:System.ServiceModel.Activities.Receive> 搭配 <xref:System.ServiceModel.Activities.SendReply>。 Visual Studio 工作流程設計工具也會提供一組活動範本，快速地實作此模式。 以內容為主的相互關聯以中所述的內容交換機制為基礎[.NET 內容交換通訊協定規格](https://go.microsoft.com/fwlink/?LinkID=166059)。 若要使用以內容為主的相互關聯，必須在端點上使用以內容為主的繫結，例如 <xref:System.ServiceModel.BasicHttpContextBinding>、<xref:System.ServiceModel.WSHttpContextBinding> 或 <xref:System.ServiceModel.NetTcpContextBinding>。  
  
如需有關通訊協定相互關聯的詳細資訊，請參閱[永久性雙工](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)並[要求-回覆](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)。 如需使用 Visual Studio 工作流程設計工具活動範本的詳細資訊，請參閱 <<c0> [ 訊息活動](../../../../docs/framework/wcf/feature-details/messaging-activities.md)。 範例程式碼，請參閱[NetContextExchangeCorrelation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee662963%28v%3dvs.100%29)範例。  
  
## <a name="content-based-correlation"></a>以內容為基礎的相互關聯

以內容為基礎的相互關聯會利用訊息中的部分資訊片段，將其與特定執行個體產生關聯。 不同於以通訊協定為主的相互關聯，以內容為主的相互關聯會要求應用程式作者明確陳述這項資料在每個相關訊息中的位置。 使用以內容為主的相互關聯的活動會使用 <xref:System.ServiceModel.MessageQuerySet> 來指定這項訊息資料。 與不使用其中一種內容繫結 (例如 <xref:System.ServiceModel.BasicHttpContextBinding>) 的服務通訊時，以內容為基礎的相互關聯非常有用。
  
## <a name="see-also"></a>另請參閱

- [NetContextExchangeCorrelation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee662963%28v%3dvs.100%29)
