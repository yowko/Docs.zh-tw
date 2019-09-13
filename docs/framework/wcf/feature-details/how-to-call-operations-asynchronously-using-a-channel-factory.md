---
title: 作法：使用通道處理站以非同步方式呼叫作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: adc4d519e8d29fef5595ab7ddc3168462525c4e2
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895241"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="e2ac4-102">作法：使用通道處理站以非同步方式呼叫作業</span><span class="sxs-lookup"><span data-stu-id="e2ac4-102">How to: Call Operations Asynchronously Using a Channel Factory</span></span>
<span data-ttu-id="e2ac4-103">本主題涵蓋用戶端如何能夠在使用 <xref:System.ServiceModel.ChannelFactory%601> 架構的用戶端應用程式時，非同步地存取服務作業</span><span class="sxs-lookup"><span data-stu-id="e2ac4-103">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="e2ac4-104">(當使用 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> 物件來叫用服務時，您可以使用事件驅動的非同步呼叫模型。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-104">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="e2ac4-105">如需詳細資訊，請參閱[如何：以非同步方式](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-105">For more information, see [How to: Call Service Operations Asynchronously](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="e2ac4-106">如需事件架構非同步呼叫模型的詳細資訊，請參閱以[事件為基礎的非同步模式（EAP）](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。）</span><span class="sxs-lookup"><span data-stu-id="e2ac4-106">For more information about the event-based asynchronous calling model, see [Event-based Asynchronous Pattern (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)</span></span>  
  
 <span data-ttu-id="e2ac4-107">本主題中的服務會實作 `ICalculator` 介面。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-107">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="e2ac4-108">用戶端可透過非同步的方式來呼叫在此介面上的作業，這表示類似 `Add` 的作業會分割為兩個方法，`BeginAdd` 和 `EndAdd`，其中前者會啟始呼叫，後者則會在作業完成時擷取結果。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-108">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="e2ac4-109">如需示範如何在服務中以非同步方式執行作業的範例， [請參閱如何：執行非同步服務](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)作業。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-109">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="e2ac4-110">如需同步和非同步作業的詳細資訊，請參閱[同步和非同步作業](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-110">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="e2ac4-111">程序</span><span class="sxs-lookup"><span data-stu-id="e2ac4-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="e2ac4-112">若要以非同步方式呼叫 WCF 服務作業</span><span class="sxs-lookup"><span data-stu-id="e2ac4-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="e2ac4-113">使用`/async`選項執行[system.servicemodel 中繼資料公用程式工具（Svcutil）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具，如下列命令所示。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="e2ac4-114">這會針對作業的服務合約產生非同步用戶端版本。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-114">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2. <span data-ttu-id="e2ac4-115">建立要在非同步作業完成時呼叫的回呼函式 (Callback Function)，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-115">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. <span data-ttu-id="e2ac4-116">若要以非同步方式來存取服務作業，請建立用戶端和呼叫 `Begin[Operation]` (例如，`BeginAdd`)，並指定回呼函式，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-116">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="e2ac4-117">當此回呼函式執行時，用戶端便會呼叫 `End<operation>` (例如，`EndAdd`) 以擷取結果。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-117">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2ac4-118">範例</span><span class="sxs-lookup"><span data-stu-id="e2ac4-118">Example</span></span>  
 <span data-ttu-id="e2ac4-119">在用於上述程序中之用戶端程式碼所使用的服務會實作 `ICalculator` 介面，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-119">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="e2ac4-120">在服務端，合約的`Add`和`Subtract`作業會由 Windows Communication Foundation （WCF）執行時間以同步方式叫用，即使在用戶端上以非同步方式叫用上述用戶端步驟也是一樣。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-120">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the Windows Communication Foundation (WCF) run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="e2ac4-121">在服務端，會使用 `Multiply` 和 `Divide` 作業來非同步叫用服務，即使用戶端會同步叫用這些服務也是一樣。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-121">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="e2ac4-122">這個範例會將 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-122">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="e2ac4-123">此屬性設定（結合 .NET Framework 非同步模式的執行）會告知執行時間以非同步方式叫用作業。</span><span class="sxs-lookup"><span data-stu-id="e2ac4-123">This property setting, in combination with the implementation of the .NET Framework asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
