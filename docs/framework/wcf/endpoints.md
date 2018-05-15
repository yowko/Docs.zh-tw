---
title: Windows Communication Foundation 端點
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: b55abe937701f8708643efa2ea4cb62514b3521b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="43bfb-102">Windows Communication Foundation 端點</span><span class="sxs-lookup"><span data-stu-id="43bfb-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="43bfb-103">所有與 Windows Communication Foundation (WCF) 服務的通訊會透過*端點*的服務。</span><span class="sxs-lookup"><span data-stu-id="43bfb-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="43bfb-104">端點可讓用戶端存取 WCF 服務提供的功能。</span><span class="sxs-lookup"><span data-stu-id="43bfb-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="43bfb-105">如需有關如何建立端點的概觀，請參閱[端點建立概觀](../../../docs/framework/wcf/endpoint-creation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="43bfb-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="43bfb-106">每個端點包含：</span><span class="sxs-lookup"><span data-stu-id="43bfb-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="43bfb-107">指出可在何處找到端點的位址。</span><span class="sxs-lookup"><span data-stu-id="43bfb-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="43bfb-108">指定用戶端可以如何與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="43bfb-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="43bfb-109">識別可用方法的合約。</span><span class="sxs-lookup"><span data-stu-id="43bfb-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="43bfb-110">如需有關如何指定端點之這些個別部分的說明，請參閱：</span><span class="sxs-lookup"><span data-stu-id="43bfb-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   [<span data-ttu-id="43bfb-111">指定端點位址</span><span class="sxs-lookup"><span data-stu-id="43bfb-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [<span data-ttu-id="43bfb-112">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="43bfb-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [<span data-ttu-id="43bfb-113">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="43bfb-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="43bfb-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="43bfb-114">In This Section</span></span>  
 [<span data-ttu-id="43bfb-115">建立端點概觀</span><span class="sxs-lookup"><span data-stu-id="43bfb-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="43bfb-116">說明端點的結構，並且摘要說明如何透過組態與程式碼來定義端點，以及如何使用執行階段所提供的預設端點、繫結和行為。</span><span class="sxs-lookup"><span data-stu-id="43bfb-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="43bfb-117">指定端點位址</span><span class="sxs-lookup"><span data-stu-id="43bfb-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="43bfb-118">描述如何透過端點來進行與 WCF 服務的通訊。</span><span class="sxs-lookup"><span data-stu-id="43bfb-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="43bfb-119">如何：在組態中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="43bfb-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="43bfb-120">示範如何在組態中建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="43bfb-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="43bfb-121">如何：在程式碼中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="43bfb-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="43bfb-122">示範如何在程式碼中建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="43bfb-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="43bfb-123">發行中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="43bfb-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="43bfb-124">示範如何在組態和程式碼中發行中繼資料端點，以發行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="43bfb-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="43bfb-125">參考資料</span><span class="sxs-lookup"><span data-stu-id="43bfb-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="43bfb-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="43bfb-126">Related Sections</span></span>  
 [<span data-ttu-id="43bfb-127">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="43bfb-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
