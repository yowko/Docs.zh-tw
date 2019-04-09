---
title: HOW TO：實作非同步服務作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: ec1c6549c4a386f529ca2191e1876975b2bf5dcd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186845"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="f5328-102">HOW TO：實作非同步服務作業</span><span class="sxs-lookup"><span data-stu-id="f5328-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="f5328-103">在 Windows Communication Foundation (WCF) 應用程式中，實作服務作業可以非同步或同步不需規定用戶端如何呼叫它。</span><span class="sxs-lookup"><span data-stu-id="f5328-103">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="f5328-104">比方說，可以呼叫非同步服務作業同步，並以非同步方式呼叫同步服務作業。</span><span class="sxs-lookup"><span data-stu-id="f5328-104">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="f5328-105">如需示範如何在用戶端應用程式中以非同步方式呼叫作業的範例，請參閱[How to:以非同步方式呼叫服務作業](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="f5328-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="f5328-106">如需有關同步和非同步作業的詳細資訊，請參閱 < [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md)並[同步和非同步作業](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="f5328-106">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) and [Synchronous and Asynchronous Operations](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="f5328-107">本主題描述非同步服務作業的基本結構，程式碼尚未完成。</span><span class="sxs-lookup"><span data-stu-id="f5328-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="f5328-108">服務和用戶端的側邊的完整範例，請參閱 <<c0> [ 非同步](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="f5328-108">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="f5328-109">以非同步方式實作服務作業</span><span class="sxs-lookup"><span data-stu-id="f5328-109">Implement a service operation asynchronously</span></span>  
  
1.  <span data-ttu-id="f5328-110">在您的服務合約中，根據 .NET 非同步設計方針宣告一個非同步方法組。</span><span class="sxs-lookup"><span data-stu-id="f5328-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="f5328-111">`Begin` 方法可接受一個參數、回呼物件和狀態物件，並傳回 <xref:System.IAsyncResult?displayProperty=nameWithType> 和對應的 `End` 方法，該方法會接受 <xref:System.IAsyncResult?displayProperty=nameWithType> 並傳回其傳回值。</span><span class="sxs-lookup"><span data-stu-id="f5328-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="f5328-112">如需有關非同步呼叫的詳細資訊，請參閱[非同步程式設計模式](https://go.microsoft.com/fwlink/?LinkId=248221)。</span><span class="sxs-lookup"><span data-stu-id="f5328-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](https://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2.  <span data-ttu-id="f5328-113">使用 `Begin` 屬性 (Attribute) 來標記非同步方法組中的 <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> 方法，並將 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> 屬性 (Property) 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f5328-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="f5328-114">例如，下列程式碼會執行步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="f5328-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  <span data-ttu-id="f5328-115">根據非同步設計方針，在您的服務類別內實作 `Begin/End` 方法組。</span><span class="sxs-lookup"><span data-stu-id="f5328-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="f5328-116">例如，下列程式碼範例會顯示利用非同步服務作業的 `Begin` 和 `End` 兩個部分，將字串寫入主控台的實作，以及傳回用戶端之 `End` 作業的傳回值。</span><span class="sxs-lookup"><span data-stu-id="f5328-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="f5328-117">如需完整的程式碼範例，請參閱＜範例＞一節。</span><span class="sxs-lookup"><span data-stu-id="f5328-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="f5328-118">範例</span><span class="sxs-lookup"><span data-stu-id="f5328-118">Example</span></span>  
 <span data-ttu-id="f5328-119">下列程式碼範例會顯示：</span><span class="sxs-lookup"><span data-stu-id="f5328-119">The following code examples show:</span></span>  
  
1.  <span data-ttu-id="f5328-120">服務合約介面，其中具有：</span><span class="sxs-lookup"><span data-stu-id="f5328-120">A service contract interface with:</span></span>  
  
    1.  <span data-ttu-id="f5328-121">一個同步 `SampleMethod` 作業。</span><span class="sxs-lookup"><span data-stu-id="f5328-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2.  <span data-ttu-id="f5328-122">一個非同步 `BeginSampleMethod` 作業。</span><span class="sxs-lookup"><span data-stu-id="f5328-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3.  <span data-ttu-id="f5328-123">非同步`BeginServiceAsyncMethod` / `EndServiceAsyncMethod`作業組。</span><span class="sxs-lookup"><span data-stu-id="f5328-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2.  <span data-ttu-id="f5328-124">一個使用 <xref:System.IAsyncResult?displayProperty=nameWithType> 物件的服務實作。</span><span class="sxs-lookup"><span data-stu-id="f5328-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f5328-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5328-125">See also</span></span>

- [<span data-ttu-id="f5328-126">設計服務合約</span><span class="sxs-lookup"><span data-stu-id="f5328-126">Designing Service Contracts</span></span>](../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="f5328-127">同步和非同步作業</span><span class="sxs-lookup"><span data-stu-id="f5328-127">Synchronous and Asynchronous Operations</span></span>](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
