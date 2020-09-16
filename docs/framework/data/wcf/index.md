---
title: WCF Data Services 4.5
description: 瞭解 WCF Data Services，這是 .NET Framework 元件，其支援使用 REST 語義公開和取用資料的服務。
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: c36967236c40efbf432d554c3f551aea22cfb148
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549675"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="6efe0-103">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="6efe0-103">WCF Data Services 4.5</span></span>

<span data-ttu-id="6efe0-104">WCF Data Services (之前稱為「ADO.NET 資料服務」 ) 是 .NET Framework 的元件，可讓您建立使用開放式資料通訊協定 (OData) 的服務，利用 [具像狀態傳輸 (REST) ](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)的語法，透過 Web 或內部網路公開及取用資料。</span><span class="sxs-lookup"><span data-stu-id="6efe0-104">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="6efe0-105">OData 會將資料公開為可由 URI 定址的資源。</span><span class="sxs-lookup"><span data-stu-id="6efe0-105">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="6efe0-106">資料是使用 GET、PUT、POST 和 DELETE 的標準 HTTP 動作來存取及變更。</span><span class="sxs-lookup"><span data-stu-id="6efe0-106">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="6efe0-107">OData 使用 [實體資料模型](../adonet/entity-data-model.md) 的實體關聯慣例，將資源公開為依關聯性相關的實體集。</span><span class="sxs-lookup"><span data-stu-id="6efe0-107">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="6efe0-108">WCF Data Services 使用 OData 通訊協定來定址及更新資源。</span><span class="sxs-lookup"><span data-stu-id="6efe0-108">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="6efe0-109">如此一來，您就可以從任何支援 OData 的用戶端存取這些服務。</span><span class="sxs-lookup"><span data-stu-id="6efe0-109">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="6efe0-110">OData 可讓您使用已知的傳輸格式來要求和寫入資料至資源： Atom、一組以 XML 交換和更新資料的標準，以及 JavaScript 物件標記法 (JSON) （在 AJAX 應用程式中廣泛使用的文字型資料交換格式）。</span><span class="sxs-lookup"><span data-stu-id="6efe0-110">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="6efe0-111">WCF Data Services 可以將源自各種來源的資料公開為 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="6efe0-111">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="6efe0-112">Visual Studio 的工具可讓您更輕鬆地使用 ADO.NET Entity Framework 資料模型來建立以 OData 為基礎的服務。</span><span class="sxs-lookup"><span data-stu-id="6efe0-112">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="6efe0-113">您也可以根據 common language runtime (CLR) 類別，甚至是晚期繫結或不具類型的資料，來建立 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="6efe0-113">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="6efe0-114">WCF Data Services 也包含一組用戶端程式庫，一個適用于一般 .NET Framework 用戶端應用程式，另一個則專門用於 Silverlight 架構應用程式。</span><span class="sxs-lookup"><span data-stu-id="6efe0-114">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="6efe0-115">當您從類似 .NET Framework 和 Silverlight 等環境存取 OData 摘要時，這些用戶端程式庫可提供以物件為基礎的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="6efe0-115">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="6efe0-116">我該從哪裡開始？</span><span class="sxs-lookup"><span data-stu-id="6efe0-116">Where Should I Start?</span></span>

<span data-ttu-id="6efe0-117">根據您的興趣，請考慮在下列其中一個主題中開始 WCF Data Services。</span><span class="sxs-lookup"><span data-stu-id="6efe0-117">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="6efe0-118">我想直接開始</span><span class="sxs-lookup"><span data-stu-id="6efe0-118">I want to jump right in...</span></span>

