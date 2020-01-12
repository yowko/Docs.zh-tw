---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 890f0ba25d8320008228c73660753b9899269fd7
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900993"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="884f8-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="884f8-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="884f8-103">WCF Data Services （之前稱為 "ADO.NET 資料服務"）是 .NET Framework 的元件，可讓您建立使用開放式資料通訊協定（OData）的服務，利用[具像狀態傳輸（REST）](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)的語義，透過 Web 或內部網路公開及取用資料。</span><span class="sxs-lookup"><span data-stu-id="884f8-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="884f8-104">OData 會將資料公開為可由 URI 定址的資源。</span><span class="sxs-lookup"><span data-stu-id="884f8-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="884f8-105">資料的存取和變更方式是使用 GET、PUT、POST 和 DELETE 等標準 HTTP 動詞。</span><span class="sxs-lookup"><span data-stu-id="884f8-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="884f8-106">OData 會使用[實體資料模型](../adonet/entity-data-model.md)的實體關聯性慣例，將資源公開為與關聯相關的實體集。</span><span class="sxs-lookup"><span data-stu-id="884f8-106">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="884f8-107">WCF Data Services 使用 OData 通訊協定來定址及更新資源。</span><span class="sxs-lookup"><span data-stu-id="884f8-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="884f8-108">如此一來，您就可以從任何支援 OData 的用戶端存取這些服務。</span><span class="sxs-lookup"><span data-stu-id="884f8-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="884f8-109">OData 可讓您使用已知的傳輸格式來要求和寫入資源： Atom （一組以 XML 形式交換和更新資料的標準），以及 JavaScript 物件標記法（JSON），這是在 AJAX 中廣泛使用的文字型資料交換格式應用程式.</span><span class="sxs-lookup"><span data-stu-id="884f8-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="884f8-110">WCF Data Services 可以將源自各種來源的資料公開為 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="884f8-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="884f8-111">Visual Studio 工具可讓您使用 ADO.NET Entity Framework 資料模型，更輕鬆地建立以 OData 為基礎的服務。</span><span class="sxs-lookup"><span data-stu-id="884f8-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="884f8-112">您也可以根據 common language runtime （CLR）類別，甚至是晚期繫結或不具類型的資料來建立 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="884f8-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="884f8-113">WCF Data Services 也包含一組用戶端程式庫，一個用於一般 .NET Framework 用戶端應用程式，另一個則特別針對 Silverlight 應用程式。</span><span class="sxs-lookup"><span data-stu-id="884f8-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="884f8-114">當您從 .NET Framework 和 Silverlight 等環境存取 OData 摘要時，這些用戶端程式庫可提供以物件為基礎的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="884f8-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="884f8-115">我該從哪裡開始？</span><span class="sxs-lookup"><span data-stu-id="884f8-115">Where Should I Start?</span></span>

<span data-ttu-id="884f8-116">根據您的興趣而定，請考慮在下列其中一個主題中開始使用 WCF Data Services。</span><span class="sxs-lookup"><span data-stu-id="884f8-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="884f8-117">我想直接開始</span><span class="sxs-lookup"><span data-stu-id="884f8-117">I want to jump right in...</span></span>

