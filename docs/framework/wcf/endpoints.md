---
title: Windows Communication Foundation 端點
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: f11a8198d38a01fe27a84a3e613e1ff066c25b9d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319917"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="42dfb-102">Windows Communication Foundation 端點</span><span class="sxs-lookup"><span data-stu-id="42dfb-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="42dfb-103">所有與 Windows Communication Foundation （WCF）服務的通訊都是透過服務的*端點*進行。</span><span class="sxs-lookup"><span data-stu-id="42dfb-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="42dfb-104">端點可讓用戶端存取 WCF 服務所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="42dfb-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="42dfb-105">如需如何建立端點的總覽，請參閱[端點建立總覽](endpoint-creation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="42dfb-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="42dfb-106">每個端點包含：</span><span class="sxs-lookup"><span data-stu-id="42dfb-106">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="42dfb-107">指出可在何處找到端點的位址。</span><span class="sxs-lookup"><span data-stu-id="42dfb-107">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="42dfb-108">指定用戶端可以如何與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="42dfb-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="42dfb-109">識別可用方法的合約。</span><span class="sxs-lookup"><span data-stu-id="42dfb-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="42dfb-110">如需有關如何指定端點之這些個別部分的說明，請參閱：</span><span class="sxs-lookup"><span data-stu-id="42dfb-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="42dfb-111">指定端點位址</span><span class="sxs-lookup"><span data-stu-id="42dfb-111">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="42dfb-112">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="42dfb-112">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="42dfb-113">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="42dfb-113">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="42dfb-114">本章節內容</span><span class="sxs-lookup"><span data-stu-id="42dfb-114">In This Section</span></span>  
 [<span data-ttu-id="42dfb-115">建立端點概觀</span><span class="sxs-lookup"><span data-stu-id="42dfb-115">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)  
 <span data-ttu-id="42dfb-116">說明端點的結構，並且摘要說明如何透過組態與程式碼來定義端點，以及如何使用執行階段所提供的預設端點、繫結和行為。</span><span class="sxs-lookup"><span data-stu-id="42dfb-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="42dfb-117">指定端點位址</span><span class="sxs-lookup"><span data-stu-id="42dfb-117">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
 <span data-ttu-id="42dfb-118">描述如何透過端點與 WCF 服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="42dfb-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="42dfb-119">如何：在組態中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="42dfb-119">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="42dfb-120">示範如何在組態中建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="42dfb-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="42dfb-121">如何：在程式碼中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="42dfb-121">How to: Create a Service Endpoint in Code</span></span>](./feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="42dfb-122">示範如何在程式碼中建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="42dfb-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="42dfb-123">發行中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="42dfb-123">Publishing Metadata Endpoints</span></span>](publishing-metadata-endpoints.md)  
 <span data-ttu-id="42dfb-124">示範如何在組態和程式碼中發行中繼資料端點，以發行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="42dfb-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="42dfb-125">參考資料</span><span class="sxs-lookup"><span data-stu-id="42dfb-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="42dfb-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="42dfb-126">Related Sections</span></span>  
 [<span data-ttu-id="42dfb-127">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="42dfb-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)
