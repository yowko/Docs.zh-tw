---
title: Wcf 端點和 gRPC 方法-適用于 WCF 開發人員的 gRPC
description: 比較以 ServiceContract 和 OperationContract 屬性宣告的 WCF 端點，以及 Protobuf 中宣告的 gRPC 方法
ms.date: 09/02/2019
ms.openlocfilehash: 1bc6ecbc73bfc0a58393e4c28672b897ed6f2f15
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503423"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="31055-103">WCF 端點和 gRPC 方法</span><span class="sxs-lookup"><span data-stu-id="31055-103">WCF endpoints and gRPC methods</span></span>

<span data-ttu-id="31055-104">在 Windows Communication Foundation （WCF）中，當您撰寫應用程式程式碼時，您可以使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="31055-104">In Windows Communication Foundation (WCF), when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="31055-105">您在類別中撰寫應用程式程式碼，並使用[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性來裝飾方法。</span><span class="sxs-lookup"><span data-stu-id="31055-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="31055-106">您可以宣告服務的介面，並將[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性新增至介面。</span><span class="sxs-lookup"><span data-stu-id="31055-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="31055-107">例如，`greet.proto` Greeter 服務的 WCF 對等項可能會寫入如下：</span><span class="sxs-lookup"><span data-stu-id="31055-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="31055-108">第3章顯示使用 Protobuf 訊息定義來產生資料類別。</span><span class="sxs-lookup"><span data-stu-id="31055-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="31055-109">服務和方法宣告是用來產生繼承自的基類，以執行服務。</span><span class="sxs-lookup"><span data-stu-id="31055-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="31055-110">您只要宣告要在 `.proto` 檔案中執行的方法，編譯器就會產生具有您必須覆寫之虛擬方法的基類。</span><span class="sxs-lookup"><span data-stu-id="31055-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods that you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="31055-111">OperationContract 屬性</span><span class="sxs-lookup"><span data-stu-id="31055-111">OperationContract properties</span></span>

<span data-ttu-id="31055-112">[OperationContract](xref:System.ServiceModel.OperationContractAttribute)屬性具有屬性，可控制或精簡其運作方式。</span><span class="sxs-lookup"><span data-stu-id="31055-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="31055-113">gRPC 方法不提供這種類型的控制項。</span><span class="sxs-lookup"><span data-stu-id="31055-113">gRPC methods don't offer this type of control.</span></span> <span data-ttu-id="31055-114">下表列出這些 `OperationContract` 屬性，並說明在 gRPC 中，它們所指定的功能是（或未）處理：</span><span class="sxs-lookup"><span data-stu-id="31055-114">The following table lists those `OperationContract` properties and describes how the functionality that they specify is (or isn't) dealt with in gRPC:</span></span>

| <span data-ttu-id="31055-115">`OperationContract` 屬性</span><span class="sxs-lookup"><span data-stu-id="31055-115">`OperationContract` property</span></span> | <span data-ttu-id="31055-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="31055-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="31055-117">URI 可識別作業。</span><span class="sxs-lookup"><span data-stu-id="31055-117">A URI identifies the operation.</span></span> <span data-ttu-id="31055-118">gRPC 會使用 `.proto` 檔案中 `package`、`service`和 `rpc` 的名稱。</span><span class="sxs-lookup"><span data-stu-id="31055-118">gRPC uses the name of `package`, `service`, and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="31055-119">所有的 gRPC 服務方法都會傳回 `Task` 物件。</span><span class="sxs-lookup"><span data-stu-id="31055-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="31055-120">請參閱此表格後面的段落。</span><span class="sxs-lookup"><span data-stu-id="31055-120">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="31055-121">單向 gRPC 方法會傳回 `Empty` 結果，或使用用戶端串流。</span><span class="sxs-lookup"><span data-stu-id="31055-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="31055-122">請參閱此表格後面的段落。</span><span class="sxs-lookup"><span data-stu-id="31055-122">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="31055-123">這個屬性與 SOAP 相關，在 gRPC 中沒有意義。</span><span class="sxs-lookup"><span data-stu-id="31055-123">This property is SOAP related and has no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="31055-124">沒有訊息加密。</span><span class="sxs-lookup"><span data-stu-id="31055-124">There's no message encryption.</span></span> <span data-ttu-id="31055-125">網路加密會在傳輸層處理（TLS over HTTP/2）。</span><span class="sxs-lookup"><span data-stu-id="31055-125">Network encryption is handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="31055-126">這個屬性與 SOAP 相關，在 gRPC 中沒有意義。</span><span class="sxs-lookup"><span data-stu-id="31055-126">This property is SOAP related and has no meaning in gRPC.</span></span> |

<span data-ttu-id="31055-127">`IsInitiating` 屬性可讓您指出[ServiceContract](xref:System.ServiceModel.ServiceContractAttribute)中的方法不能是第一個呼叫作為會話一部分的方法。</span><span class="sxs-lookup"><span data-stu-id="31055-127">The `IsInitiating` property lets you indicate that a method within [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="31055-128">在呼叫作業之後，`IsTerminating` 屬性會導致伺服器關閉會話（如果在回呼用戶端上使用此屬性，則為用戶端）。</span><span class="sxs-lookup"><span data-stu-id="31055-128">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if the property is used on a callback client).</span></span> <span data-ttu-id="31055-129">在 gRPC 中，資料流程是由單一方法建立，並且明確地關閉。</span><span class="sxs-lookup"><span data-stu-id="31055-129">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="31055-130">請參閱[gRPC 串流](rpc-types.md#grpc-streaming)。</span><span class="sxs-lookup"><span data-stu-id="31055-130">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="31055-131">如需有關 gRPC 安全性和加密的詳細資訊，請參閱[第6章](security.md)。</span><span class="sxs-lookup"><span data-stu-id="31055-131">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="31055-132">[上一頁](wcf-services-to-grpc-comparison.md)
>[下一頁](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="31055-132">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
