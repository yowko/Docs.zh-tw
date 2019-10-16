---
title: Wcf 端點和 gRPC 方法-適用于 WCF 開發人員的 gRPC
description: 比較以 ServiceContract 和 OperationContract 屬性宣告的 WCF 端點，以及 Protobuf 中宣告的 gRPC 方法
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 08f2d0874417c0ca319b0c193e6108536376d693
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184061"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="01ff3-103">WCF 端點和 gRPC 方法</span><span class="sxs-lookup"><span data-stu-id="01ff3-103">WCF endpoints and gRPC methods</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="01ff3-104">在 WCF 中，當您撰寫應用程式程式碼時，您可以使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="01ff3-104">In WCF, when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="01ff3-105">您在類別中撰寫應用程式程式碼，並使用[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性來裝飾方法。</span><span class="sxs-lookup"><span data-stu-id="01ff3-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="01ff3-106">您可以宣告服務的介面，並將[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性新增至介面。</span><span class="sxs-lookup"><span data-stu-id="01ff3-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="01ff3-107">例如， `greet.proto` Greeter 服務的 WCF 對等項可能會寫入如下：</span><span class="sxs-lookup"><span data-stu-id="01ff3-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="01ff3-108">第3章顯示使用 Protobuf 訊息定義來產生資料類別。</span><span class="sxs-lookup"><span data-stu-id="01ff3-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="01ff3-109">服務和方法宣告是用來產生繼承自的基類，以執行服務。</span><span class="sxs-lookup"><span data-stu-id="01ff3-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="01ff3-110">您只要宣告要在檔案中`.proto`執行的方法，編譯器就會產生具有您必須覆寫之虛擬方法的基類。</span><span class="sxs-lookup"><span data-stu-id="01ff3-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="01ff3-111">OperationContract 屬性</span><span class="sxs-lookup"><span data-stu-id="01ff3-111">OperationContract properties</span></span>

<span data-ttu-id="01ff3-112">[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性具有屬性，可控制或精簡其運作方式。</span><span class="sxs-lookup"><span data-stu-id="01ff3-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="01ff3-113">gRPC 方法不提供這種類型的控制項。</span><span class="sxs-lookup"><span data-stu-id="01ff3-113">gRPC methods don’t offer this type of control.</span></span> <span data-ttu-id="01ff3-114">下表會設定這些`OperationContract`屬性，以及它們所指定的功能在 gRPC 中的處理方式（或不會）：</span><span class="sxs-lookup"><span data-stu-id="01ff3-114">The following table sets out those `OperationContract` properties and how the functionality they specify is (or isn’t) dealt with in gRPC:</span></span>

| <span data-ttu-id="01ff3-115">`OperationContract` 屬性</span><span class="sxs-lookup"><span data-stu-id="01ff3-115">`OperationContract` property</span></span> | <span data-ttu-id="01ff3-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="01ff3-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="01ff3-117">識別作業的 URI。</span><span class="sxs-lookup"><span data-stu-id="01ff3-117">URI identifying the operation.</span></span> <span data-ttu-id="01ff3-118">gRPC 會使用的`package`名稱， `service`以及`rpc`檔案中`.proto`的。</span><span class="sxs-lookup"><span data-stu-id="01ff3-118">gRPC uses the name of the `package`, `service` and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="01ff3-119">所有 gRPC 服務方法`Task`都會傳回物件。</span><span class="sxs-lookup"><span data-stu-id="01ff3-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="01ff3-120">請參閱下列注意事項。</span><span class="sxs-lookup"><span data-stu-id="01ff3-120">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="01ff3-121">單向 gRPC 方法`Empty`會傳回結果，或使用用戶端串流。</span><span class="sxs-lookup"><span data-stu-id="01ff3-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="01ff3-122">請參閱下列注意事項。</span><span class="sxs-lookup"><span data-stu-id="01ff3-122">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="01ff3-123">SOAP 相關，在 gRPC 中沒有意義。</span><span class="sxs-lookup"><span data-stu-id="01ff3-123">SOAP-related, no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="01ff3-124">無訊息加密;在傳輸層處理的網路加密（TLS over HTTP/2）。</span><span class="sxs-lookup"><span data-stu-id="01ff3-124">No message encryption; network encryption handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="01ff3-125">SOAP 相關，在 gRPC 中沒有意義。</span><span class="sxs-lookup"><span data-stu-id="01ff3-125">SOAP-related, no meaning in gRPC.</span></span> |

<span data-ttu-id="01ff3-126">屬性可讓您指出 [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) 中的方法不能是第一個呼叫作為會話一部分的方法。`IsInitiating`</span><span class="sxs-lookup"><span data-stu-id="01ff3-126">The `IsInitiating` property lets you indicate that a method within a [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="01ff3-127">`IsTerminating`屬性會在呼叫作業之後，讓伺服器關閉會話（如果是在回呼用戶端上使用，則會導致用戶端）。</span><span class="sxs-lookup"><span data-stu-id="01ff3-127">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if used on a callback client).</span></span> <span data-ttu-id="01ff3-128">在 gRPC 中，資料流程是由單一方法建立，並且明確地關閉。</span><span class="sxs-lookup"><span data-stu-id="01ff3-128">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="01ff3-129">請參閱[gRPC 串流](rpc-types.md#grpc-streaming)。</span><span class="sxs-lookup"><span data-stu-id="01ff3-129">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="01ff3-130">如需有關 gRPC 安全性和加密的詳細資訊，請參閱[第6章](security.md)。</span><span class="sxs-lookup"><span data-stu-id="01ff3-130">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="01ff3-131">[上一頁](wcf-services-to-grpc-comparison.md)
>[下一頁](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="01ff3-131">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
