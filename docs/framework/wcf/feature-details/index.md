---
title: WCF 功能詳細資料
ms.date: 03/30/2017
helpviewer_keywords:
- features [WCF]
- WCF, features
- Windows Communication Foundation, features
ms.assetid: 9b4368ca-0bd3-40dc-a539-bcd5779cee5f
ms.openlocfilehash: c97bd891f0bbb58f8b267296b9b53e00a5486622
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047044"
---
# <a name="wcf-feature-details"></a><span data-ttu-id="e9e0e-102">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="e9e0e-102">WCF Feature Details</span></span>
<span data-ttu-id="e9e0e-103">Windows Communication Foundation (WCF) 可讓您有效掌控應用程式的訊息功能。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-103">Windows Communication Foundation (WCF) allows extensive control over the messaging functions of an application.</span></span> <span data-ttu-id="e9e0e-104">本節的主題將詳述可用的功能。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-104">The topics in this section go into detail about the available features.</span></span> <span data-ttu-id="e9e0e-105">如需有關基本程式設計的詳細資訊，請參閱 <<c0> [ 基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9e0e-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="e9e0e-106">In This Section</span></span>  
 [<span data-ttu-id="e9e0e-107">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="e9e0e-107">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 <span data-ttu-id="e9e0e-108">描述如何建立和設定工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-108">Describes how to create and configure workflow services.</span></span>  
  
 [<span data-ttu-id="e9e0e-109">端點：位址、 繫結和合約</span><span class="sxs-lookup"><span data-stu-id="e9e0e-109">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 <span data-ttu-id="e9e0e-110">描述如何控制服務的多種層面。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-110">Describes how to control multiple aspects of your service.</span></span>  
  
 [<span data-ttu-id="e9e0e-111">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="e9e0e-111">Data Transfer and Serialization</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)  
 <span data-ttu-id="e9e0e-112">說明資料的序列化如何針對互通或未來相容性而量身打造。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-112">Describes how serialization of data can be tailored for interoperation or future compatibility.</span></span>  
  
 [<span data-ttu-id="e9e0e-113">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="e9e0e-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 <span data-ttu-id="e9e0e-114">說明 WCF，以及如何選取正確的模式，您的應用程式的執行個體和工作階段模式。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-114">Describes the instancing and session modes of WCF and how to select the right mode for your application.</span></span>  
  
 [<span data-ttu-id="e9e0e-115">傳輸</span><span class="sxs-lookup"><span data-stu-id="e9e0e-115">Transports</span></span>](../../../../docs/framework/wcf/feature-details/transports.md)  
 <span data-ttu-id="e9e0e-116">說明如何設定通道堆疊的最底層：傳輸層。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-116">Describes how to configure the transport layer, the lowest level of the channel stack.</span></span>  
  
 [<span data-ttu-id="e9e0e-117">佇列和可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="e9e0e-117">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)  
 <span data-ttu-id="e9e0e-118">說明代表接收應用程式儲存來自傳送應用程式的訊息，並在稍後將這些訊息轉發給接收應用程式的佇列。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-118">Describes queues, which store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span>  
  
 [<span data-ttu-id="e9e0e-119">異動</span><span class="sxs-lookup"><span data-stu-id="e9e0e-119">Transactions</span></span>](../../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)  
 <span data-ttu-id="e9e0e-120">解釋如何建立在需要時可復原的交易作業。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-120">Explains how to create transacted operations that can be rolled back if needed.</span></span>  
  
 [<span data-ttu-id="e9e0e-121">安全性</span><span class="sxs-lookup"><span data-stu-id="e9e0e-121">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 <span data-ttu-id="e9e0e-122">說明 WCF 安全性如何協助您建立具有機密性與完整性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-122">Describes how WCF security helps you to create applications that have confidentiality and integrity.</span></span> <span data-ttu-id="e9e0e-123">驗證、授權和稽核功能皆可使用。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-123">Authentication and authorization are also available, as are auditing features.</span></span>  
  
 [<span data-ttu-id="e9e0e-124">對等網路</span><span class="sxs-lookup"><span data-stu-id="e9e0e-124">Peer-to-Peer Networking</span></span>](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 <span data-ttu-id="e9e0e-125">詳述如何建立對等式服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-125">Details how to create peer services and clients.</span></span>  
  
 [<span data-ttu-id="e9e0e-126">中繼資料</span><span class="sxs-lookup"><span data-stu-id="e9e0e-126">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 <span data-ttu-id="e9e0e-127">說明中繼資料的架構和格式。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-127">Describes metadata architecture and formats.</span></span>  
  
 [<span data-ttu-id="e9e0e-128">用戶端</span><span class="sxs-lookup"><span data-stu-id="e9e0e-128">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)  
 <span data-ttu-id="e9e0e-129">說明如何建立存取服務的各種用戶端。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-129">Describes how to create a variety of clients that access services.</span></span>  
  
 [<span data-ttu-id="e9e0e-130">裝載</span><span class="sxs-lookup"><span data-stu-id="e9e0e-130">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 <span data-ttu-id="e9e0e-131">說明裝載。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-131">Describes hosting.</span></span> <span data-ttu-id="e9e0e-132">服務可以由另一個應用程式裝載，或是自我裝載。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-132">A service can be hosted by another application, or it can be self-hosted.</span></span>  
  
 [<span data-ttu-id="e9e0e-133">互通性和整合</span><span class="sxs-lookup"><span data-stu-id="e9e0e-133">Interoperability and Integration</span></span>](../../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)  
 <span data-ttu-id="e9e0e-134">描述如何使用 WCF 來擴充現有邏輯，而不需要將它改寫，如果您已長期開發裝載於 COM + 元件為基礎的應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-134">Describes how to use WCF to extend your existing logic rather than having to rewrite it if you have a substantial investment in component-based application logic hosted in COM+.</span></span>  
  
 [<span data-ttu-id="e9e0e-135">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="e9e0e-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 <span data-ttu-id="e9e0e-136">描述可讓開發人員公開非 SOAP 端點的 WCF 服務作業的 WCF Web 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-136">Describes the WCF Web Programming Model that allows developers to expose WCF service operations to non-SOAP endpoints.</span></span>  
  
 [<span data-ttu-id="e9e0e-137">WCF 摘要整合</span><span class="sxs-lookup"><span data-stu-id="e9e0e-137">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 <span data-ttu-id="e9e0e-138">說明簡易公開新聞訂閱摘要，從 WCF 服務的支援。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-138">Describes support to easily expose syndication feeds from a WCF service.</span></span>  
  
 [<span data-ttu-id="e9e0e-139">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="e9e0e-139">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 <span data-ttu-id="e9e0e-140">描述對 ASP.NET Asynchronous JavaScript 與 XML (AJAX) 及 JavaScript Object Notation (JSON) 資料格式，讓 WCF 服務對 AJAX 用戶端公開作業。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-140">Describes support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format to allow WCF services to expose operations to AJAX clients.</span></span>  
  
 [<span data-ttu-id="e9e0e-141">WCF 探索</span><span class="sxs-lookup"><span data-stu-id="e9e0e-141">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 <span data-ttu-id="e9e0e-142">描述以互通方式使用 WS-Discovery 通訊協定讓服務可在執行階段搜尋的支援。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-142">Describes support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span>  
  
 [<span data-ttu-id="e9e0e-143">路由傳送</span><span class="sxs-lookup"><span data-stu-id="e9e0e-143">Routing</span></span>](../../../../docs/framework/wcf/feature-details/routing.md)  
 <span data-ttu-id="e9e0e-144">描述路由服務。</span><span class="sxs-lookup"><span data-stu-id="e9e0e-144">Describes the routing service.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e9e0e-145">參考資料</span><span class="sxs-lookup"><span data-stu-id="e9e0e-145">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.ServiceModel.Routing>  
  
## <a name="related-sections"></a><span data-ttu-id="e9e0e-146">相關章節</span><span class="sxs-lookup"><span data-stu-id="e9e0e-146">Related Sections</span></span>  
 [<span data-ttu-id="e9e0e-147">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="e9e0e-147">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
