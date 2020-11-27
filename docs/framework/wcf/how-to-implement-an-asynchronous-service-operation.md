---
title: 作法：實作非同步服務作業
description: 瞭解 WFC 中非同步服務作業的結構。 服務作業可以透過非同步或同步方式來執行。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 157311f29b203e0c26be21a89d2d5b560543094b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267828"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="6b994-104">作法：實作非同步服務作業</span><span class="sxs-lookup"><span data-stu-id="6b994-104">How to: Implement an Asynchronous Service Operation</span></span>

<span data-ttu-id="6b994-105">在 Windows Communication Foundation (WCF) 應用程式中，服務作業可以透過非同步或同步方式執行，而不需要向用戶端要求如何呼叫它。</span><span class="sxs-lookup"><span data-stu-id="6b994-105">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="6b994-106">例如，非同步服務作業可以同步呼叫，同步服務作業則可以非同步方式呼叫。</span><span class="sxs-lookup"><span data-stu-id="6b994-106">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="6b994-107">如需示範如何在用戶端應用程式中以非同步方式呼叫作業的範例，請參閱 [如何：以非同步方式呼叫服務作業](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="6b994-107">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="6b994-108">如需同步和非同步作業的詳細資訊，請參閱 [設計服務合約](designing-service-contracts.md) 和 [同步和非同步作業](synchronous-and-asynchronous-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="6b994-108">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="6b994-109">本主題描述非同步服務作業的基本結構，程式碼尚未完成。</span><span class="sxs-lookup"><span data-stu-id="6b994-109">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="6b994-110">如需服務和用戶端的完整範例，請參閱 [非同步](/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="6b994-110">For a complete example of both the service and client sides, see [Asynchronous](/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="6b994-111">以非同步方式實作服務作業</span><span class="sxs-lookup"><span data-stu-id="6b994-111">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="6b994-112">在您的服務合約中，根據 .NET 非同步設計方針宣告一個非同步方法組。</span><span class="sxs-lookup"><span data-stu-id="6b994-112">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="6b994-113">`Begin` 方法可接受一個參數、回呼物件和狀態物件，並傳回 <xref:System.IAsyncResult?displayProperty=nameWithType> 和對應的 `End` 方法，該方法會接受 <xref:System.IAsyncResult?displayProperty=nameWithType> 並傳回其傳回值。</span><span class="sxs-lookup"><span data-stu-id="6b994-113">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="6b994-114">如需非同步呼叫的詳細資訊，請參閱 [非同步程式設計模式](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。</span><span class="sxs-lookup"><span data-stu-id="6b994-114">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
2. <span data-ttu-id="6b994-115">使用 `Begin` 屬性 (Attribute) 來標記非同步方法組中的 <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> 方法，並將 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> 屬性 (Property) 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6b994-115">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="6b994-116">例如，下列程式碼會執行步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="6b994-116">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="6b994-117">根據非同步設計方針，在您的服務類別內實作 `Begin/End` 方法組。</span><span class="sxs-lookup"><span data-stu-id="6b994-117">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="6b994-118">例如，下列程式碼範例會顯示利用非同步服務作業的 `Begin` 和 `End` 兩個部分，將字串寫入主控台的實作，以及傳回用戶端之 `End` 作業的傳回值。</span><span class="sxs-lookup"><span data-stu-id="6b994-118">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="6b994-119">如需完整的程式碼範例，請參閱＜範例＞一節。</span><span class="sxs-lookup"><span data-stu-id="6b994-119">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="6b994-120">範例</span><span class="sxs-lookup"><span data-stu-id="6b994-120">Example</span></span>  

 <span data-ttu-id="6b994-121">下列程式碼範例會顯示：</span><span class="sxs-lookup"><span data-stu-id="6b994-121">The following code examples show:</span></span>  
  
1. <span data-ttu-id="6b994-122">服務合約介面，其中具有：</span><span class="sxs-lookup"><span data-stu-id="6b994-122">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="6b994-123">一個同步 `SampleMethod` 作業。</span><span class="sxs-lookup"><span data-stu-id="6b994-123">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="6b994-124">一個非同步 `BeginSampleMethod` 作業。</span><span class="sxs-lookup"><span data-stu-id="6b994-124">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="6b994-125">非同步 `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` 操作配對。</span><span class="sxs-lookup"><span data-stu-id="6b994-125">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="6b994-126">一個使用 <xref:System.IAsyncResult?displayProperty=nameWithType> 物件的服務實作。</span><span class="sxs-lookup"><span data-stu-id="6b994-126">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6b994-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b994-127">See also</span></span>

- [<span data-ttu-id="6b994-128">設計服務合約</span><span class="sxs-lookup"><span data-stu-id="6b994-128">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="6b994-129">同步和非同步作業</span><span class="sxs-lookup"><span data-stu-id="6b994-129">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
