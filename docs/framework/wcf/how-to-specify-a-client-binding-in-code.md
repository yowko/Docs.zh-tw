---
title: HOW TO：在程式碼中指定用戶端繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: ec5db7a305a63ac7ae9c2e2a7bb1c9c7691b8daa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320892"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="c65d5-102">HOW TO：在程式碼中指定用戶端繫結</span><span class="sxs-lookup"><span data-stu-id="c65d5-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="c65d5-103">在這個範例中，建立了一個使用計算機服務的用戶端，並於程式碼中以命令方式指定該用戶端的繫結。</span><span class="sxs-lookup"><span data-stu-id="c65d5-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="c65d5-104">用戶端會存取 `CalculatorService` (該服務會實作 `ICalculator` 介面)，而服務和用戶端都會使用 <xref:System.ServiceModel.BasicHttpBinding> 類別。</span><span class="sxs-lookup"><span data-stu-id="c65d5-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="c65d5-105">此程序假設計算機服務正在執行中。</span><span class="sxs-lookup"><span data-stu-id="c65d5-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="c65d5-106">如需建立服務的相關資訊，請參閱 how [to：在 Configuration 中指定服務](how-to-specify-a-service-binding-in-configuration.md)系結。</span><span class="sxs-lookup"><span data-stu-id="c65d5-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="c65d5-107">它也會使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](servicemodel-metadata-utility-tool-svcutil-exe.md)，WINDOWS COMMUNICATION FOUNDATION （WCF）提供自動產生用戶端元件。</span><span class="sxs-lookup"><span data-stu-id="c65d5-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="c65d5-108">此工具會產生存取服務所需的用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="c65d5-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="c65d5-109">用戶端會建置成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="c65d5-109">The client is built in two parts.</span></span> <span data-ttu-id="c65d5-110">Svcutil.exe 會產生 `ClientCalculator`，而該元件會實作 `ICalculator` 介面。</span><span class="sxs-lookup"><span data-stu-id="c65d5-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="c65d5-111">接著，會建構 `ClientCalculator` 的執行個體，並在程式碼中指定此服務的繫結與位址，藉此建構此用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="c65d5-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="c65d5-112">如需此範例的來源複本，請參閱[BasicBinding](./samples/basicbinding.md)範例。</span><span class="sxs-lookup"><span data-stu-id="c65d5-112">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="c65d5-113">若要在程式碼中指定自訂繫結</span><span class="sxs-lookup"><span data-stu-id="c65d5-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="c65d5-114">從命令列使用 Svcutil.exe 產生取自服務中繼資料的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c65d5-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="c65d5-115">所產生的用戶端會包含 `ICalculator` 介面，其中定義了用戶端實作所必須滿足的服務合約。</span><span class="sxs-lookup"><span data-stu-id="c65d5-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="c65d5-116">產生的用戶端也會包含 `ClientCalculator` 的實作。</span><span class="sxs-lookup"><span data-stu-id="c65d5-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="c65d5-117">建立 `ClientCalculator` 的執行個體 (此執行個體會在用戶端應用程式中使用 <xref:System.ServiceModel.BasicHttpBinding> 類別)，然後在指定的位址上呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="c65d5-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="c65d5-118">請編譯並執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="c65d5-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65d5-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="c65d5-119">See also</span></span>

- [<span data-ttu-id="c65d5-120">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="c65d5-120">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
