---
title: 快速入門 (WCF 資料服務)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: df3151dfd3628231d84d2d128c61d1c0b6b0d48e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800360"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="41454-102">快速入門 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="41454-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="41454-103">本快速入門可協助您透過一系列支援[消費者入門](getting-started-with-wcf-data-services.md)主題的工作，熟悉 WCF Data Services 和開放式資料通訊協定（OData）。</span><span class="sxs-lookup"><span data-stu-id="41454-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="41454-104">學習內容</span><span class="sxs-lookup"><span data-stu-id="41454-104">What you'll learn</span></span>

<span data-ttu-id="41454-105">本快速入門中的第一個工作會示範如何建立資料服務，以公開 Northwind 範例資料庫中的 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="41454-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="41454-106">在後續的主題中，您將使用網頁瀏覽器來存取 OData 摘要，並使用用戶端程式庫建立使用 OData 摘要的 Windows Presentation Foundation （WPF）用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="41454-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="41454-107">必要條件：</span><span class="sxs-lookup"><span data-stu-id="41454-107">Prerequisites</span></span>

<span data-ttu-id="41454-108">若要完成本快速入門，您必須安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="41454-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="41454-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="41454-109">Visual Studio</span></span>

- <span data-ttu-id="41454-110">SQL Server 的實例。</span><span class="sxs-lookup"><span data-stu-id="41454-110">An instance of SQL Server.</span></span> <span data-ttu-id="41454-111">這包括 SQL Server Express （隨附于 Visual Studio 2015 的預設安裝中），或是 Visual Studio 2017 或更新版本中的**資料儲存和處理**工作負載的一部分。</span><span class="sxs-lookup"><span data-stu-id="41454-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="41454-112">Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="41454-112">The Northwind sample database.</span></span> <span data-ttu-id="41454-113">若要下載此範例資料庫，請參閱下載頁面： [SQL Server 的範例資料庫](https://go.microsoft.com/fwlink/?linkid=24758)。</span><span class="sxs-lookup"><span data-stu-id="41454-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="41454-114">WCF data services 快速入門工作</span><span class="sxs-lookup"><span data-stu-id="41454-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="41454-115">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="41454-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="41454-116">定義 ADO.NET 應用程式、定義資料模型、建立資料服務，並且啟用資源存取。</span><span class="sxs-lookup"><span data-stu-id="41454-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="41454-117">從網頁瀏覽器存取服務</span><span class="sxs-lookup"><span data-stu-id="41454-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="41454-118">從 Visual Studio 啟動服務，然後透過 Web 瀏覽器將 HTTP GET 要求提交至公開的摘要，以存取該服務。</span><span class="sxs-lookup"><span data-stu-id="41454-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="41454-119">建立 .NET Framework 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="41454-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="41454-120">建立 WPF 應用程式來取用 OData 摘要、將資料系結至 Windows 控制項、變更繫結控制項中的資料，然後將變更傳回資料服務。</span><span class="sxs-lookup"><span data-stu-id="41454-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="41454-121">已完成之快速入門版本中的專案檔案可以從 [WCF Data Services 文件範例](https://go.microsoft.com/fwlink/?LinkId=179994) 頁面下載。</span><span class="sxs-lookup"><span data-stu-id="41454-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="41454-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="41454-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="41454-123">開始快速入門</span><span class="sxs-lookup"><span data-stu-id="41454-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="41454-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="41454-124">See also</span></span>

- [<span data-ttu-id="41454-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="41454-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
