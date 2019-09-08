---
title: 快速入門 (WCF 資料服務)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: df6806cd77e7ff109d79f7ba61866763de4c7fc1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790372"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="fff7a-102">快速入門 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="fff7a-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="fff7a-103">本快速入門可協助您[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]透過一系列支援[消費者入門](getting-started-with-wcf-data-services.md)主題的工作，熟悉 WCF Data Services 和。</span><span class="sxs-lookup"><span data-stu-id="fff7a-103">This quickstart helps you become familiar with WCF Data Services and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="fff7a-104">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="fff7a-104">What you'll learn</span></span>

<span data-ttu-id="fff7a-105">本快速入門中的第一個工作會示範如何建立資料服務，以公開 Northwind 範例資料庫中的 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="fff7a-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="fff7a-106">在後續的主題中，您將使用網頁瀏覽器來存取 OData 摘要，並使用用戶端程式庫建立使用 OData 摘要的 Windows Presentation Foundation （WPF）用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="fff7a-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fff7a-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="fff7a-107">Prerequisites</span></span>

<span data-ttu-id="fff7a-108">若要完成本快速入門，您必須安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="fff7a-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="fff7a-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fff7a-109">Visual Studio</span></span>

- <span data-ttu-id="fff7a-110">SQL Server 的實例。</span><span class="sxs-lookup"><span data-stu-id="fff7a-110">An instance of SQL Server.</span></span> <span data-ttu-id="fff7a-111">這包括 SQL Server Express （隨附于 Visual Studio 2015 的預設安裝中），或 Visual Studio 2017 中的**資料儲存和處理**工作負載的一部分。</span><span class="sxs-lookup"><span data-stu-id="fff7a-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="fff7a-112">Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="fff7a-112">The Northwind sample database.</span></span> <span data-ttu-id="fff7a-113">若要下載此範例資料庫，請參閱下載頁面： [SQL Server 的範例資料庫](https://go.microsoft.com/fwlink/?linkid=24758)。</span><span class="sxs-lookup"><span data-stu-id="fff7a-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="fff7a-114">WCF data services 快速入門工作</span><span class="sxs-lookup"><span data-stu-id="fff7a-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="fff7a-115">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="fff7a-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="fff7a-116">定義 ADO.NET 應用程式、定義資料模型、建立資料服務，並且啟用資源存取。</span><span class="sxs-lookup"><span data-stu-id="fff7a-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="fff7a-117">從網頁瀏覽器存取服務</span><span class="sxs-lookup"><span data-stu-id="fff7a-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="fff7a-118">從 Visual Studio 啟動服務，然後透過 Web 瀏覽器將 HTTP GET 要求提交至公開的摘要，以存取該服務。</span><span class="sxs-lookup"><span data-stu-id="fff7a-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="fff7a-119">建立 .NET Framework 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="fff7a-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="fff7a-120">建立 WPF 應用程式來取用 OData 摘要、將資料系結至 Windows 控制項、變更繫結控制項中的資料，然後將變更傳回資料服務。</span><span class="sxs-lookup"><span data-stu-id="fff7a-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="fff7a-121">已完成之快速入門版本中的專案檔案可以從 [WCF Data Services 文件範例](https://go.microsoft.com/fwlink/?LinkId=179994) 頁面下載。</span><span class="sxs-lookup"><span data-stu-id="fff7a-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fff7a-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fff7a-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fff7a-123">開始快速入門</span><span class="sxs-lookup"><span data-stu-id="fff7a-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="fff7a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fff7a-124">See also</span></span>

- [<span data-ttu-id="fff7a-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="fff7a-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
