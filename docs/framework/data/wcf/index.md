---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 9ece2fe051855d0fd39556f56a4343ead2c437bc
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46482127"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="65e0c-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="65e0c-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="65e0c-103">WCF Data Services （先前稱為"ADO.NET Data Services"） 是可讓您建立使用服務的.NET framework 的元件[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]來公開及取用資料透過 Web 或內部網路使用的語意[具像狀態傳輸 (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)。</span><span class="sxs-lookup"><span data-stu-id="65e0c-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="65e0c-104">OData 會將資料公開為可由 URI 定址的資源。</span><span class="sxs-lookup"><span data-stu-id="65e0c-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="65e0c-105">資料是使用 GET、PUT、POST 和 DELETE 的標準 HTTP 動作來存取及變更。</span><span class="sxs-lookup"><span data-stu-id="65e0c-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="65e0c-106">OData 會使用的實體-關聯性慣例[Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)將資源公開為依關聯性相關的實體集。</span><span class="sxs-lookup"><span data-stu-id="65e0c-106">OData uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="65e0c-107">WCF Data Services 會使用 OData 通訊協定來定址及更新資源。</span><span class="sxs-lookup"><span data-stu-id="65e0c-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="65e0c-108">如此一來，您可以從任何支援 OData 的用戶端存取這些服務。</span><span class="sxs-lookup"><span data-stu-id="65e0c-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="65e0c-109">OData 可讓您要求，並使用已知的傳輸格式將資料寫入資源： Atom，一組交換及更新資料的 XML，以及 JavaScript Object Notation (JSON) 的標準 AJAX 中廣泛使用的文字型資料交換格式應用程式。</span><span class="sxs-lookup"><span data-stu-id="65e0c-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>

<span data-ttu-id="65e0c-110">WCF 資料服務可以公開為 OData 摘要，來自不同來源的資料。</span><span class="sxs-lookup"><span data-stu-id="65e0c-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="65e0c-111">Visual Studio tools 可讓您更輕鬆地使用 ADO.NET Entity Framework 資料模型建立 OData 為基礎的服務。</span><span class="sxs-lookup"><span data-stu-id="65e0c-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="65e0c-112">您也可以建立根據 common language runtime (CLR) 類別以及甚至是晚期繫結或不具類型資料的 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="65e0c-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="65e0c-113">WCF Data Services 也包含一組用戶端程式庫，一個用於一般.NET Framework 用戶端應用程式，另一個專門針對以 Silverlight 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="65e0c-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="65e0c-114">當您存取 OData 摘要的.NET Framework 和 Silverlight 等環境中時，這些用戶端程式庫會提供以物件為基礎的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="65e0c-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="65e0c-115">我該從哪裡開始？</span><span class="sxs-lookup"><span data-stu-id="65e0c-115">Where Should I Start?</span></span>

<span data-ttu-id="65e0c-116">根據您感興趣，請考慮開始使用 WCF Data Services 中的下列主題之一。</span><span class="sxs-lookup"><span data-stu-id="65e0c-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="65e0c-117">我想直接開始</span><span class="sxs-lookup"><span data-stu-id="65e0c-117">I want to jump right in...</span></span>

