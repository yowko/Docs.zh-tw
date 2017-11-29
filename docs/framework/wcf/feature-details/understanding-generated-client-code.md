---
title: "了解產生的用戶端程式碼"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d185371c1648241db7b01f26a49e2e1e8710b0e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="understanding-generated-client-code"></a><span data-ttu-id="f488c-102">了解產生的用戶端程式碼</span><span class="sxs-lookup"><span data-stu-id="f488c-102">Understanding Generated Client Code</span></span>
<span data-ttu-id="f488c-103">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 會產生用戶端程式碼和用戶端應用程式組態檔，用於建置用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="f488c-103">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generates client code and a client application configuration file for use in building client applications.</span></span> <span data-ttu-id="f488c-104">本主題將提供產生之程式碼範例的導覽，用於標準服務合約情節。</span><span class="sxs-lookup"><span data-stu-id="f488c-104">This topic provides a tour of generated code examples for standard service contract scenarios.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f488c-105"> 使用產生之程式碼建置用戶端應用程式的詳細資訊，請參閱 [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f488c-105"> building a client application using the generated code, see [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="f488c-106">概觀</span><span class="sxs-lookup"><span data-stu-id="f488c-106">Overview</span></span>  
 <span data-ttu-id="f488c-107">如果您使用 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 為您的專案產生 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端類型，通常不需要檢查產生的用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="f488c-107">If you use [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] to generate [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client types for your project, you typically do not need to examine the generated client code.</span></span> <span data-ttu-id="f488c-108">如果您不是使用為您執行相同服務的開發環境，可以使用如 Svcutil.exe 等工具來產生用戶端程式碼，然後使用該程式碼來開發您的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="f488c-108">If you are not using a development environment that performs the same services for you, you can use a tool such as Svcutil.exe to generate client code and then use that code to develop your client application.</span></span>  
  
 <span data-ttu-id="f488c-109">由於 Svcutil.exe 有許多選項可修改產生的型別資訊，因此本主題不會討論所有的案例。</span><span class="sxs-lookup"><span data-stu-id="f488c-109">Because Svcutil.exe has a number of options that modify the generated type information, this topic does not discuss all scenarios.</span></span> <span data-ttu-id="f488c-110">然而，下列標準工作包含找出產生的程式碼：</span><span class="sxs-lookup"><span data-stu-id="f488c-110">However, the following standard tasks involve locating generated code:</span></span>  
  
-   <span data-ttu-id="f488c-111">識別服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="f488c-111">Identifying service contract interfaces.</span></span>  
  
-   <span data-ttu-id="f488c-112">識別 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="f488c-112">Identifying the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class.</span></span>  
  
-   <span data-ttu-id="f488c-113">識別資料型別。</span><span class="sxs-lookup"><span data-stu-id="f488c-113">Identifying data types.</span></span>  
  
-   <span data-ttu-id="f488c-114">識別雙工服務的回呼合約。</span><span class="sxs-lookup"><span data-stu-id="f488c-114">Identifying callback contracts for duplex services.</span></span>  
  
-   <span data-ttu-id="f488c-115">識別協助程式服務合約通道介面。</span><span class="sxs-lookup"><span data-stu-id="f488c-115">Identifying the helper service contract channel interface.</span></span>  
  
### <a name="finding-service-contract-interfaces"></a><span data-ttu-id="f488c-116">尋找服務合約介面</span><span class="sxs-lookup"><span data-stu-id="f488c-116">Finding Service Contract Interfaces</span></span>  
 <span data-ttu-id="f488c-117">如果要找出建立服務合約模型的介面，請搜尋以 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 屬性標示的介面。</span><span class="sxs-lookup"><span data-stu-id="f488c-117">To locate the interfaces that model service contracts, search for interfaces that are marked with the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="f488c-118">由於其他屬性的存在，且這個屬性本身有明確的內容設定，因此常常很難快速找出這個屬性。</span><span class="sxs-lookup"><span data-stu-id="f488c-118">Often this attribute can be difficult to locate with a quick read due to the presence of other attributes and the explicit properties set on the attribute itself.</span></span> <span data-ttu-id="f488c-119">請記住，服務合約介面和用戶端合約介面是兩種不同的型別。</span><span class="sxs-lookup"><span data-stu-id="f488c-119">Remember that the service contract interface and the client contract interface are two different types.</span></span> <span data-ttu-id="f488c-120">下列程式碼範例會顯示原始的服務合約。</span><span class="sxs-lookup"><span data-stu-id="f488c-120">The following code example shows the original service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 <span data-ttu-id="f488c-121">下列程式碼範例會顯示和 Svcutil.exe 所產生之相同的服務合約。</span><span class="sxs-lookup"><span data-stu-id="f488c-121">The following code example shows the same service contract as generated by Svcutil.exe.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 <span data-ttu-id="f488c-122">您可以使用產生的服務合約介面以及 <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> 類別，來建立叫用服務作業的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通道物件。</span><span class="sxs-lookup"><span data-stu-id="f488c-122">You can use the generated service contract interface along with the <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> class to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel object with which to invoke service operations.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f488c-123">[How to： 使用 ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)。</span><span class="sxs-lookup"><span data-stu-id="f488c-123"> [How to: Use the ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).</span></span>  
  
### <a name="finding-wcf-client-classes"></a><span data-ttu-id="f488c-124">尋找 WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="f488c-124">Finding WCF Client Classes</span></span>  
 <span data-ttu-id="f488c-125">如果要找出實作您要使用之服務合約的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別，請搜尋 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> 的延伸，其中型別參數是您之前找出且延伸該介面的服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="f488c-125">To locate the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class that implements the service contract you want to use, search for an extension of <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, where the type parameter is the service contract interface that you previously located and that extends that interface.</span></span> <span data-ttu-id="f488c-126">下列程式碼範例會顯示型別 <xref:System.ServiceModel.ClientBase%601> 的 `ISampleService`類別。</span><span class="sxs-lookup"><span data-stu-id="f488c-126">The following code example shows the <xref:System.ServiceModel.ClientBase%601> class of type `ISampleService`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 <span data-ttu-id="f488c-127">您可以使用這個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別，方法是建立它的新執行個體並呼叫它實作的方法。</span><span class="sxs-lookup"><span data-stu-id="f488c-127">You can use this [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class by creating a new instance of it and calling the methods it implements.</span></span> <span data-ttu-id="f488c-128">這些方法會叫用用於設計及設定互動的服務作業。</span><span class="sxs-lookup"><span data-stu-id="f488c-128">Those methods invoke the service operation with which it is designed and configured to interact.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f488c-129">[WCF 用戶端概觀](../../../../docs/framework/wcf/wcf-client-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f488c-129"> [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f488c-130">當 SvcUtil.exe 產生 WCF 用戶端類別時，會將 <xref:System.Diagnostics.DebuggerStepThroughAttribute> 加入至用戶端類別，防止偵錯工具逐步執行 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="f488c-130">When SvcUtil.exe generates a WCF client class, it adds a <xref:System.Diagnostics.DebuggerStepThroughAttribute> to the client class that prevents debuggers from stepping through the WCF client class.</span></span>  
  
### <a name="finding-data-types"></a><span data-ttu-id="f488c-131">尋找資料型別</span><span class="sxs-lookup"><span data-stu-id="f488c-131">Finding Data Types</span></span>  
 <span data-ttu-id="f488c-132">如果要在產生的程式碼中找出資料型別，最基本的機制就是識別合約中指定的型別名稱，然後在程式碼中搜尋該型別宣告。</span><span class="sxs-lookup"><span data-stu-id="f488c-132">To locate data types in the generated code, the most basic mechanism is to identify the type name specified in a contract and search the code for that type declaration.</span></span> <span data-ttu-id="f488c-133">例如，下列合約指定 `SampleMethod` 可以傳回型別 `microsoft.wcf.documentation.SampleFault`的 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="f488c-133">For example, the following contract specifies that the `SampleMethod` can return a SOAP fault of type `microsoft.wcf.documentation.SampleFault`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 <span data-ttu-id="f488c-134">搜尋 `SampleFault` 會找出下列型別宣告。</span><span class="sxs-lookup"><span data-stu-id="f488c-134">Searching for `SampleFault` locates the following type declaration.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 <span data-ttu-id="f488c-135">在此情況下，資料型別是由用戶端上特定例外狀況擲回的詳細型別，其中詳細型別參數為 <xref:System.ServiceModel.FaultException%601> 的 `microsoft.wcf.documentation.SampleFault`。</span><span class="sxs-lookup"><span data-stu-id="f488c-135">In this case the data type is the detail type thrown by a specific exception on the client, a <xref:System.ServiceModel.FaultException%601> where the detail type parameter is `microsoft.wcf.documentation.SampleFault`.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f488c-136"> 資料型別的詳細資訊，請參閱 [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="f488c-136"> data types, see [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f488c-137"> 處理用戶端中例外狀況的詳細資訊，請參閱 [Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md)。</span><span class="sxs-lookup"><span data-stu-id="f488c-137"> handling exceptions in clients, see [Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md).</span></span>  
  
### <a name="finding-callback-contracts-for-duplex-services"></a><span data-ttu-id="f488c-138">尋找雙工服務的回呼合約</span><span class="sxs-lookup"><span data-stu-id="f488c-138">Finding Callback Contracts for Duplex Services</span></span>  
 <span data-ttu-id="f488c-139">如果您找出合約介面為其指定 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> 屬性值的服務合約，該合約就會指定雙工合約。</span><span class="sxs-lookup"><span data-stu-id="f488c-139">If you locate a service contract for which the contract interface specifies a value for the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property, then that contract specifies a duplex contract.</span></span> <span data-ttu-id="f488c-140">雙工合約需要用戶端應用程式建立回呼類別，實作回呼合約並將該類別的執行個體傳遞至用來與服務通訊的 <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> 或 <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f488c-140">Duplex contracts require the client application to create a callback class that implements the callback contract and pass an instance of that class to the <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> or <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> used to communicate with the service.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f488c-141">雙工用戶端，請參閱[How to: Access Services 搭配雙工合約](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="f488c-141"> duplex clients, see [How to: Access Services with a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="f488c-142">下列合約會指定型別 `SampleDuplexHelloCallback`的回呼合約。</span><span class="sxs-lookup"><span data-stu-id="f488c-142">The following contract specifies a callback contract of type `SampleDuplexHelloCallback`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 <span data-ttu-id="f488c-143">搜尋該回呼合約會找出下列用戶端應用程式必須實作的介面。</span><span class="sxs-lookup"><span data-stu-id="f488c-143">Searching for that callback contract locates the following interface that the client application must implement.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a><span data-ttu-id="f488c-144">尋找服務合約通道介面</span><span class="sxs-lookup"><span data-stu-id="f488c-144">Finding Service Contract Channel Interfaces</span></span>  
 <span data-ttu-id="f488c-145">當使用含有服務合約介面的 <xref:System.ServiceModel.ChannelFactory> 類別時，您必須轉換為 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> 介面，以明確開啟、關閉或中止通道。</span><span class="sxs-lookup"><span data-stu-id="f488c-145">When using the <xref:System.ServiceModel.ChannelFactory> class with a service contract interface, you must cast to the <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface to explicitly open, close, or abort the channel.</span></span> <span data-ttu-id="f488c-146">為了讓這個類別更容易使用，Svcutil.exe 工具會另外產生可以實作服務合約介面和 <xref:System.ServiceModel.IClientChannel> 兩者的協助程式介面，讓您可以不用轉型就與用戶端通道基礎結構進行互動。</span><span class="sxs-lookup"><span data-stu-id="f488c-146">To make it easier to work with, the Svcutil.exe tool also generates a helper interface that implements both the service contract interface and <xref:System.ServiceModel.IClientChannel> to enable you to interact with the client channel infrastructure without having to cast.</span></span> <span data-ttu-id="f488c-147">下列程式碼會示範實作前述服務合約之協助程式用戶端通道的定義。</span><span class="sxs-lookup"><span data-stu-id="f488c-147">The following code shows the definition of a helper client channel that implements the preceding service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="f488c-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f488c-148">See Also</span></span>  
 [<span data-ttu-id="f488c-149">WCF 用戶端概觀</span><span class="sxs-lookup"><span data-stu-id="f488c-149">WCF Client Overview</span></span>](../../../../docs/framework/wcf/wcf-client-overview.md)
