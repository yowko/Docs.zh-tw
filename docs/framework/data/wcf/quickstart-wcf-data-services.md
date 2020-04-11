---
title: 快速入門 (WCF 資料服務)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121218"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="9736d-102">快速入門 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="9736d-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="9736d-103">此快速入門可説明您通過一系列支援[入門](getting-started-with-wcf-data-services.md)主題的任務熟悉 WCF 數據服務和開放數據協定 (OData)。</span><span class="sxs-lookup"><span data-stu-id="9736d-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="9736d-104">您將學到什麼</span><span class="sxs-lookup"><span data-stu-id="9736d-104">What you'll learn</span></span>

<span data-ttu-id="9736d-105">此快速入門中的第一個任務演示如何創建數據服務以公開來自北風示例資料庫的 OData 源。</span><span class="sxs-lookup"><span data-stu-id="9736d-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="9736d-106">在後面的主題中,您將使用 Web 瀏覽器訪問 OData 源,還可以建立一個 Windows 演示文稿基礎 (WPF) 用戶端應用程式,該應用程式使用用戶端庫使用 OData 源。</span><span class="sxs-lookup"><span data-stu-id="9736d-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9736d-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="9736d-107">Prerequisites</span></span>

<span data-ttu-id="9736d-108">要完成此快速入門,請安裝以下元件:</span><span class="sxs-lookup"><span data-stu-id="9736d-108">To complete this quickstart, install the following components:</span></span>

- <span data-ttu-id="9736d-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9736d-109">Visual Studio</span></span>

- <span data-ttu-id="9736d-110">SQL 伺服器的實例。</span><span class="sxs-lookup"><span data-stu-id="9736d-110">An instance of SQL Server.</span></span> <span data-ttu-id="9736d-111">這包括 SQL Server Express,它包含在 Visual Studio 2015 的預設安裝中,或作為 Visual Studio 2017 或更高版本中**的數據儲存和處理**工作負載的一部分。</span><span class="sxs-lookup"><span data-stu-id="9736d-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="9736d-112">Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="9736d-112">The Northwind sample database.</span></span> <span data-ttu-id="9736d-113">要安裝資料庫,請從北風執行 Transact-SQL 文稿[,並為 Microsoft SQL Server 執行 pubs 範例資料庫](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)。</span><span class="sxs-lookup"><span data-stu-id="9736d-113">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="9736d-114">WCF 資料服務快速啟動工作</span><span class="sxs-lookup"><span data-stu-id="9736d-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="9736d-115">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="9736d-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="9736d-116">定義 ADO.NET 應用程式、定義資料模型、建立資料服務，並且啟用資源存取。</span><span class="sxs-lookup"><span data-stu-id="9736d-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="9736d-117">從網頁瀏覽器存取服務</span><span class="sxs-lookup"><span data-stu-id="9736d-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="9736d-118">從 Visual Studio 啟動服務，然後透過 Web 瀏覽器將 HTTP GET 要求提交至公開的摘要，以存取該服務。</span><span class="sxs-lookup"><span data-stu-id="9736d-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="9736d-119">建立 .NET 框架客戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="9736d-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="9736d-120">創建 WPF 應用以使用 OData 源、將資料綁定到 Windows 控制件、更改繫結項的資料,然後將更改發送回資料服務。</span><span class="sxs-lookup"><span data-stu-id="9736d-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="9736d-121">專案檔從已完成版本的快速啟動可以從[GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))下載。</span><span class="sxs-lookup"><span data-stu-id="9736d-121">Project files from a completed version of the quickstart can be downloaded from [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9736d-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9736d-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9736d-123">開始快速入門</span><span class="sxs-lookup"><span data-stu-id="9736d-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="9736d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9736d-124">See also</span></span>

- [<span data-ttu-id="9736d-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="9736d-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
