---
title: "端點：位址、繫結和合約"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af82cb934570b371d332c0e08ebc9b2338d0c0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="c3c58-102">端點：位址、繫結和合約</span><span class="sxs-lookup"><span data-stu-id="c3c58-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="c3c58-103">所有與通訊[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]服務會透過*端點*的服務。</span><span class="sxs-lookup"><span data-stu-id="c3c58-103">All communication with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="c3c58-104">端點針對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務所提供的功能提供了用戶端存取。</span><span class="sxs-lookup"><span data-stu-id="c3c58-104">Endpoints provide clients access to the functionality offered by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="c3c58-105">端點包含四項屬性：</span><span class="sxs-lookup"><span data-stu-id="c3c58-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="c3c58-106">指出可在何處找到端點的位址。</span><span class="sxs-lookup"><span data-stu-id="c3c58-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="c3c58-107">指定用戶端可以如何與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="c3c58-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="c3c58-108">識別可用作業的合約。</span><span class="sxs-lookup"><span data-stu-id="c3c58-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="c3c58-109">指定本機端點實作細節的行為集。</span><span class="sxs-lookup"><span data-stu-id="c3c58-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="c3c58-110">本主題討論這個端點結構並說明如何以 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 物件模型來加以表示。</span><span class="sxs-lookup"><span data-stu-id="c3c58-110">This topic discusses this endpoint structure and explains how it is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="c3c58-111">端點結構</span><span class="sxs-lookup"><span data-stu-id="c3c58-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="c3c58-112">每個端點都包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="c3c58-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="c3c58-113">位址：位址會唯一識別端點並告訴潛在取用者服務的位置。</span><span class="sxs-lookup"><span data-stu-id="c3c58-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="c3c58-114">它會透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 物件模型中的 <xref:System.ServiceModel.EndpointAddress> 類別來表示。</span><span class="sxs-lookup"><span data-stu-id="c3c58-114">It is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="c3c58-115"><xref:System.ServiceModel.EndpointAddress> 類別包含：</span><span class="sxs-lookup"><span data-stu-id="c3c58-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="c3c58-116"><xref:System.ServiceModel.EndpointAddress.Uri%2A> 屬性，用來代表服務位址。</span><span class="sxs-lookup"><span data-stu-id="c3c58-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="c3c58-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> 屬性，用來代表服務的安全性身分識別以及一群選用的訊息標頭集合。</span><span class="sxs-lookup"><span data-stu-id="c3c58-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="c3c58-118">選用訊息標頭會用來提供其他更詳細的定址資訊來識別端點或與端點互動。</span><span class="sxs-lookup"><span data-stu-id="c3c58-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="c3c58-119">[指定端點位址](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="c3c58-119"> [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="c3c58-120">繫結：繫結會指定與端點的通訊方式。</span><span class="sxs-lookup"><span data-stu-id="c3c58-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="c3c58-121">包括：</span><span class="sxs-lookup"><span data-stu-id="c3c58-121">This includes:</span></span>  
  
    -   <span data-ttu-id="c3c58-122">要使用的傳輸通訊協定 (例如，TCP 或 HTTP)。</span><span class="sxs-lookup"><span data-stu-id="c3c58-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="c3c58-123">訊息使用的編碼 (例如，文字或二進位)。</span><span class="sxs-lookup"><span data-stu-id="c3c58-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="c3c58-124">必要的安全性需求 (例如，SSL 或 SOAP 訊息安全性)。</span><span class="sxs-lookup"><span data-stu-id="c3c58-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="c3c58-125">[WCF 繫結概觀](../../../../docs/framework/wcf/bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c3c58-125"> [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="c3c58-126">繫結會透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 物件模型中的抽象基底類別 <xref:System.ServiceModel.Channels.Binding> 來表示。</span><span class="sxs-lookup"><span data-stu-id="c3c58-126">A binding is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="c3c58-127">在大部分情況中，使用者可以使用下列其中一種系統提供的繫結。</span><span class="sxs-lookup"><span data-stu-id="c3c58-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="c3c58-128">如需詳細資訊，請參閱[之繫結](../../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="c3c58-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="c3c58-129">合約：合約會概略說明端點公開哪些功能給用戶端。</span><span class="sxs-lookup"><span data-stu-id="c3c58-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="c3c58-130">合約會指定：</span><span class="sxs-lookup"><span data-stu-id="c3c58-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="c3c58-131">用戶端可以呼叫的作業。</span><span class="sxs-lookup"><span data-stu-id="c3c58-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="c3c58-132">訊息格式。</span><span class="sxs-lookup"><span data-stu-id="c3c58-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="c3c58-133">呼叫作業所需的輸入參數或資料型別。</span><span class="sxs-lookup"><span data-stu-id="c3c58-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="c3c58-134">用戶端可以期待收到的處理或回應訊息型別。</span><span class="sxs-lookup"><span data-stu-id="c3c58-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="c3c58-135">如需有關如何定義合約的詳細資訊，請參閱[設計服務合約](../../../../docs/framework/wcf/designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="c3c58-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="c3c58-136">行為：您可以使用端點行為來自訂服務端點的本機行為。</span><span class="sxs-lookup"><span data-stu-id="c3c58-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="c3c58-137">端點行為來達成此目的參與正在建置[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]執行階段。</span><span class="sxs-lookup"><span data-stu-id="c3c58-137">Endpoint behaviors achieve this by participating in the process of building a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]runtime.</span></span> <span data-ttu-id="c3c58-138"><xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> 屬性是一個端點行為範例，它可讓您指定不同於 SOAP 或 Web 服務描述語言 (WSDL) 位址的接聽位址。</span><span class="sxs-lookup"><span data-stu-id="c3c58-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="c3c58-139">[ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md)。</span><span class="sxs-lookup"><span data-stu-id="c3c58-139"> [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="c3c58-140">定義端點</span><span class="sxs-lookup"><span data-stu-id="c3c58-140">Defining Endpoints</span></span>  
 <span data-ttu-id="c3c58-141">您可以透過命令式程式碼或是宣告式組態來指定服務端點。</span><span class="sxs-lookup"><span data-stu-id="c3c58-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="c3c58-142">[How to： 在組態中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)和[How to： 在程式碼中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="c3c58-142"> [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3c58-143">本節內容</span><span class="sxs-lookup"><span data-stu-id="c3c58-143">In This Section</span></span>  
 <span data-ttu-id="c3c58-144">本章節說明繫結、端點與位址的用途；說明如何設定繫結與端點；並示範如何使用 `ClientVia` 行為和 `ListenUri` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c3c58-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="c3c58-145">位址</span><span class="sxs-lookup"><span data-stu-id="c3c58-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="c3c58-146">說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 如何處理端點。</span><span class="sxs-lookup"><span data-stu-id="c3c58-146">Describes how endpoints are addressed in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="c3c58-147">繫結</span><span class="sxs-lookup"><span data-stu-id="c3c58-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="c3c58-148">說明如何使用繫結程序來指定必要的傳輸、編碼與通訊協定詳細資料，以供用戶端與服務彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="c3c58-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="c3c58-149">合約</span><span class="sxs-lookup"><span data-stu-id="c3c58-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="c3c58-150">說明合約如何定義服務方法。</span><span class="sxs-lookup"><span data-stu-id="c3c58-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="c3c58-151">如何：在組態中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="c3c58-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="c3c58-152">說明如何透過組態建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="c3c58-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="c3c58-153">如何：在程式碼中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="c3c58-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="c3c58-154">說明如何透過程式碼建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="c3c58-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="c3c58-155">如何：使用 Svcutil.exe 來驗證已編譯服務程式碼</span><span class="sxs-lookup"><span data-stu-id="c3c58-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="c3c58-156">描述如何在服務實作和組態中偵測錯誤，而不需要裝載服務會使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="c3c58-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3c58-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3c58-157">See Also</span></span>  
 [<span data-ttu-id="c3c58-158">設定服務</span><span class="sxs-lookup"><span data-stu-id="c3c58-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="c3c58-159">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="c3c58-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