- [<span data-ttu-id="884f8-118">快速入門</span><span class="sxs-lookup"><span data-stu-id="884f8-118">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="884f8-119">使用者入門</span><span class="sxs-lookup"><span data-stu-id="884f8-119">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="884f8-120">只顯示一些程式碼 。</span><span class="sxs-lookup"><span data-stu-id="884f8-120">Just show me some code...</span></span>

- [<span data-ttu-id="884f8-121">快速入門</span><span class="sxs-lookup"><span data-stu-id="884f8-121">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="884f8-122">如何：執行資料服務查詢</span><span class="sxs-lookup"><span data-stu-id="884f8-122">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="884f8-123">如何：將資料繫結至 Windows Presentation Foundation 項目</span><span class="sxs-lookup"><span data-stu-id="884f8-123">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="884f8-124">我想要深入瞭解 OData 。</span><span class="sxs-lookup"><span data-stu-id="884f8-124">I want to know more about OData...</span></span>

- [<span data-ttu-id="884f8-125">白皮書：OData 簡介</span><span class="sxs-lookup"><span data-stu-id="884f8-125">Whitepaper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="884f8-126">開放式資料通訊協定網站</span><span class="sxs-lookup"><span data-stu-id="884f8-126">Open Data Protocol Web site</span></span>](https://www.odata.org/)
- [<span data-ttu-id="884f8-127">OData：SDK</span><span class="sxs-lookup"><span data-stu-id="884f8-127">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="884f8-128">我想要查看端對端範例 。</span><span class="sxs-lookup"><span data-stu-id="884f8-128">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="884f8-129">[WCF Data Services 快速入門](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="884f8-129">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="884f8-130">OData SDK-範例程式碼</span><span class="sxs-lookup"><span data-stu-id="884f8-130">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="884f8-131">如何與 Visual Studio 整合？</span><span class="sxs-lookup"><span data-stu-id="884f8-131">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="884f8-132">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="884f8-132">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="884f8-133">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="884f8-133">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="884f8-134">Entity Framework 提供者</span><span class="sxs-lookup"><span data-stu-id="884f8-134">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="884f8-135">可使用哪些功能？</span><span class="sxs-lookup"><span data-stu-id="884f8-135">What can I do with it?</span></span>

- [<span data-ttu-id="884f8-136">概觀</span><span class="sxs-lookup"><span data-stu-id="884f8-136">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="884f8-137">應用程式案例</span><span class="sxs-lookup"><span data-stu-id="884f8-137">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="884f8-138">我想要使用 LINQ 。</span><span class="sxs-lookup"><span data-stu-id="884f8-138">I want to use LINQ...</span></span>

- [<span data-ttu-id="884f8-139">查詢資料服務</span><span class="sxs-lookup"><span data-stu-id="884f8-139">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="884f8-140">LINQ 考量</span><span class="sxs-lookup"><span data-stu-id="884f8-140">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="884f8-141">如何：執行資料服務查詢</span><span class="sxs-lookup"><span data-stu-id="884f8-141">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="884f8-142">我還需要一些其他資訊 。</span><span class="sxs-lookup"><span data-stu-id="884f8-142">I still need some more information...</span></span>

- [<span data-ttu-id="884f8-143">WCF Data Services 小組部落格</span><span class="sxs-lookup"><span data-stu-id="884f8-143">WCF Data Services Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [<span data-ttu-id="884f8-144">資源</span><span class="sxs-lookup"><span data-stu-id="884f8-144">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="884f8-145">本章節內容</span><span class="sxs-lookup"><span data-stu-id="884f8-145">In This Section</span></span>

[<span data-ttu-id="884f8-146">概觀</span><span class="sxs-lookup"><span data-stu-id="884f8-146">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="884f8-147">提供 WCF Data Services 中可用的特性和功能的總覽。</span><span class="sxs-lookup"><span data-stu-id="884f8-147">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="884f8-148">[5.0 WCF Data Services 的新功能](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="884f8-148">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="884f8-149">描述 WCF Data Services 中的新功能，以及新 OData 功能的支援。</span><span class="sxs-lookup"><span data-stu-id="884f8-149">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="884f8-150">使用者入門</span><span class="sxs-lookup"><span data-stu-id="884f8-150">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="884f8-151">描述如何使用 WCF Data Services 公開和取用 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="884f8-151">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="884f8-152">定義 WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="884f8-152">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="884f8-153">描述如何建立和設定會公開 OData 摘要的資料服務。</span><span class="sxs-lookup"><span data-stu-id="884f8-153">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="884f8-154">WCF Data Services 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="884f8-154">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="884f8-155">描述如何使用用戶端程式庫，從 .NET Framework 用戶端應用程式取用 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="884f8-155">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="884f8-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="884f8-156">See also</span></span>

- <span data-ttu-id="884f8-157">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) (具像狀態傳輸 (REST))</span><span class="sxs-lookup"><span data-stu-id="884f8-157">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)</span></span>
