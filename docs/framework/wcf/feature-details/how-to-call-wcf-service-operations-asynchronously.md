---
title: HOW TO：以非同步方式呼叫 WCF 服務作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 2815757bf9b00375f763673f18180bfbf51a165a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317438"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="4809a-102">HOW TO：以非同步方式呼叫 WCF 服務作業</span><span class="sxs-lookup"><span data-stu-id="4809a-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="4809a-103">本主題涵蓋用戶端如何能夠非同步地存取服務作業。</span><span class="sxs-lookup"><span data-stu-id="4809a-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="4809a-104">本主題中的服務會實作 `ICalculator` 介面。</span><span class="sxs-lookup"><span data-stu-id="4809a-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="4809a-105">用戶端可以透過使用事件驅動的非同步呼叫模型，以非同步方式在這個介面上呼叫作業。</span><span class="sxs-lookup"><span data-stu-id="4809a-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="4809a-106">(如需事件架構非同步呼叫模型的詳細資訊，請參閱[使用 「 事件架構非同步模式的多執行緒程式設計](https://go.microsoft.com/fwlink/?LinkId=248184))。</span><span class="sxs-lookup"><span data-stu-id="4809a-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="4809a-107">如需示範如何在服務中以非同步方式實作作業的範例，請參閱[How to:實作非同步服務作業](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="4809a-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="4809a-108">如需有關同步和非同步作業的詳細資訊，請參閱 <<c0> [ 同步和非同步作業](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="4809a-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4809a-109">當使用 <xref:System.ServiceModel.ChannelFactory%601> 時，不支援事件驅動非同步呼叫模型。</span><span class="sxs-lookup"><span data-stu-id="4809a-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="4809a-110">如需進行非同步呼叫使用<xref:System.ServiceModel.ChannelFactory%601>，請參閱[How to:呼叫作業以非同步方式使用通道處理站](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)。</span><span class="sxs-lookup"><span data-stu-id="4809a-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="4809a-111">程序</span><span class="sxs-lookup"><span data-stu-id="4809a-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="4809a-112">若要以非同步方式呼叫 WCF 服務作業</span><span class="sxs-lookup"><span data-stu-id="4809a-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="4809a-113">執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具，同時`/async`而`/tcv:Version35`一起命令選項，如下列命令所示。</span><span class="sxs-lookup"><span data-stu-id="4809a-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="4809a-114">這會產生，除了同步作業和標準委派架構非同步作業，WCF 用戶端類別，其中包含：</span><span class="sxs-lookup"><span data-stu-id="4809a-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    -   <span data-ttu-id="4809a-115">兩個 <`operationName` > `Async`與事件架構非同步呼叫方法搭配使用的作業。</span><span class="sxs-lookup"><span data-stu-id="4809a-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="4809a-116">例如：</span><span class="sxs-lookup"><span data-stu-id="4809a-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   <span data-ttu-id="4809a-117">作業已完成事件表單的 <`operationName` > `Completed`與事件架構非同步呼叫方法搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4809a-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="4809a-118">例如：</span><span class="sxs-lookup"><span data-stu-id="4809a-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <span data-ttu-id="4809a-119"><xref:System.EventArgs?displayProperty=nameWithType> 每個作業的類型 (表單的 <`operationName`>`CompletedEventArgs`) 與事件架構非同步呼叫方法搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4809a-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="4809a-120">例如: </span><span class="sxs-lookup"><span data-stu-id="4809a-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="4809a-121">在呼叫應用程式中，建立要在非同步作業完成時呼叫的回呼方法，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4809a-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="4809a-122">在呼叫作業之前, 使用 新的泛型<xref:System.EventHandler%601?displayProperty=nameWithType>類型的 <`operationName` > `EventArgs`將處理常式方法 （在上一個步驟中所建立的） 新增至 <`operationName` > `Completed`事件。</span><span class="sxs-lookup"><span data-stu-id="4809a-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="4809a-123">然後呼叫 <`operationName` > `Async`方法。</span><span class="sxs-lookup"><span data-stu-id="4809a-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="4809a-124">例如：</span><span class="sxs-lookup"><span data-stu-id="4809a-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="4809a-125">範例</span><span class="sxs-lookup"><span data-stu-id="4809a-125">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4809a-126">事件架構非同步模型的設計方針指出，如果傳回多個值，則其中一個值會傳回做為 `Result` 屬性，其他值則傳回做為 <xref:System.EventArgs> 物件上的屬性。</span><span class="sxs-lookup"><span data-stu-id="4809a-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="4809a-127">這樣做的結果就是，如果用戶端使用事件架構非同步命令選項匯入中繼資料，且作業傳回多個值，則預設 <xref:System.EventArgs> 物件會傳回一個值做為 `Result` 屬性，而其餘則做為 <xref:System.EventArgs> 物件的屬性。如果您要接收訊息物件做為 `Result` 屬性，並讓傳回值做為該物件的屬性，請使用 `/messageContract` 命令選項。</span><span class="sxs-lookup"><span data-stu-id="4809a-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="4809a-128">這會產生一個簽章，此簽章會將回應訊息傳回做為 `Result` 物件的 <xref:System.EventArgs> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4809a-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="4809a-129">然後，所有的內部傳回值都成為回應訊息物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="4809a-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4809a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4809a-130">See also</span></span>

- [<span data-ttu-id="4809a-131">如何：實作非同步服務作業</span><span class="sxs-lookup"><span data-stu-id="4809a-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
