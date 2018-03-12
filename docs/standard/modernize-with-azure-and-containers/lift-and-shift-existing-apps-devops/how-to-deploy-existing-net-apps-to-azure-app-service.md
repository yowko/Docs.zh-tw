---
title: "如何將現有的.NET 應用程式部署至 Azure App Service"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |如何將現有的.NET 應用程式部署至 Azure App Service"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aefcd79574cbbf6b3759bfa6cc0f9e46a58244ce
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a><span data-ttu-id="e7e59-103">如何將現有的.NET 應用程式部署至 Azure App Service</span><span class="sxs-lookup"><span data-stu-id="e7e59-103">How to deploy existing .NET apps to Azure App Service</span></span> 

<span data-ttu-id="e7e59-104">Azure App Service Web 應用程式功能是完全受管理的運算平台，並針對主控網站和 web 應用程式最佳化。</span><span class="sxs-lookup"><span data-stu-id="e7e59-104">The Web Apps feature of Azure App Service is a fully managed compute platform that is optimized for hosting websites and web apps.</span></span> <span data-ttu-id="e7e59-105">此 PaaS 供應項目，在 Microsoft Azure 可讓您專注於商務邏輯，而 Azure 會負責執行，並調整您的應用程式的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="e7e59-105">This PaaS offering in Microsoft Azure lets you focus on your business logic, while Azure takes care of the infrastructure to run and scale your apps.</span></span>

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a><span data-ttu-id="e7e59-106">驗證站台，並移轉至 App Service 與 Azure 應用程式服務移轉小幫手</span><span class="sxs-lookup"><span data-stu-id="e7e59-106">Validate sites and migrate to App Service with Azure App Service Migration Assistant</span></span>

<span data-ttu-id="e7e59-107">當您建立新的應用程式在 Visual Studio 中，將應用程式移至應用程式服務通常相當簡單。</span><span class="sxs-lookup"><span data-stu-id="e7e59-107">When you create a new application in Visual Studio, moving the app to App Service usually is straightforward.</span></span> <span data-ttu-id="e7e59-108">不過，如果您正在規劃移轉現有應用程式服務的應用程式，您必須先評估所有應用程式的相依性是否與應用程式服務相容。</span><span class="sxs-lookup"><span data-stu-id="e7e59-108">However, if you are planning to migrate an existing application to App Service, first you need to evaluate whether all your application's dependencies are compatible with App Service.</span></span> <span data-ttu-id="e7e59-109">這包括伺服器作業系統和伺服器安裝任何協力廠商軟體相依性。</span><span class="sxs-lookup"><span data-stu-id="e7e59-109">This includes dependencies like server OS and any third-party software that's installed on the server.</span></span>

<span data-ttu-id="e7e59-110">您可以使用[Azure 應用程式服務移轉小幫手](https://www.migratetoazure.net/)來分析網站並再將它們從 Windows 和 Linux 的 web 伺服器，移轉到應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="e7e59-110">You can use [Azure App Service Migration Assistant](https://www.migratetoazure.net/) to analyze sites and then migrate them from Windows and Linux web servers to App Service.</span></span> <span data-ttu-id="e7e59-111">移轉的一部分，此工具會建立 web 應用程式，且資料庫在 Azure 上的如有需要發行的內容，並發行您的資料庫。</span><span class="sxs-lookup"><span data-stu-id="e7e59-111">As part of the migration, the tool creates web apps and databases on Azure as needed, publishes content, and publishes your database.</span></span>

<span data-ttu-id="e7e59-112">Azure 應用程式服務移轉小幫手支援移轉至雲端的 Windows Server 上執行的 iis。</span><span class="sxs-lookup"><span data-stu-id="e7e59-112">Azure App Service Migration Assistant supports migrating from IIS running on Windows Server to the cloud.</span></span> <span data-ttu-id="e7e59-113">應用程式服務支援 Windows Server 2003 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="e7e59-113">App Service supports Windows Server 2003 and later versions.</span></span>

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> <span data-ttu-id="e7e59-115">**圖 4-5。**</span><span class="sxs-lookup"><span data-stu-id="e7e59-115">**Figure 4-5.**</span></span> <span data-ttu-id="e7e59-116">使用 Azure App Service 移轉小幫手</span><span class="sxs-lookup"><span data-stu-id="e7e59-116">Using Azure App Service Migration Assistant</span></span>

<span data-ttu-id="e7e59-117">應用程式服務移轉小幫手是一種工具，將您的網站，從您網頁伺服器移至 Azure 雲端。</span><span class="sxs-lookup"><span data-stu-id="e7e59-117">App Service Migration Assistant is a tool that moves your websites from your web servers to the Azure cloud.</span></span>

<span data-ttu-id="e7e59-118">網站移轉至 App Service 之後，站台會有安全而有效率地執行所需要的所有項目。</span><span class="sxs-lookup"><span data-stu-id="e7e59-118">After a website is migrated to App Service, the site has everything it needs to run safely and efficiently.</span></span> <span data-ttu-id="e7e59-119">站台所設定，並自動在 Azure 雲端 PaaS 服務 （應用程式服務） 中執行。</span><span class="sxs-lookup"><span data-stu-id="e7e59-119">Sites are set up and run automatically in the Azure cloud PaaS service (App Service).</span></span>

<span data-ttu-id="e7e59-120">應用程式服務移轉工具可以分析您的網站，並報告其相容性移至應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="e7e59-120">The App Service migration tool can analyze your websites and report on their compatibility for moving to App Service.</span></span> <span data-ttu-id="e7e59-121">如果您很滿意分析，您可以讓應用程式服務移轉小幫手移轉內容、 資料和設定。</span><span class="sxs-lookup"><span data-stu-id="e7e59-121">If you're happy with the analysis, you can let App Service Migration Assistant migrate content, data, and settings for you.</span></span> <span data-ttu-id="e7e59-122">如果網站不完全相容，則會移轉工具，告訴您需要調整，以讓它運作。</span><span class="sxs-lookup"><span data-stu-id="e7e59-122">If a site is not quite compatible, the migration tool tells you what you need to adjust to make it work.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e7e59-123">其他資源</span><span class="sxs-lookup"><span data-stu-id="e7e59-123">Additional resources</span></span>

- <span data-ttu-id="e7e59-124">**Azure App Service 移轉小幫手**</span><span class="sxs-lookup"><span data-stu-id="e7e59-124">**Azure App Service Migration Assistant**</span></span>

    [<span data-ttu-id="e7e59-125">https://www.migratetoazure.net/</span><span class="sxs-lookup"><span data-stu-id="e7e59-125">https://www.migratetoazure.net/</span></span>](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
<span data-ttu-id="e7e59-126">[上一頁](what-about-cloud-optimized-applications.md)
[下一頁](deploy-existing-net-apps-as-windows-containers.md)</span><span class="sxs-lookup"><span data-stu-id="e7e59-126">[Previous](what-about-cloud-optimized-applications.md)
[Next](deploy-existing-net-apps-as-windows-containers.md)</span></span>
