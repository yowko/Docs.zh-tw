---
title: 快速入門 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: 1a30f7e65efc65bf47abd61e5bfdfa85b58ae3a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365393"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="84894-102">快速入門 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="84894-102">Quickstart (WCF Data Services)</span></span>
<span data-ttu-id="84894-103">本快速入門可協助您熟悉[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]和[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]透過一系列的支援中的主題的工作[入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="84894-103">This quickstart helps you become familiar with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="84894-104">學習內容</span><span class="sxs-lookup"><span data-stu-id="84894-104">What You Will Learn</span></span>  
 <span data-ttu-id="84894-105">本快速入門的第一個工作會示範如何建立資料服務，以公開來自 Northwind 範例資料庫的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。</span><span class="sxs-lookup"><span data-stu-id="84894-105">The first task in this quickstart shows how to create a data service to expose an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from the Northwind sample database.</span></span> <span data-ttu-id="84894-106">在後續主題中，您將使用 Web 瀏覽器存取 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要，也會建立 Windows Presentation Foundation (WPF) 用戶端應用程式，這個應用程式會利用用戶端程式庫來取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。</span><span class="sxs-lookup"><span data-stu-id="84894-106">In later topics, you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using client libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="84894-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="84894-107">Prerequisites</span></span>  
 <span data-ttu-id="84894-108">若要完成本快速入門，您必須安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="84894-108">To complete this quickstart, you must install the following components:</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]<span data-ttu-id="84894-109">.</span><span class="sxs-lookup"><span data-stu-id="84894-109">.</span></span>  
  
-   <span data-ttu-id="84894-110">執行個體[!INCLUDE[msCoName](../../../../includes/msconame-md.md)]SQL Server。</span><span class="sxs-lookup"><span data-stu-id="84894-110">An instance of [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] SQL Server.</span></span> <span data-ttu-id="84894-111">其中包括 SQL Server Express，這個產品會包含在 Visual Studio 的預設安裝中。</span><span class="sxs-lookup"><span data-stu-id="84894-111">This includes SQL Server Express, which is included in a default installation of Visual Studio.</span></span>  
  
-   <span data-ttu-id="84894-112">Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="84894-112">The Northwind sample database.</span></span> <span data-ttu-id="84894-113">若要下載此範例資料庫，請參閱下載頁面： [SQL Server 的範例資料庫](http://go.microsoft.com/fwlink/?linkid=24758)。</span><span class="sxs-lookup"><span data-stu-id="84894-113">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="84894-114">WCF Data Services 快速入門工作</span><span class="sxs-lookup"><span data-stu-id="84894-114">WCF Data Services Quickstart Tasks</span></span>  
 [<span data-ttu-id="84894-115">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="84894-115">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
 <span data-ttu-id="84894-116">定義 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式、定義資料模型、建立資料服務，並且啟用資源存取。</span><span class="sxs-lookup"><span data-stu-id="84894-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>  
  
 [<span data-ttu-id="84894-117">從網頁瀏覽器存取服務</span><span class="sxs-lookup"><span data-stu-id="84894-117">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
 <span data-ttu-id="84894-118">從 Visual Studio 啟動服務，然後透過 Web 瀏覽器將 HTTP GET 要求提交至公開的摘要，以存取該服務。</span><span class="sxs-lookup"><span data-stu-id="84894-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>  
  
 [<span data-ttu-id="84894-119">建立 .NET Framework 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="84894-119">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
 <span data-ttu-id="84894-120">建立 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 用戶端應用程式來取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要、將資料繫結至 Windows 控制項、變更繫結控制項中的資料，然後將變更傳回資料服務。</span><span class="sxs-lookup"><span data-stu-id="84894-120">Create a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] client application to consume the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84894-121">已完成之快速入門版本中的專案檔案可以從 [WCF Data Services 文件範例](http://go.microsoft.com/fwlink/?LinkId=179994) 頁面下載。</span><span class="sxs-lookup"><span data-stu-id="84894-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](http://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="84894-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="84894-122">Next Steps</span></span>  
 <span data-ttu-id="84894-123">[啟動快速入門](../../../../docs/framework/data/wcf/creating-the-data-service.md)</span><span class="sxs-lookup"><span data-stu-id="84894-123">[Start the Quickstart](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84894-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84894-124">See Also</span></span>  
 [<span data-ttu-id="84894-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="84894-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