- [<span data-ttu-id="6efe0-119">快速入門</span><span class="sxs-lookup"><span data-stu-id="6efe0-119">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="6efe0-120">快速入門</span><span class="sxs-lookup"><span data-stu-id="6efe0-120">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="6efe0-121">只顯示一些程式碼 .。。</span><span class="sxs-lookup"><span data-stu-id="6efe0-121">Just show me some code...</span></span>

- [<span data-ttu-id="6efe0-122">快速入門</span><span class="sxs-lookup"><span data-stu-id="6efe0-122">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="6efe0-123">作法：執行資料服務查詢</span><span class="sxs-lookup"><span data-stu-id="6efe0-123">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="6efe0-124">作法：將資料繫結至 Windows Presentation Foundation 項目</span><span class="sxs-lookup"><span data-stu-id="6efe0-124">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="6efe0-125">我想要深入瞭解 OData .。。</span><span class="sxs-lookup"><span data-stu-id="6efe0-125">I want to know more about OData...</span></span>

- [<span data-ttu-id="6efe0-126">技術白皮書： OData 簡介</span><span class="sxs-lookup"><span data-stu-id="6efe0-126">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="6efe0-127">開放式資料通訊協定網站</span><span class="sxs-lookup"><span data-stu-id="6efe0-127">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="6efe0-128">OData：SDK</span><span class="sxs-lookup"><span data-stu-id="6efe0-128">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="6efe0-129">我想查看端對端範例 .。。</span><span class="sxs-lookup"><span data-stu-id="6efe0-129">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="6efe0-130">[WCF Data Services 快速入門](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="6efe0-130">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="6efe0-131">OData SDK-範例程式碼</span><span class="sxs-lookup"><span data-stu-id="6efe0-131">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="6efe0-132">如何與 Visual Studio 整合？</span><span class="sxs-lookup"><span data-stu-id="6efe0-132">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="6efe0-133">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="6efe0-133">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="6efe0-134">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="6efe0-134">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="6efe0-135">Entity Framework 提供者</span><span class="sxs-lookup"><span data-stu-id="6efe0-135">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="6efe0-136">用途為何？</span><span class="sxs-lookup"><span data-stu-id="6efe0-136">What can I do with it?</span></span>

- [<span data-ttu-id="6efe0-137">概觀</span><span class="sxs-lookup"><span data-stu-id="6efe0-137">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="6efe0-138">應用程式案例</span><span class="sxs-lookup"><span data-stu-id="6efe0-138">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="6efe0-139">我想要使用 LINQ .。。</span><span class="sxs-lookup"><span data-stu-id="6efe0-139">I want to use LINQ...</span></span>

- [<span data-ttu-id="6efe0-140">查詢資料服務</span><span class="sxs-lookup"><span data-stu-id="6efe0-140">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="6efe0-141">LINQ 考量</span><span class="sxs-lookup"><span data-stu-id="6efe0-141">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="6efe0-142">作法：執行資料服務查詢</span><span class="sxs-lookup"><span data-stu-id="6efe0-142">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="6efe0-143">我還需要其他資訊 .。。</span><span class="sxs-lookup"><span data-stu-id="6efe0-143">I still need some more information...</span></span>

- [<span data-ttu-id="6efe0-144">WCF Data Services 小組部落格</span><span class="sxs-lookup"><span data-stu-id="6efe0-144">WCF Data Services Team Blog</span></span>](/archive/blogs/astoriateam/)

- [<span data-ttu-id="6efe0-145">資源</span><span class="sxs-lookup"><span data-stu-id="6efe0-145">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="6efe0-146">本節內容</span><span class="sxs-lookup"><span data-stu-id="6efe0-146">In This Section</span></span>

[<span data-ttu-id="6efe0-147">概觀</span><span class="sxs-lookup"><span data-stu-id="6efe0-147">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="6efe0-148">提供 WCF Data Services 中可用特性和功能的總覽。</span><span class="sxs-lookup"><span data-stu-id="6efe0-148">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="6efe0-149">[WCF Data Services 5.0 的新功能](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="6efe0-149">[What's New in WCF Data Services 5.0](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="6efe0-150">描述 WCF Data Services 中的新功能，以及新 OData 功能的支援。</span><span class="sxs-lookup"><span data-stu-id="6efe0-150">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="6efe0-151">快速入門</span><span class="sxs-lookup"><span data-stu-id="6efe0-151">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="6efe0-152">說明如何使用 WCF Data Services 公開和取用 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="6efe0-152">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="6efe0-153">定義 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="6efe0-153">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="6efe0-154">描述如何建立及設定公開 OData 摘要的資料服務。</span><span class="sxs-lookup"><span data-stu-id="6efe0-154">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="6efe0-155">WCF 資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="6efe0-155">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="6efe0-156">說明如何使用用戶端程式庫，從 .NET Framework 用戶端應用程式取用 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="6efe0-156">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="6efe0-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6efe0-157">See also</span></span>

- <span data-ttu-id="6efe0-158">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) (具像狀態傳輸 (REST))</span><span class="sxs-lookup"><span data-stu-id="6efe0-158">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)</span></span>
