---
title: 了解產生的用戶端程式碼
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 22cb7a7b4cd6712d509586cb2ae7699d233eff2a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281621"
---
# <a name="understanding-generated-client-code"></a><span data-ttu-id="6a1b1-102">了解產生的用戶端程式碼</span><span class="sxs-lookup"><span data-stu-id="6a1b1-102">Understanding Generated Client Code</span></span>

<span data-ttu-id="6a1b1-103">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 會產生用戶端程式碼和用戶端應用程式組態檔，用於建置用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-103">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) generates client code and a client application configuration file for use in building client applications.</span></span> <span data-ttu-id="6a1b1-104">本主題將提供產生之程式碼範例的導覽，用於標準服務合約情節。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-104">This topic provides a tour of generated code examples for standard service contract scenarios.</span></span> <span data-ttu-id="6a1b1-105">如需使用產生的程式碼來建立用戶端應用程式的詳細資訊，請參閱 [WCF 用戶端總覽](../wcf-client-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-105">For more information about building a client application using the generated code, see [WCF Client Overview](../wcf-client-overview.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="6a1b1-106">概觀</span><span class="sxs-lookup"><span data-stu-id="6a1b1-106">Overview</span></span>  

 <span data-ttu-id="6a1b1-107">如果您使用 Visual Studio 產生專案的 Windows Communication Foundation (WCF) 用戶端類型，您通常不需要檢查產生的用戶端程式代碼。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-107">If you use Visual Studio to generate Windows Communication Foundation (WCF) client types for your project, you typically do not need to examine the generated client code.</span></span> <span data-ttu-id="6a1b1-108">如果您不是使用為您執行相同服務的開發環境，可以使用如 Svcutil.exe 等工具來產生用戶端程式碼，然後使用該程式碼來開發您的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-108">If you are not using a development environment that performs the same services for you, you can use a tool such as Svcutil.exe to generate client code and then use that code to develop your client application.</span></span>  
  
 <span data-ttu-id="6a1b1-109">由於 Svcutil.exe 有許多選項可修改產生的型別資訊，因此本主題不會討論所有的案例。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-109">Because Svcutil.exe has a number of options that modify the generated type information, this topic does not discuss all scenarios.</span></span> <span data-ttu-id="6a1b1-110">然而，下列標準工作包含找出產生的程式碼：</span><span class="sxs-lookup"><span data-stu-id="6a1b1-110">However, the following standard tasks involve locating generated code:</span></span>  
  
- <span data-ttu-id="6a1b1-111">識別服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-111">Identifying service contract interfaces.</span></span>  
  
- <span data-ttu-id="6a1b1-112">識別 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-112">Identifying the WCF client class.</span></span>  
  
- <span data-ttu-id="6a1b1-113">識別資料型別。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-113">Identifying data types.</span></span>  
  
- <span data-ttu-id="6a1b1-114">識別雙工服務的回呼合約。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-114">Identifying callback contracts for duplex services.</span></span>  
  
- <span data-ttu-id="6a1b1-115">識別協助程式服務合約通道介面。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-115">Identifying the helper service contract channel interface.</span></span>  
  
### <a name="finding-service-contract-interfaces"></a><span data-ttu-id="6a1b1-116">尋找服務合約介面</span><span class="sxs-lookup"><span data-stu-id="6a1b1-116">Finding Service Contract Interfaces</span></span>  

 <span data-ttu-id="6a1b1-117">如果要找出建立服務合約模型的介面，請搜尋以 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 屬性標示的介面。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-117">To locate the interfaces that model service contracts, search for interfaces that are marked with the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="6a1b1-118">由於其他屬性的存在，且這個屬性本身有明確的內容設定，因此常常很難快速找出這個屬性。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-118">Often this attribute can be difficult to locate with a quick read due to the presence of other attributes and the explicit properties set on the attribute itself.</span></span> <span data-ttu-id="6a1b1-119">請記住，服務合約介面和用戶端合約介面是兩種不同的型別。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-119">Remember that the service contract interface and the client contract interface are two different types.</span></span> <span data-ttu-id="6a1b1-120">下列程式碼範例會顯示原始的服務合約。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-120">The following code example shows the original service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 <span data-ttu-id="6a1b1-121">下列程式碼範例會顯示和 Svcutil.exe 所產生之相同的服務合約。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-121">The following code example shows the same service contract as generated by Svcutil.exe.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 <span data-ttu-id="6a1b1-122">您可以使用產生的服務合約介面以及 <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> 類別，建立用來叫用服務作業的 WCF 通道物件。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-122">You can use the generated service contract interface along with the <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> class to create a WCF channel object with which to invoke service operations.</span></span> <span data-ttu-id="6a1b1-123">如需詳細資訊，請參閱 [如何：使用 ChannelFactory](how-to-use-the-channelfactory.md)。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-123">For more information, see [How to: Use the ChannelFactory](how-to-use-the-channelfactory.md).</span></span>  
  
### <a name="finding-wcf-client-classes"></a><span data-ttu-id="6a1b1-124">尋找 WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="6a1b1-124">Finding WCF Client Classes</span></span>  

 <span data-ttu-id="6a1b1-125">若要找出您想要使用之服務合約的 WCF 用戶端類別，請搜尋的延伸模組 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> ，其中型別參數是您先前所找出並擴充該介面的服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-125">To locate the WCF client class that implements the service contract you want to use, search for an extension of <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, where the type parameter is the service contract interface that you previously located and that extends that interface.</span></span> <span data-ttu-id="6a1b1-126">下列程式碼範例會顯示型別 <xref:System.ServiceModel.ClientBase%601> 的 `ISampleService`類別。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-126">The following code example shows the <xref:System.ServiceModel.ClientBase%601> class of type `ISampleService`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 <span data-ttu-id="6a1b1-127">您可以使用這個 WCF 用戶端類別，方法是建立新的實例，並呼叫它所實行的方法。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-127">You can use this WCF client class by creating a new instance of it and calling the methods it implements.</span></span> <span data-ttu-id="6a1b1-128">這些方法會叫用用於設計及設定互動的服務作業。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-128">Those methods invoke the service operation with which it is designed and configured to interact.</span></span> <span data-ttu-id="6a1b1-129">如需詳細資訊，請參閱 [WCF 用戶端總覽](../wcf-client-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-129">For more information, see [WCF Client Overview](../wcf-client-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a1b1-130">當 SvcUtil.exe 產生 WCF 用戶端類別時，會將 <xref:System.Diagnostics.DebuggerStepThroughAttribute> 加入至用戶端類別，防止偵錯工具逐步執行 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-130">When SvcUtil.exe generates a WCF client class, it adds a <xref:System.Diagnostics.DebuggerStepThroughAttribute> to the client class that prevents debuggers from stepping through the WCF client class.</span></span>  
  
### <a name="finding-data-types"></a><span data-ttu-id="6a1b1-131">尋找資料型別</span><span class="sxs-lookup"><span data-stu-id="6a1b1-131">Finding Data Types</span></span>  

 <span data-ttu-id="6a1b1-132">如果要在產生的程式碼中找出資料型別，最基本的機制就是識別合約中指定的型別名稱，然後在程式碼中搜尋該型別宣告。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-132">To locate data types in the generated code, the most basic mechanism is to identify the type name specified in a contract and search the code for that type declaration.</span></span> <span data-ttu-id="6a1b1-133">例如，下列合約指定 `SampleMethod` 可以傳回型別 `microsoft.wcf.documentation.SampleFault`的 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-133">For example, the following contract specifies that the `SampleMethod` can return a SOAP fault of type `microsoft.wcf.documentation.SampleFault`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 <span data-ttu-id="6a1b1-134">搜尋 `SampleFault` 會找出下列型別宣告。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-134">Searching for `SampleFault` locates the following type declaration.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 <span data-ttu-id="6a1b1-135">在此情況下，資料型別是由用戶端上特定例外狀況擲回的詳細型別，其中詳細型別參數為 <xref:System.ServiceModel.FaultException%601> 的 `microsoft.wcf.documentation.SampleFault`。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-135">In this case the data type is the detail type thrown by a specific exception on the client, a <xref:System.ServiceModel.FaultException%601> where the detail type parameter is `microsoft.wcf.documentation.SampleFault`.</span></span> <span data-ttu-id="6a1b1-136">如需資料類型的詳細資訊，請參閱 [指定服務合約中的資料傳輸](specifying-data-transfer-in-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-136">For more information about data types, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="6a1b1-137">如需在用戶端中處理例外狀況的詳細資訊，請參閱傳送 [和接收錯誤](../sending-and-receiving-faults.md)。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-137">For more information about handling exceptions in clients, see [Sending and Receiving Faults](../sending-and-receiving-faults.md).</span></span>  
  
### <a name="finding-callback-contracts-for-duplex-services"></a><span data-ttu-id="6a1b1-138">尋找雙工服務的回呼合約</span><span class="sxs-lookup"><span data-stu-id="6a1b1-138">Finding Callback Contracts for Duplex Services</span></span>  

 <span data-ttu-id="6a1b1-139">如果您找出合約介面為其指定 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> 屬性值的服務合約，該合約就會指定雙工合約。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-139">If you locate a service contract for which the contract interface specifies a value for the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property, then that contract specifies a duplex contract.</span></span> <span data-ttu-id="6a1b1-140">雙工合約需要用戶端應用程式建立回呼類別，實作回呼合約並將該類別的執行個體傳遞至用來與服務通訊的 <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> 或 <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-140">Duplex contracts require the client application to create a callback class that implements the callback contract and pass an instance of that class to the <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> or <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> used to communicate with the service.</span></span> <span data-ttu-id="6a1b1-141">如需雙工用戶端的詳細資訊，請參閱 how [to：使用雙工合約存取服務](how-to-access-services-with-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-141">For more information about duplex clients, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="6a1b1-142">下列合約會指定型別 `SampleDuplexHelloCallback`的回呼合約。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-142">The following contract specifies a callback contract of type `SampleDuplexHelloCallback`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 <span data-ttu-id="6a1b1-143">搜尋該回呼合約會找出下列用戶端應用程式必須實作的介面。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-143">Searching for that callback contract locates the following interface that the client application must implement.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a><span data-ttu-id="6a1b1-144">尋找服務合約通道介面</span><span class="sxs-lookup"><span data-stu-id="6a1b1-144">Finding Service Contract Channel Interfaces</span></span>  

 <span data-ttu-id="6a1b1-145">當使用含有服務合約介面的 <xref:System.ServiceModel.ChannelFactory> 類別時，您必須轉換為 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> 介面，以明確開啟、關閉或中止通道。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-145">When using the <xref:System.ServiceModel.ChannelFactory> class with a service contract interface, you must cast to the <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface to explicitly open, close, or abort the channel.</span></span> <span data-ttu-id="6a1b1-146">為了讓這個類別更容易使用，Svcutil.exe 工具會另外產生可以實作服務合約介面和 <xref:System.ServiceModel.IClientChannel> 兩者的協助程式介面，讓您可以不用轉型就與用戶端通道基礎結構進行互動。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-146">To make it easier to work with, the Svcutil.exe tool also generates a helper interface that implements both the service contract interface and <xref:System.ServiceModel.IClientChannel> to enable you to interact with the client channel infrastructure without having to cast.</span></span> <span data-ttu-id="6a1b1-147">下列程式碼會示範實作前述服務合約之協助程式用戶端通道的定義。</span><span class="sxs-lookup"><span data-stu-id="6a1b1-147">The following code shows the definition of a helper client channel that implements the preceding service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="6a1b1-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a1b1-148">See also</span></span>

- [<span data-ttu-id="6a1b1-149">WCF 用戶端概觀</span><span class="sxs-lookup"><span data-stu-id="6a1b1-149">WCF Client Overview</span></span>](../wcf-client-overview.md)
