---
title: Windows Form 的 ClickOnce 部署
ms.date: 03/30/2017
helpviewer_keywords:
- ClickOnce deployment [Windows Forms]
- Windows Forms, ClickOnce deployment
- walkthroughs [Windows Forms], ClickOnce deployment
ms.assetid: 1451fce9-1965-4a03-b4d3-831b5fe4ad66
ms.openlocfilehash: 1212096422f5bb10c7b781228dc54c8790ac97ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072840"
---
# <a name="clickonce-deployment-for-windows-forms"></a><span data-ttu-id="f9546-102">Windows Form 的 ClickOnce 部署</span><span class="sxs-lookup"><span data-stu-id="f9546-102">ClickOnce Deployment for Windows Forms</span></span>
<span data-ttu-id="f9546-103">下列主題描述 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]，您可以使用這項技術輕鬆地將 Windows Form 應用程式部署到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="f9546-103">The following topics describe [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], a technology used for easily deploying Windows Forms applications to client computers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f9546-104">相關章節</span><span class="sxs-lookup"><span data-stu-id="f9546-104">Related Sections</span></span>  
 [<span data-ttu-id="f9546-105">選擇 ClickOnce 部署策略</span><span class="sxs-lookup"><span data-stu-id="f9546-105">Choosing a ClickOnce Deployment Strategy</span></span>](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy)  
 <span data-ttu-id="f9546-106">顯示部署 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的幾個選項。</span><span class="sxs-lookup"><span data-stu-id="f9546-106">Presents several options for deploying [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications.</span></span>  
  
 [<span data-ttu-id="f9546-107">選擇 ClickOnce 更新策略</span><span class="sxs-lookup"><span data-stu-id="f9546-107">Choosing a ClickOnce Update Strategy</span></span>](/visualstudio/deployment/choosing-a-clickonce-update-strategy)  
 <span data-ttu-id="f9546-108">顯示更新 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的幾個選項。</span><span class="sxs-lookup"><span data-stu-id="f9546-108">Presents several options for updating [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications.</span></span>  
  
 [<span data-ttu-id="f9546-109">保護 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="f9546-109">Securing ClickOnce Applications</span></span>](/visualstudio/deployment/securing-clickonce-applications)  
 <span data-ttu-id="f9546-110">說明 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署的安全性影響。</span><span class="sxs-lookup"><span data-stu-id="f9546-110">Explains the security implications of [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployment.</span></span>  
  
 [<span data-ttu-id="f9546-111">疑難排解 ClickOnce 部署</span><span class="sxs-lookup"><span data-stu-id="f9546-111">Troubleshooting ClickOnce Deployments</span></span>](/visualstudio/deployment/troubleshooting-clickonce-deployments)  
 <span data-ttu-id="f9546-112">描述在部署 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式時可能發生的各種問題，並記載 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 可能產生的最上層錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f9546-112">Describes various problems that can occur when deploying [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications, and documents the top-level error messages that [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] might generate.</span></span>  
  
 [<span data-ttu-id="f9546-113">ClickOnce 和應用程式設定</span><span class="sxs-lookup"><span data-stu-id="f9546-113">ClickOnce and Application Settings</span></span>](/visualstudio/deployment/clickonce-and-application-settings)  
 <span data-ttu-id="f9546-114">描述 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署如何使用應用程式設定，這些設定會儲存應用程式和使用者設定以供未來擷取。</span><span class="sxs-lookup"><span data-stu-id="f9546-114">Describes how [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployment works with application settings, which stores application and user settings for future retrieval.</span></span>  
  
 [<span data-ttu-id="f9546-115">受信任的應用程式部署概觀</span><span class="sxs-lookup"><span data-stu-id="f9546-115">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)  
 <span data-ttu-id="f9546-116">描述允許信任的應用程式在用戶端電腦上以更高層級的權限執行的 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="f9546-116">Describes a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] feature that allows trusted applications to run with a higher level of permission on client computers.</span></span>  
  
 [<span data-ttu-id="f9546-117">ClickOnce 和 Authenticode</span><span class="sxs-lookup"><span data-stu-id="f9546-117">ClickOnce and Authenticode</span></span>](/visualstudio/deployment/clickonce-and-authenticode)  
 <span data-ttu-id="f9546-118">描述如何在信任的應用程式部署中使用 Authenticode 技術。</span><span class="sxs-lookup"><span data-stu-id="f9546-118">Describes how Authenticode technology is used in trusted application deployment.</span></span>  
  
 [<span data-ttu-id="f9546-119">逐步解說：手動部署 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="f9546-119">Walkthrough: Manually Deploying a ClickOnce Application</span></span>](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 <span data-ttu-id="f9546-120">示範如何使用命令列和 SDK 工具來部署 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]，而不使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f9546-120">Demonstrates using command-line and SDK tools to deploy a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application without using Visual Studio.</span></span>  
  
 [<span data-ttu-id="f9546-121">如何：將信任發行者新增到 ClickOnce 應用程式的用戶端電腦</span><span class="sxs-lookup"><span data-stu-id="f9546-121">How to: Add a Trusted Publisher to a Client Computer for ClickOnce Applications</span></span>](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications)  
 <span data-ttu-id="f9546-122">示範信任的應用程式部署所需之用戶端電腦的一次組態。</span><span class="sxs-lookup"><span data-stu-id="f9546-122">Demonstrates the one-time configuration of client computers required for trusted application deployment.</span></span>  
  
 [<span data-ttu-id="f9546-123">如何：指定部署更新的替代位置</span><span class="sxs-lookup"><span data-stu-id="f9546-123">How to: Specify an Alternate Location for Deployment Updates</span></span>](/visualstudio/deployment/how-to-specify-an-alternate-location-for-deployment-updates)  
 <span data-ttu-id="f9546-124">示範如何使用 SDK 工具設定 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式，來檢查其他位置是否有新版應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9546-124">Demonstrates configuring a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application, using SDK tools, to check a different location for new versions of an application.</span></span>  
  
 [<span data-ttu-id="f9546-125">逐步解說：依需求以 ClickOnce 部署 API 下載組件</span><span class="sxs-lookup"><span data-stu-id="f9546-125">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api)  
 <span data-ttu-id="f9546-126">示範如何使用應用程式開發介面呼叫，在應用程式第一次嘗試載入組件時擷取組件。</span><span class="sxs-lookup"><span data-stu-id="f9546-126">Demonstrates using API calls to retrieve an assembly the first time your application attempts to load it.</span></span>  
  
 [<span data-ttu-id="f9546-127">如何：在線上 ClickOnce 應用程式中擷取查詢字串資訊</span><span class="sxs-lookup"><span data-stu-id="f9546-127">How to: Retrieve Query String Information in an Online ClickOnce Application</span></span>](/visualstudio/deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application)  
 <span data-ttu-id="f9546-128">示範如何從用來執行 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的 URL 擷取參數。</span><span class="sxs-lookup"><span data-stu-id="f9546-128">Demonstrates retrieving parameters from the URL used to run a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application.</span></span>  
  
 [<span data-ttu-id="f9546-129">ClickOnce 快取概觀</span><span class="sxs-lookup"><span data-stu-id="f9546-129">ClickOnce Cache Overview</span></span>](/visualstudio/deployment/clickonce-cache-overview)  
 <span data-ttu-id="f9546-130">描述本機電腦上用來儲存 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的快取。</span><span class="sxs-lookup"><span data-stu-id="f9546-130">Describes the cache used to store [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications on the local computer.</span></span>  
  
 [<span data-ttu-id="f9546-131">在 ClickOnce 應用程式中存取本機和遠端資料</span><span class="sxs-lookup"><span data-stu-id="f9546-131">Accessing Local and Remote Data in ClickOnce Applications</span></span>](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)  
 <span data-ttu-id="f9546-132">描述如何從 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式存取本機資料檔案和遠端資料來源。</span><span class="sxs-lookup"><span data-stu-id="f9546-132">Describes how to access local data files and remote data sources from a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application.</span></span>  
  
 [<span data-ttu-id="f9546-133">如何：在 ClickOnce 應用程式中納入資料檔案</span><span class="sxs-lookup"><span data-stu-id="f9546-133">How to: Include a Data File in a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application)  
 <span data-ttu-id="f9546-134">示範如何標記檔案，以便在 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 資料目錄中使用。</span><span class="sxs-lookup"><span data-stu-id="f9546-134">Demonstrates how to mark a file so that it is available in the [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] data directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9546-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9546-135">See also</span></span>

- [<span data-ttu-id="f9546-136">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="f9546-136">Application Settings Overview</span></span>](./advanced/application-settings-overview.md)
- [<span data-ttu-id="f9546-137">發行 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="f9546-137">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)
- [<span data-ttu-id="f9546-138">從命令列建置 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="f9546-138">Building ClickOnce Applications from the Command Line</span></span>](/visualstudio/deployment/building-clickonce-applications-from-the-command-line)
- [<span data-ttu-id="f9546-139">偵錯使用 System.Deployment.Application 的 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="f9546-139">Debugging ClickOnce Applications That Use System.Deployment.Application</span></span>](/visualstudio/deployment/debugging-clickonce-applications-that-use-system-deployment-application)
- [<span data-ttu-id="f9546-140">使用 ClickOnce 部署 COM 元件</span><span class="sxs-lookup"><span data-stu-id="f9546-140">Deploying COM Components with ClickOnce</span></span>](/visualstudio/deployment/deploying-com-components-with-clickonce)
- <span data-ttu-id="f9546-141">[如何：使用 [發佈精靈] 發佈 ClickOnce 應用程式](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)</span><span class="sxs-lookup"><span data-stu-id="f9546-141">[How to: Publish a ClickOnce Application using the Publish Wizard](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)</span></span>
