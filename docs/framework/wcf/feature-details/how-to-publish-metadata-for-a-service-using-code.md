---
title: "HOW TO：使用程式碼發行服務的中繼資料"
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
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 455929144f771128ca070cd02e65c919ce4c741f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="a44ad-102">HOW TO：使用程式碼發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="a44ad-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="a44ad-103">本文是探討發行 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務中繼資料的兩個 HOW TO 主題之其一。</span><span class="sxs-lookup"><span data-stu-id="a44ad-103">This is one of two how-to topics that discuss publishing metadata for a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="a44ad-104">有兩種方法可以指定服務發行中繼資料的方式，分別是使用組態檔和使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="a44ad-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="a44ad-105">本主題說明如何使用程式碼發行服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a44ad-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a44ad-106">本主題將示範以不安全的方法發行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a44ad-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="a44ad-107">任何用戶端都能從服務擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a44ad-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="a44ad-108">若您的服務需要以安全的方法發行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a44ad-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="a44ad-109">請參閱[自訂安全中繼資料端點](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="a44ad-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a44ad-110">發行中繼資料，在組態檔中，請參閱[How to： 使用組態檔的服務發行中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="a44ad-110"> publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="a44ad-111">發行中繼資料可讓用戶端透過 WS-Transfer GET 要求，或是透過使用 `?wsdl` 查詢字串的 HTTP/GET 要求來擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a44ad-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="a44ad-112">若要確定程式碼可以運作，您必須建立基本的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="a44ad-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="a44ad-113">下列程式碼提供您基本的自我裝載服務。</span><span class="sxs-lookup"><span data-stu-id="a44ad-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="a44ad-114">若要透過程式碼發行中繼資料</span><span class="sxs-lookup"><span data-stu-id="a44ad-114">To publish metadata in code</span></span>  
  
1.  <span data-ttu-id="a44ad-115">在主控台應用程式的 main 方法中，傳入服務類型與基底位址來產生 <xref:System.ServiceModel.ServiceHost> 物件。</span><span class="sxs-lookup"><span data-stu-id="a44ad-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  <span data-ttu-id="a44ad-116">在步驟 1 的程式碼底下，立即建立 try 區塊，以便在執行服務時，攔截任何擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a44ad-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  <span data-ttu-id="a44ad-117">檢查服務主機是否已包含 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>，如果沒有的話，建立新的 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a44ad-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  <span data-ttu-id="a44ad-118">將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 屬性設定為 `true.`</span><span class="sxs-lookup"><span data-stu-id="a44ad-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  <span data-ttu-id="a44ad-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> 會包含 <xref:System.ServiceModel.Description.MetadataExporter> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a44ad-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="a44ad-120"><xref:System.ServiceModel.Description.MetadataExporter> 會包含 <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a44ad-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="a44ad-121">將 <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> 屬性值設定為 <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>。</span><span class="sxs-lookup"><span data-stu-id="a44ad-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="a44ad-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> 屬性也可以設為 <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>。</span><span class="sxs-lookup"><span data-stu-id="a44ad-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="a44ad-123">當設定為<xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>中繼資料匯出工具會產生與中繼資料的原則資訊的 「 符合 Ws-policy 1.5。</span><span class="sxs-lookup"><span data-stu-id="a44ad-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="a44ad-124">一旦設為 <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>，中繼資料匯出工具會產生符合 WS-Policy 1.2 的原則資訊。</span><span class="sxs-lookup"><span data-stu-id="a44ad-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  <span data-ttu-id="a44ad-125">將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 執行個體新增至服務主機的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="a44ad-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  <span data-ttu-id="a44ad-126">將中繼資料交換端點新增至服務主機。</span><span class="sxs-lookup"><span data-stu-id="a44ad-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  <span data-ttu-id="a44ad-127">將應用程式端點新增至服務主機。</span><span class="sxs-lookup"><span data-stu-id="a44ad-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  <span data-ttu-id="a44ad-128">如果您沒有將任何端點加入至服務中，執行階段會為您加入預設端點。</span><span class="sxs-lookup"><span data-stu-id="a44ad-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="a44ad-129">在這個範例中，由於服務將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 設定為 `true`，表示服務已啟用中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="a44ad-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a44ad-130">預設端點，請參閱[簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a44ad-130"> default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="a44ad-131">開啟服務主機並等候傳入呼叫。</span><span class="sxs-lookup"><span data-stu-id="a44ad-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="a44ad-132">當使用者按下 ENTER 鍵時，關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="a44ad-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="a44ad-133">建置並執行主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="a44ad-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="a44ad-134">使用 Internet Explorer 瀏覽至服務的基底位址 (此範例中為 http://localhost:8001/MetadataSample)，然後確認已開啟中繼資料發行功能。</span><span class="sxs-lookup"><span data-stu-id="a44ad-134">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="a44ad-135">您應該會看到頁面上方標示「簡易服務」，且在其下跟著「您已建立服務」的網頁。</span><span class="sxs-lookup"><span data-stu-id="a44ad-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="a44ad-136">如果沒有的話，結果頁面上方應該會顯示：「為此服務發行的中繼資料目前停用」。</span><span class="sxs-lookup"><span data-stu-id="a44ad-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="a44ad-137">範例</span><span class="sxs-lookup"><span data-stu-id="a44ad-137">Example</span></span>  
 <span data-ttu-id="a44ad-138">下列程式碼範例說明可透過程式碼發行服務中繼資料的基本 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務實作。</span><span class="sxs-lookup"><span data-stu-id="a44ad-138">The following code example shows the implementation of a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="a44ad-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="a44ad-139">See Also</span></span>  
 [<span data-ttu-id="a44ad-140">如何：於受管理的應用程式中裝載 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="a44ad-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="a44ad-141">自我裝載</span><span class="sxs-lookup"><span data-stu-id="a44ad-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="a44ad-142">中繼資料架構概觀</span><span class="sxs-lookup"><span data-stu-id="a44ad-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="a44ad-143">使用中繼資料</span><span class="sxs-lookup"><span data-stu-id="a44ad-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="a44ad-144">如何：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="a44ad-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
