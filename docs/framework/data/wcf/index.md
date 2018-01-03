---
title: WCF Data Services 4.5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b6b9ddd27422c09f21833548634afd7945afa89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="acd6f-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="acd6f-102">WCF Data Services 4.5</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="acd6f-103"> (之前稱為 "ADO.NET Data Services") 是 .NET Framework 的一個元件，可讓您建立使用[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]的服務來透過 Web 或內部網路公開及取用資料，其方式是使用[具像狀態傳輸 (REST)](http://go.microsoft.com/fwlink/?LinkId=113919) 的語意。</span><span class="sxs-lookup"><span data-stu-id="acd6f-103"> (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919).</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="acd6f-104"> 會將資料公開為可由 URI 定址的資源。</span><span class="sxs-lookup"><span data-stu-id="acd6f-104"> exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="acd6f-105">資料是使用 GET、PUT、POST 和 DELETE 的標準 HTTP 動作來存取及變更。</span><span class="sxs-lookup"><span data-stu-id="acd6f-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="acd6f-106"> 會運用[實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)的實體關聯慣例，將資源公開為依關聯性相關的實體集。</span><span class="sxs-lookup"><span data-stu-id="acd6f-106"> uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="acd6f-107"> 會使用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定來定址及更新資源。</span><span class="sxs-lookup"><span data-stu-id="acd6f-107"> uses the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol for addressing and updating resources.</span></span> <span data-ttu-id="acd6f-108">您可以透過這個方式來從任何支援 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 的用戶端存取這些服務。</span><span class="sxs-lookup"><span data-stu-id="acd6f-108">In this way, you can access these services from any client that supports [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="acd6f-109"> 可讓您使用以下知名的傳輸格式來要求資料，並將其寫入至資源：Atom (以 XML 格式交換與更新資料的一組標準) 以及 JavaScript 物件標記法 (JSON) (在 AJAX 應用程式中廣泛使用的文字型資料交換格式)。</span><span class="sxs-lookup"><span data-stu-id="acd6f-109"> enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="acd6f-110"> 可將來自各種不同來源的資料公開為 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。</span><span class="sxs-lookup"><span data-stu-id="acd6f-110"> can expose data that originates from various sources as [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span> <span data-ttu-id="acd6f-111">Visual Studio 工具可讓您輕鬆地建立以 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 為基礎的服務，其方式是使用 ADO.NET Entity Framework 資料模型。</span><span class="sxs-lookup"><span data-stu-id="acd6f-111">Visual Studio tools make it easier for you to create an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="acd6f-112">您也可以根據 Common Language Runtime (CLR) 類別以及甚至是晚期繫結或不具類型的資料來建立 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。</span><span class="sxs-lookup"><span data-stu-id="acd6f-112">You can also create [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="acd6f-113"> 也包含用戶端程式庫集，其中一個程式庫適用於一般 .NET Framework 用戶端應用程式，而另一個則是針對以 Silverlight 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="acd6f-113"> also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="acd6f-114">當您從類似 .NET Framework 和 Silverlight 等環境存取 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要時，這些用戶端程式庫可提供以物件為基礎的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="acd6f-114">These client libraries provide an object-based programming model when you access an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from environments such as the .NET Framework and Silverlight.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="acd6f-115">我該從哪裡開始？</span><span class="sxs-lookup"><span data-stu-id="acd6f-115">Where Should I Start?</span></span>  
 <span data-ttu-id="acd6f-116">視您最感興趣的項目而定，您可以考慮從下列其中一個主題開始學習 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="acd6f-116">Depending on your interests, consider getting started with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] in one of the following topics.</span></span>  
  
 <span data-ttu-id="acd6f-117">我想直接開始</span><span class="sxs-lookup"><span data-stu-id="acd6f-117">I want to jump right in…</span></span>  
 -   [<span data-ttu-id="acd6f-118">快速入門</span><span class="sxs-lookup"><span data-stu-id="acd6f-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="acd6f-119">快速入門</span><span class="sxs-lookup"><span data-stu-id="acd6f-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [<span data-ttu-id="acd6f-120">Silverlight 快速入門</span><span class="sxs-lookup"><span data-stu-id="acd6f-120">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="acd6f-121">適用於 Windows Phone 開發的 Silverlight 快速入門</span><span class="sxs-lookup"><span data-stu-id="acd6f-121">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 <span data-ttu-id="acd6f-122">我只想查看某些程式碼</span><span class="sxs-lookup"><span data-stu-id="acd6f-122">Just show me some code…</span></span>  
 -   [<span data-ttu-id="acd6f-123">快速入門</span><span class="sxs-lookup"><span data-stu-id="acd6f-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="acd6f-124">如何：執行資料服務查詢</span><span class="sxs-lookup"><span data-stu-id="acd6f-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [<span data-ttu-id="acd6f-125">如何：將資料繫結至 Windows Presentation Foundation 項目</span><span class="sxs-lookup"><span data-stu-id="acd6f-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 <span data-ttu-id="acd6f-126">我想要進一步了解 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acd6f-126">I want to know more about [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]…</span></span>  
 -   [<span data-ttu-id="acd6f-127">白皮書：OData 簡介</span><span class="sxs-lookup"><span data-stu-id="acd6f-127">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="acd6f-128">開放式資料通訊協定網站</span><span class="sxs-lookup"><span data-stu-id="acd6f-128">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [<span data-ttu-id="acd6f-129">OData：SDK</span><span class="sxs-lookup"><span data-stu-id="acd6f-129">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [<span data-ttu-id="acd6f-130">OData：常見問題集</span><span class="sxs-lookup"><span data-stu-id="acd6f-130">OData: Frequently Asked Questions</span></span>](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 <span data-ttu-id="acd6f-131">我想觀看某些影片</span><span class="sxs-lookup"><span data-stu-id="acd6f-131">I want to watch some videos…</span></span>  
 -   [<span data-ttu-id="acd6f-132">WCF Data Services 初學者指南</span><span class="sxs-lookup"><span data-stu-id="acd6f-132">Beginner's Guide to WCF Data Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [<span data-ttu-id="acd6f-133">WCF Data Services 開發人員視訊</span><span class="sxs-lookup"><span data-stu-id="acd6f-133">WCF Data Services Developer Videos</span></span>](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [<span data-ttu-id="acd6f-134">OData：開發人員網站</span><span class="sxs-lookup"><span data-stu-id="acd6f-134">OData: Developers Web site</span></span>](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 <span data-ttu-id="acd6f-135">我想要查看端對端的範例程式</span><span class="sxs-lookup"><span data-stu-id="acd6f-135">I want to see end-to-end samples</span></span>  
 -   [<span data-ttu-id="acd6f-136">MSDN 範例庫上的 WCF Data Services 文件範例</span><span class="sxs-lookup"><span data-stu-id="acd6f-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [<span data-ttu-id="acd6f-137">MSDN 範例庫上的其他 WCF Data Services 範例</span><span class="sxs-lookup"><span data-stu-id="acd6f-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [<span data-ttu-id="acd6f-138">OData：SDK</span><span class="sxs-lookup"><span data-stu-id="acd6f-138">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 <span data-ttu-id="acd6f-139">如何與 Visual Studio 整合？</span><span class="sxs-lookup"><span data-stu-id="acd6f-139">How does it integrate with Visual Studio?</span></span>  
 -   [<span data-ttu-id="acd6f-140">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="acd6f-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [<span data-ttu-id="acd6f-141">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="acd6f-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [<span data-ttu-id="acd6f-142">Entity Framework 提供者</span><span class="sxs-lookup"><span data-stu-id="acd6f-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 <span data-ttu-id="acd6f-143">可使用哪些功能？</span><span class="sxs-lookup"><span data-stu-id="acd6f-143">What can I do with it?</span></span>  
 -   [<span data-ttu-id="acd6f-144">概觀</span><span class="sxs-lookup"><span data-stu-id="acd6f-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [<span data-ttu-id="acd6f-145">白皮書：OData 簡介</span><span class="sxs-lookup"><span data-stu-id="acd6f-145">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="acd6f-146">應用程式案例</span><span class="sxs-lookup"><span data-stu-id="acd6f-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 <span data-ttu-id="acd6f-147">我想使用 Silverlight</span><span class="sxs-lookup"><span data-stu-id="acd6f-147">I want to use Silverlight…</span></span>  
 -   [<span data-ttu-id="acd6f-148">Silverlight 快速入門</span><span class="sxs-lookup"><span data-stu-id="acd6f-148">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="acd6f-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="acd6f-149">WCF Data Services (Silverlight)</span></span>](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [<span data-ttu-id="acd6f-150">Silverlight 使用者入門</span><span class="sxs-lookup"><span data-stu-id="acd6f-150">Getting Started with Silverlight</span></span>](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 <span data-ttu-id="acd6f-151">我想建立 Windows Phone 應用程式…</span><span class="sxs-lookup"><span data-stu-id="acd6f-151">I want to create a Windows Phone application…</span></span>  
 -   [<span data-ttu-id="acd6f-152">適用於 Windows Phone 開發的 Silverlight 快速入門</span><span class="sxs-lookup"><span data-stu-id="acd6f-152">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [<span data-ttu-id="acd6f-153">適用於 Windows Phone 的開放式資料通訊協定 (OData) 用戶端</span><span class="sxs-lookup"><span data-stu-id="acd6f-153">Open Data Protocol (OData) Client for Windows Phone</span></span>](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 <span data-ttu-id="acd6f-154">我想使用 LINQ</span><span class="sxs-lookup"><span data-stu-id="acd6f-154">I want to use LINQ…</span></span>  
 -   [<span data-ttu-id="acd6f-155">查詢資料服務</span><span class="sxs-lookup"><span data-stu-id="acd6f-155">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [<span data-ttu-id="acd6f-156">LINQ 考量</span><span class="sxs-lookup"><span data-stu-id="acd6f-156">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [<span data-ttu-id="acd6f-157">如何：執行資料服務查詢</span><span class="sxs-lookup"><span data-stu-id="acd6f-157">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 <span data-ttu-id="acd6f-158">我仍然需要一些詳細資訊</span><span class="sxs-lookup"><span data-stu-id="acd6f-158">I still need some more information…</span></span>  
 -   [<span data-ttu-id="acd6f-159">WCF Data Services 小組部落格</span><span class="sxs-lookup"><span data-stu-id="acd6f-159">WCF Data Services Team Blog</span></span>](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [<span data-ttu-id="acd6f-160">資源</span><span class="sxs-lookup"><span data-stu-id="acd6f-160">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [<span data-ttu-id="acd6f-161">WCF Data Services 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="acd6f-161">WCF Data Services Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [<span data-ttu-id="acd6f-162">開放式資料通訊協定網站</span><span class="sxs-lookup"><span data-stu-id="acd6f-162">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a><span data-ttu-id="acd6f-163">本節內容</span><span class="sxs-lookup"><span data-stu-id="acd6f-163">In This Section</span></span>  
 [<span data-ttu-id="acd6f-164">概觀</span><span class="sxs-lookup"><span data-stu-id="acd6f-164">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 <span data-ttu-id="acd6f-165">提供 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中可取得之特性與功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="acd6f-165">Provides an overview of the features and functionality available in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="acd6f-166">WCF Data Services 的新功能</span><span class="sxs-lookup"><span data-stu-id="acd6f-166">What's New in WCF Data Services</span></span>](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 <span data-ttu-id="acd6f-167">描述 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 的新功能以及新 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 功能的支援。</span><span class="sxs-lookup"><span data-stu-id="acd6f-167">Describes new functionality in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and support for new [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] features.</span></span>  
  
 [<span data-ttu-id="acd6f-168">快速入門</span><span class="sxs-lookup"><span data-stu-id="acd6f-168">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 <span data-ttu-id="acd6f-169">描述如何使用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 來公開及取用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 摘要。</span><span class="sxs-lookup"><span data-stu-id="acd6f-169">Describes how to expose and consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds by using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="acd6f-170">定義 WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="acd6f-170">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 <span data-ttu-id="acd6f-171">描述如何建立及設定可公開 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的資料服務。</span><span class="sxs-lookup"><span data-stu-id="acd6f-171">Describes how to create and configure a data service that exposes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 [<span data-ttu-id="acd6f-172">WCF Data Services 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="acd6f-172">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 <span data-ttu-id="acd6f-173">描述如何使用用戶端程式庫，從 .NET Framework 用戶端應用程式取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。</span><span class="sxs-lookup"><span data-stu-id="acd6f-173">Describes how to use client libraries to consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from a .NET Framework client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd6f-174">請參閱</span><span class="sxs-lookup"><span data-stu-id="acd6f-174">See Also</span></span>  
 <span data-ttu-id="acd6f-175">[Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919) (具像狀態傳輸 (REST))</span><span class="sxs-lookup"><span data-stu-id="acd6f-175">[Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919)</span></span>
