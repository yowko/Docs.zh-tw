---
title: WCF 功能詳細資料
description: 深入瞭解 WCF 透過應用程式的訊息功能提供的廣泛控制項。
ms.date: 03/30/2017
helpviewer_keywords:
- features [WCF]
- WCF, features
- Windows Communication Foundation, features
ms.assetid: 9b4368ca-0bd3-40dc-a539-bcd5779cee5f
ms.openlocfilehash: 30b8acb3b89b8c28be0b8d0b4ce5a1d1d734b055
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280425"
---
# <a name="wcf-feature-details"></a><span data-ttu-id="e2355-103">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="e2355-103">WCF Feature Details</span></span>

<span data-ttu-id="e2355-104">Windows Communication Foundation (WCF) 可讓您對應用程式的訊息功能進行廣泛的控制。</span><span class="sxs-lookup"><span data-stu-id="e2355-104">Windows Communication Foundation (WCF) allows extensive control over the messaging functions of an application.</span></span> <span data-ttu-id="e2355-105">本節的主題將詳述可用的功能。</span><span class="sxs-lookup"><span data-stu-id="e2355-105">The topics in this section go into detail about the available features.</span></span> <span data-ttu-id="e2355-106">如需基本程式設計的詳細資訊，請參閱 [基本 WCF 程式設計](../basic-wcf-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="e2355-106">For more information about basic programming, see [Basic WCF Programming](../basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2355-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="e2355-107">In This Section</span></span>  

 [<span data-ttu-id="e2355-108">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="e2355-108">Workflow Services</span></span>](workflow-services.md)  
 <span data-ttu-id="e2355-109">描述如何建立和設定工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="e2355-109">Describes how to create and configure workflow services.</span></span>  
  
 [<span data-ttu-id="e2355-110">端點：位址、繫結和合約</span><span class="sxs-lookup"><span data-stu-id="e2355-110">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)  
 <span data-ttu-id="e2355-111">描述如何控制服務的多種層面。</span><span class="sxs-lookup"><span data-stu-id="e2355-111">Describes how to control multiple aspects of your service.</span></span>  
  
 [<span data-ttu-id="e2355-112">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="e2355-112">Data Transfer and Serialization</span></span>](data-transfer-and-serialization.md)  
 <span data-ttu-id="e2355-113">說明資料的序列化如何針對互通或未來相容性而量身打造。</span><span class="sxs-lookup"><span data-stu-id="e2355-113">Describes how serialization of data can be tailored for interoperation or future compatibility.</span></span>  
  
 [<span data-ttu-id="e2355-114">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="e2355-114">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)  
 <span data-ttu-id="e2355-115">描述 WCF 的實例和會話模式，以及如何為您的應用程式選取正確的模式。</span><span class="sxs-lookup"><span data-stu-id="e2355-115">Describes the instancing and session modes of WCF and how to select the right mode for your application.</span></span>  
  
 [<span data-ttu-id="e2355-116">傳輸</span><span class="sxs-lookup"><span data-stu-id="e2355-116">Transports</span></span>](transports.md)  
 <span data-ttu-id="e2355-117">說明如何設定通道堆疊的最底層：傳輸層。</span><span class="sxs-lookup"><span data-stu-id="e2355-117">Describes how to configure the transport layer, the lowest level of the channel stack.</span></span>  
  
 [<span data-ttu-id="e2355-118">佇列和可靠的工作階段</span><span class="sxs-lookup"><span data-stu-id="e2355-118">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)  
 <span data-ttu-id="e2355-119">說明代表接收應用程式儲存來自傳送應用程式的訊息，並在稍後將這些訊息轉發給接收應用程式的佇列。</span><span class="sxs-lookup"><span data-stu-id="e2355-119">Describes queues, which store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span>  
  
 [<span data-ttu-id="e2355-120">交易</span><span class="sxs-lookup"><span data-stu-id="e2355-120">Transactions</span></span>](transactions-in-wcf.md)  
 <span data-ttu-id="e2355-121">解釋如何建立在需要時可復原的交易作業。</span><span class="sxs-lookup"><span data-stu-id="e2355-121">Explains how to create transacted operations that can be rolled back if needed.</span></span>  
  
 [<span data-ttu-id="e2355-122">安全性</span><span class="sxs-lookup"><span data-stu-id="e2355-122">Security</span></span>](security.md)  
 <span data-ttu-id="e2355-123">描述 WCF 安全性如何協助您建立具有機密性和完整性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e2355-123">Describes how WCF security helps you to create applications that have confidentiality and integrity.</span></span> <span data-ttu-id="e2355-124">驗證、授權和稽核功能皆可使用。</span><span class="sxs-lookup"><span data-stu-id="e2355-124">Authentication and authorization are also available, as are auditing features.</span></span>  
  
 [<span data-ttu-id="e2355-125">對等網路</span><span class="sxs-lookup"><span data-stu-id="e2355-125">Peer-to-Peer Networking</span></span>](peer-to-peer-networking.md)  
 <span data-ttu-id="e2355-126">詳述如何建立對等式服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2355-126">Details how to create peer services and clients.</span></span>  
  
 [<span data-ttu-id="e2355-127">中繼資料</span><span class="sxs-lookup"><span data-stu-id="e2355-127">Metadata</span></span>](metadata.md)  
 <span data-ttu-id="e2355-128">說明中繼資料的架構和格式。</span><span class="sxs-lookup"><span data-stu-id="e2355-128">Describes metadata architecture and formats.</span></span>  
  
 [<span data-ttu-id="e2355-129">用戶端</span><span class="sxs-lookup"><span data-stu-id="e2355-129">Clients</span></span>](clients.md)  
 <span data-ttu-id="e2355-130">說明如何建立存取服務的各種用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2355-130">Describes how to create a variety of clients that access services.</span></span>  
  
 [<span data-ttu-id="e2355-131">裝載</span><span class="sxs-lookup"><span data-stu-id="e2355-131">Hosting</span></span>](hosting.md)  
 <span data-ttu-id="e2355-132">說明裝載。</span><span class="sxs-lookup"><span data-stu-id="e2355-132">Describes hosting.</span></span> <span data-ttu-id="e2355-133">服務可以由另一個應用程式裝載，或是自我裝載。</span><span class="sxs-lookup"><span data-stu-id="e2355-133">A service can be hosted by another application, or it can be self-hosted.</span></span>  
  
 [<span data-ttu-id="e2355-134">互通性與整合</span><span class="sxs-lookup"><span data-stu-id="e2355-134">Interoperability and Integration</span></span>](interoperability-and-integration.md)  
 <span data-ttu-id="e2355-135">描述如何使用 WCF 擴充您現有的邏輯，而不需要在 COM + 中裝載以元件為基礎的應用程式邏輯進行大量投資時，才需要加以重寫。</span><span class="sxs-lookup"><span data-stu-id="e2355-135">Describes how to use WCF to extend your existing logic rather than having to rewrite it if you have a substantial investment in component-based application logic hosted in COM+.</span></span>  
  
 [<span data-ttu-id="e2355-136">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="e2355-136">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)  
 <span data-ttu-id="e2355-137">描述可讓開發人員將 WCF 服務作業公開至非 SOAP 端點的 WCF Web 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="e2355-137">Describes the WCF Web Programming Model that allows developers to expose WCF service operations to non-SOAP endpoints.</span></span>  
  
 [<span data-ttu-id="e2355-138">WCF 新聞訂閱</span><span class="sxs-lookup"><span data-stu-id="e2355-138">WCF Syndication</span></span>](wcf-syndication.md)  
 <span data-ttu-id="e2355-139">描述可輕鬆地從 WCF 服務公開新聞訂閱摘要的支援。</span><span class="sxs-lookup"><span data-stu-id="e2355-139">Describes support to easily expose syndication feeds from a WCF service.</span></span>  
  
 [<span data-ttu-id="e2355-140">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="e2355-140">AJAX Integration and JSON Support</span></span>](ajax-integration-and-json-support.md)  
 <span data-ttu-id="e2355-141">描述支援 ASP.NET 非同步 JavaScript 和 XML (AJAX) 和 JavaScript 物件標記法 (JSON) 資料格式，以允許 WCF 服務對 AJAX 用戶端公開作業。</span><span class="sxs-lookup"><span data-stu-id="e2355-141">Describes support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format to allow WCF services to expose operations to AJAX clients.</span></span>  
  
 [<span data-ttu-id="e2355-142">WCF 探索</span><span class="sxs-lookup"><span data-stu-id="e2355-142">WCF Discovery</span></span>](wcf-discovery.md)  
 <span data-ttu-id="e2355-143">描述以互通方式使用 WS-Discovery 通訊協定讓服務可在執行階段搜尋的支援。</span><span class="sxs-lookup"><span data-stu-id="e2355-143">Describes support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span>  
  
 [<span data-ttu-id="e2355-144">路由</span><span class="sxs-lookup"><span data-stu-id="e2355-144">Routing</span></span>](routing.md)  
 <span data-ttu-id="e2355-145">描述路由服務。</span><span class="sxs-lookup"><span data-stu-id="e2355-145">Describes the routing service.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e2355-146">參考</span><span class="sxs-lookup"><span data-stu-id="e2355-146">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.ServiceModel.Routing>  
  
## <a name="related-sections"></a><span data-ttu-id="e2355-147">相關章節</span><span class="sxs-lookup"><span data-stu-id="e2355-147">Related Sections</span></span>  

 [<span data-ttu-id="e2355-148">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="e2355-148">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