-   [<span data-ttu-id="65e0c-118">快速入門</span><span class="sxs-lookup"><span data-stu-id="65e0c-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [<span data-ttu-id="65e0c-119">快速入門</span><span class="sxs-lookup"><span data-stu-id="65e0c-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

-   [<span data-ttu-id="65e0c-120">Silverlight 快速入門</span><span class="sxs-lookup"><span data-stu-id="65e0c-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [<span data-ttu-id="65e0c-121">適用於 Windows Phone 開發的 Silverlight 快速入門</span><span class="sxs-lookup"><span data-stu-id="65e0c-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="65e0c-122">我只想查看某些程式碼...</span><span class="sxs-lookup"><span data-stu-id="65e0c-122">Just show me some code...</span></span>

-   [<span data-ttu-id="65e0c-123">快速入門</span><span class="sxs-lookup"><span data-stu-id="65e0c-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [<span data-ttu-id="65e0c-124">如何：執行資料服務查詢</span><span class="sxs-lookup"><span data-stu-id="65e0c-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

-   [<span data-ttu-id="65e0c-125">如何：將資料繫結至 Windows Presentation Foundation 項目</span><span class="sxs-lookup"><span data-stu-id="65e0c-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="65e0c-126">我想要深入了解 OData...</span><span class="sxs-lookup"><span data-stu-id="65e0c-126">I want to know more about OData...</span></span>

 -   [<span data-ttu-id="65e0c-127">白皮書：OData 簡介</span><span class="sxs-lookup"><span data-stu-id="65e0c-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [<span data-ttu-id="65e0c-128">開放式資料通訊協定網站</span><span class="sxs-lookup"><span data-stu-id="65e0c-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

-   [<span data-ttu-id="65e0c-129">OData：SDK</span><span class="sxs-lookup"><span data-stu-id="65e0c-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

-   [<span data-ttu-id="65e0c-130">OData：常見問題集</span><span class="sxs-lookup"><span data-stu-id="65e0c-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="65e0c-131">我想觀看某些影片...</span><span class="sxs-lookup"><span data-stu-id="65e0c-131">I want to watch some videos...</span></span>

-   [<span data-ttu-id="65e0c-132">WCF Data Services 初學者指南</span><span class="sxs-lookup"><span data-stu-id="65e0c-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

-   [<span data-ttu-id="65e0c-133">WCF Data Services 開發人員視訊</span><span class="sxs-lookup"><span data-stu-id="65e0c-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

-   [<span data-ttu-id="65e0c-134">OData：開發人員網站</span><span class="sxs-lookup"><span data-stu-id="65e0c-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="65e0c-135">我想要查看端對端範例...</span><span class="sxs-lookup"><span data-stu-id="65e0c-135">I want to see end-to-end samples...</span></span>

-   [<span data-ttu-id="65e0c-136">MSDN 範例庫上的 WCF Data Services 文件範例</span><span class="sxs-lookup"><span data-stu-id="65e0c-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

-   [<span data-ttu-id="65e0c-137">MSDN 範例庫上的其他 WCF Data Services 範例</span><span class="sxs-lookup"><span data-stu-id="65e0c-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

-   [<span data-ttu-id="65e0c-138">OData：SDK</span><span class="sxs-lookup"><span data-stu-id="65e0c-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="65e0c-139">如何與 Visual Studio 整合？</span><span class="sxs-lookup"><span data-stu-id="65e0c-139">How does it integrate with Visual Studio?</span></span>

-   [<span data-ttu-id="65e0c-140">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="65e0c-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

-   [<span data-ttu-id="65e0c-141">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="65e0c-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

-   [<span data-ttu-id="65e0c-142">Entity Framework 提供者</span><span class="sxs-lookup"><span data-stu-id="65e0c-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="65e0c-143">可使用哪些功能？</span><span class="sxs-lookup"><span data-stu-id="65e0c-143">What can I do with it?</span></span>

-   [<span data-ttu-id="65e0c-144">概觀</span><span class="sxs-lookup"><span data-stu-id="65e0c-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

-   [<span data-ttu-id="65e0c-145">白皮書：OData 簡介</span><span class="sxs-lookup"><span data-stu-id="65e0c-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [<span data-ttu-id="65e0c-146">應用程式案例</span><span class="sxs-lookup"><span data-stu-id="65e0c-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

<span data-ttu-id="65e0c-147">我想要使用 Silverlight...</span><span class="sxs-lookup"><span data-stu-id="65e0c-147">I want to use Silverlight...</span></span>

-   [<span data-ttu-id="65e0c-148">Silverlight 快速入門</span><span class="sxs-lookup"><span data-stu-id="65e0c-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [<span data-ttu-id="65e0c-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="65e0c-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

-   [<span data-ttu-id="65e0c-150">Silverlight 使用者入門</span><span class="sxs-lookup"><span data-stu-id="65e0c-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="65e0c-151">我想要使用 LINQ...</span><span class="sxs-lookup"><span data-stu-id="65e0c-151">I want to use LINQ...</span></span>

-   [<span data-ttu-id="65e0c-152">查詢資料服務</span><span class="sxs-lookup"><span data-stu-id="65e0c-152">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

-   [<span data-ttu-id="65e0c-153">LINQ 考量</span><span class="sxs-lookup"><span data-stu-id="65e0c-153">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

-   [<span data-ttu-id="65e0c-154">如何：執行資料服務查詢</span><span class="sxs-lookup"><span data-stu-id="65e0c-154">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="65e0c-155">我仍然需要一些詳細資訊...</span><span class="sxs-lookup"><span data-stu-id="65e0c-155">I still need some more information...</span></span>

-   [<span data-ttu-id="65e0c-156">WCF Data Services 小組部落格</span><span class="sxs-lookup"><span data-stu-id="65e0c-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

-   [<span data-ttu-id="65e0c-157">資源</span><span class="sxs-lookup"><span data-stu-id="65e0c-157">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

-   [<span data-ttu-id="65e0c-158">WCF Data Services 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="65e0c-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

-   [<span data-ttu-id="65e0c-159">開放式資料通訊協定網站</span><span class="sxs-lookup"><span data-stu-id="65e0c-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="65e0c-160">本節內容</span><span class="sxs-lookup"><span data-stu-id="65e0c-160">In This Section</span></span>

 [<span data-ttu-id="65e0c-161">概觀</span><span class="sxs-lookup"><span data-stu-id="65e0c-161">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

 <span data-ttu-id="65e0c-162">提供的功能和 WCF Data Services 中可用功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="65e0c-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

 [<span data-ttu-id="65e0c-163">WCF Data Services 的新功能</span><span class="sxs-lookup"><span data-stu-id="65e0c-163">What's New in WCF Data Services</span></span>](https://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)

 <span data-ttu-id="65e0c-164">描述 WCF Data Services 與支援中的 OData 的新功能的新功能。</span><span class="sxs-lookup"><span data-stu-id="65e0c-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

 [<span data-ttu-id="65e0c-165">快速入門</span><span class="sxs-lookup"><span data-stu-id="65e0c-165">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

 <span data-ttu-id="65e0c-166">描述如何公開及取用 OData 摘要使用 WCF Data Services。</span><span class="sxs-lookup"><span data-stu-id="65e0c-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

 [<span data-ttu-id="65e0c-167">定義 WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="65e0c-167">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

 <span data-ttu-id="65e0c-168">描述如何建立和設定資料服務公開 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="65e0c-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

 [<span data-ttu-id="65e0c-169">WCF Data Services 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="65e0c-169">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

 <span data-ttu-id="65e0c-170">描述如何使用用戶端程式庫來取用 OData 摘要，從.NET Framework 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="65e0c-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="65e0c-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65e0c-171">See Also</span></span>

- <span data-ttu-id="65e0c-172">[Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919) (具像狀態傳輸 (REST))</span><span class="sxs-lookup"><span data-stu-id="65e0c-172">[Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)</span></span>
