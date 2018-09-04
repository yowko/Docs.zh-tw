---
title: HOW TO：使用通道處理站以非同步方式呼叫作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: a45ba48408fd98c89db8664aec679a437ce8af24
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559917"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="8ad48-102">HOW TO：使用通道處理站以非同步方式呼叫作業</span><span class="sxs-lookup"><span data-stu-id="8ad48-102">How to: Call Operations Asynchronously Using a Channel Factory</span></span>
<span data-ttu-id="8ad48-103">本主題涵蓋用戶端如何能夠在使用 <xref:System.ServiceModel.ChannelFactory%601> 架構的用戶端應用程式時，非同步地存取服務作業 </span><span class="sxs-lookup"><span data-stu-id="8ad48-103">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="8ad48-104">(當使用 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> 物件來叫用服務時，您可以使用事件驅動的非同步呼叫模型。</span><span class="sxs-lookup"><span data-stu-id="8ad48-104">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="8ad48-105">如需詳細資訊，請參閱 <<c0> [ 如何： 非同步呼叫服務作業](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="8ad48-105">For more information, see [How to: Call Service Operations Asynchronously](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="8ad48-106">如需事件架構非同步呼叫模型的詳細資訊，請參閱[事件架構非同步模式 (EAP)](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。)</span><span class="sxs-lookup"><span data-stu-id="8ad48-106">For more information about the event-based asynchronous calling model, see [Event-based Asynchronous Pattern (EAP)](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)</span></span>  
  
 <span data-ttu-id="8ad48-107">本主題中的服務會實作 `ICalculator` 介面。</span><span class="sxs-lookup"><span data-stu-id="8ad48-107">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="8ad48-108">用戶端可透過非同步的方式來呼叫在此介面上的作業，這表示類似 `Add` 的作業會分割為兩個方法，`BeginAdd` 和 `EndAdd`，其中前者會啟始呼叫，後者則會在作業完成時擷取結果。</span><span class="sxs-lookup"><span data-stu-id="8ad48-108">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="8ad48-109">如需示範如何在服務中以非同步方式實作作業的範例，請參閱[如何： 實作非同步服務作業](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="8ad48-109">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="8ad48-110">如需同步與非同步作業的詳細資訊，請參閱[同步和非同步作業](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="8ad48-110">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="8ad48-111">程序</span><span class="sxs-lookup"><span data-stu-id="8ad48-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="8ad48-112">若要以非同步方式呼叫 WCF 服務作業</span><span class="sxs-lookup"><span data-stu-id="8ad48-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="8ad48-113">執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具搭配`/async`選項，如下列命令所示。</span><span class="sxs-lookup"><span data-stu-id="8ad48-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="8ad48-114">這會針對作業的服務合約產生非同步用戶端版本。</span><span class="sxs-lookup"><span data-stu-id="8ad48-114">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2.  <span data-ttu-id="8ad48-115">建立要在非同步作業完成時呼叫的回呼函式 (Callback Function)，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8ad48-115">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  <span data-ttu-id="8ad48-116">若要以非同步方式來存取服務作業，請建立用戶端和呼叫 `Begin[Operation]` (例如，`BeginAdd`)，並指定回呼函式，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8ad48-116">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="8ad48-117">當此回呼函式執行時，用戶端便會呼叫 `End<operation>` (例如，`EndAdd`) 以擷取結果。</span><span class="sxs-lookup"><span data-stu-id="8ad48-117">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ad48-118">範例</span><span class="sxs-lookup"><span data-stu-id="8ad48-118">Example</span></span>  
 <span data-ttu-id="8ad48-119">在用於上述程序中之用戶端程式碼所使用的服務會實作 `ICalculator` 介面，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8ad48-119">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="8ad48-120">在服務端，`Add`和`Subtract`合約作業的同時叫用由 Windows Communication Foundation (WCF) 執行階段，即使在用戶端上的 「 先前的用戶端步驟會叫用非同步。</span><span class="sxs-lookup"><span data-stu-id="8ad48-120">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the Windows Communication Foundation (WCF) run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="8ad48-121">在服務端，會使用 `Multiply` 和 `Divide` 作業來非同步叫用服務，即使用戶端會同步叫用這些服務也是一樣。</span><span class="sxs-lookup"><span data-stu-id="8ad48-121">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="8ad48-122">這個範例會將 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8ad48-122">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="8ad48-123">這項屬性設定在配合 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 非同步模式 (Asynchronous Pattern) 的實作時，便會告知執行階段以非同步方式來叫用作業。</span><span class="sxs-lookup"><span data-stu-id="8ad48-123">This property setting, in combination with the implementation of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8ad48-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ad48-124">See Also</span></span>  
 [<span data-ttu-id="8ad48-125">服務合約： 非同步範例</span><span class="sxs-lookup"><span data-stu-id="8ad48-125">Service Contract: Asynchronous Sample</span></span>](https://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7)
