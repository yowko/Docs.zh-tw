---
title: 快速入門 (WCF 資料服務)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: 49d11556d3703331b4cdf5bf83a69f6b15bca8ed
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881986"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="dbc0a-102">快速入門 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="dbc0a-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="dbc0a-103">本快速入門可協助您熟悉 WCF Data Services 和[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]透過一系列的支援中的主題的工作[快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-103">This quickstart helps you become familiar with WCF Data Services and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="dbc0a-104">您將學到什麼</span><span class="sxs-lookup"><span data-stu-id="dbc0a-104">What you'll learn</span></span>

<span data-ttu-id="dbc0a-105">第一項工作在本快速入門示範如何建立資料服務，以公開 OData 摘要，從 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="dbc0a-106">在後續主題中，您將會存取 OData 摘要使用網頁瀏覽器，並也會建立 Windows Presentation Foundation (WPF) 用戶端應用程式取用 OData 摘要的用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dbc0a-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="dbc0a-107">Prerequisites</span></span>

<span data-ttu-id="dbc0a-108">若要完成本快速入門，您必須安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="dbc0a-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="dbc0a-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dbc0a-109">Visual Studio</span></span>

- <span data-ttu-id="dbc0a-110">SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-110">An instance of SQL Server.</span></span> <span data-ttu-id="dbc0a-111">這包括 SQL Server Express，隨附於預設安裝的 Visual Studio 2015，或做為一部分**資料儲存和處理**Visual Studio 2017 中的工作負載。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="dbc0a-112">Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-112">The Northwind sample database.</span></span> <span data-ttu-id="dbc0a-113">若要下載此範例資料庫，請參閱下載頁面： [SQL Server 的範例資料庫](https://go.microsoft.com/fwlink/?linkid=24758)。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="dbc0a-114">WCF data services 快速入門工作</span><span class="sxs-lookup"><span data-stu-id="dbc0a-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="dbc0a-115">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="dbc0a-115">Create the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

 <span data-ttu-id="dbc0a-116">定義 ADO.NET 應用程式、定義資料模型、建立資料服務，並且啟用資源存取。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="dbc0a-117">從網頁瀏覽器存取服務</span><span class="sxs-lookup"><span data-stu-id="dbc0a-117">Access the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="dbc0a-118">從 Visual Studio 啟動服務，然後透過 Web 瀏覽器將 HTTP GET 要求提交至公開的摘要，以存取該服務。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="dbc0a-119">建立.NET Framework 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="dbc0a-119">Create the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="dbc0a-120">建立 WPF 應用程式取用 OData 摘要、 將資料繫結至 Windows 控制項、 變更繫結控制項中的資料，然後將變更傳回資料服務。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="dbc0a-121">已完成之快速入門版本中的專案檔案可以從 [WCF Data Services 文件範例](https://go.microsoft.com/fwlink/?LinkId=179994) 頁面下載。</span><span class="sxs-lookup"><span data-stu-id="dbc0a-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dbc0a-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dbc0a-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dbc0a-123">啟動快速入門</span><span class="sxs-lookup"><span data-stu-id="dbc0a-123">Start the quickstart</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="dbc0a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbc0a-124">See also</span></span>

- [<span data-ttu-id="dbc0a-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="dbc0a-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
