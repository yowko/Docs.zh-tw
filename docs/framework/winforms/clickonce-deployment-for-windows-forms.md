---
title: Windows Form 的 ClickOnce 部署
ms.date: 03/30/2017
helpviewer_keywords:
- ClickOnce deployment [Windows Forms]
- Windows Forms, ClickOnce deployment
- walkthroughs [Windows Forms], ClickOnce deployment
ms.assetid: 1451fce9-1965-4a03-b4d3-831b5fe4ad66
ms.openlocfilehash: 0b76e07a23b105f2c1b4fb55a0d25bb52bcb9dc2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741142"
---
# <a name="clickonce-deployment-for-windows-forms"></a><span data-ttu-id="6aa52-102">Windows Form 的 ClickOnce 部署</span><span class="sxs-lookup"><span data-stu-id="6aa52-102">ClickOnce Deployment for Windows Forms</span></span>
<span data-ttu-id="6aa52-103">下列主題描述 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]，您可以使用這項技術輕鬆地將 Windows Form 應用程式部署到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="6aa52-103">The following topics describe [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], a technology used for easily deploying Windows Forms applications to client computers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6aa52-104">相關章節</span><span class="sxs-lookup"><span data-stu-id="6aa52-104">Related Sections</span></span>  
 [<span data-ttu-id="6aa52-105">選擇 ClickOnce 部署策略</span><span class="sxs-lookup"><span data-stu-id="6aa52-105">Choosing a ClickOnce Deployment Strategy</span></span>](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy)  
 <span data-ttu-id="6aa52-106">顯示部署 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的幾個選項。</span><span class="sxs-lookup"><span data-stu-id="6aa52-106">Presents several options for deploying [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications.</span></span>  
  
 [<span data-ttu-id="6aa52-107">選擇 ClickOnce 更新策略</span><span class="sxs-lookup"><span data-stu-id="6aa52-107">Choosing a ClickOnce Update Strategy</span></span>](/visualstudio/deployment/choosing-a-clickonce-update-strategy)  
 <span data-ttu-id="6aa52-108">顯示更新 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的幾個選項。</span><span class="sxs-lookup"><span data-stu-id="6aa52-108">Presents several options for updating [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications.</span></span>  
  
 [<span data-ttu-id="6aa52-109">保護 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="6aa52-109">Securing ClickOnce Applications</span></span>](/visualstudio/deployment/securing-clickonce-applications)  
 <span data-ttu-id="6aa52-110">說明 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署的安全性影響。</span><span class="sxs-lookup"><span data-stu-id="6aa52-110">Explains the security implications of [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployment.</span></span>  
  
 [<span data-ttu-id="6aa52-111">疑難排解 ClickOnce 部署</span><span class="sxs-lookup"><span data-stu-id="6aa52-111">Troubleshooting ClickOnce Deployments</span></span>](/visualstudio/deployment/troubleshooting-clickonce-deployments)  
 <span data-ttu-id="6aa52-112">描述在部署 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式時可能發生的各種問題，並記載 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 可能產生的最上層錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="6aa52-112">Describes various problems that can occur when deploying [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications, and documents the top-level error messages that [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] might generate.</span></span>  
  
 [<span data-ttu-id="6aa52-113">ClickOnce 和應用程式設定</span><span class="sxs-lookup"><span data-stu-id="6aa52-113">ClickOnce and Application Settings</span></span>](/visualstudio/deployment/clickonce-and-application-settings)  
 <span data-ttu-id="6aa52-114">描述 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署如何使用應用程式設定，這些設定會儲存應用程式和使用者設定以供未來擷取。</span><span class="sxs-lookup"><span data-stu-id="6aa52-114">Describes how [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployment works with application settings, which stores application and user settings for future retrieval.</span></span>  
  
 [<span data-ttu-id="6aa52-115">受信任的應用程式部署概觀</span><span class="sxs-lookup"><span data-stu-id="6aa52-115">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)  
 <span data-ttu-id="6aa52-116">描述允許信任的應用程式在用戶端電腦上以更高層級的權限執行的 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="6aa52-116">Describes a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] feature that allows trusted applications to run with a higher level of permission on client computers.</span></span>  
  
 [<span data-ttu-id="6aa52-117">ClickOnce 和 Authenticode</span><span class="sxs-lookup"><span data-stu-id="6aa52-117">ClickOnce and Authenticode</span></span>](/visualstudio/deployment/clickonce-and-authenticode)  
 <span data-ttu-id="6aa52-118">描述如何在信任的應用程式部署中使用 Authenticode 技術。</span><span class="sxs-lookup"><span data-stu-id="6aa52-118">Describes how Authenticode technology is used in trusted application deployment.</span></span>  
  
 [<span data-ttu-id="6aa52-119">逐步解說：手動部署 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="6aa52-119">Walkthrough: Manually Deploying a ClickOnce Application</span></span>](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 <span data-ttu-id="6aa52-120">示範如何使用命令列和 SDK 工具來部署 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]，而不使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="6aa52-120">Demonstrates using command-line and SDK tools to deploy a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application without using Visual Studio.</span></span>  
  
 [<span data-ttu-id="6aa52-121">如何：新增信任發行者至 ClickOnce 應用程式的用戶端電腦</span><span class="sxs-lookup"><span data-stu-id="6aa52-121">How to: Add a Trusted Publisher to a Client Computer for ClickOnce Applications</span></span>](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications)  
 <span data-ttu-id="6aa52-122">示範信任的應用程式部署所需之用戶端電腦的一次組態。</span><span class="sxs-lookup"><span data-stu-id="6aa52-122">Demonstrates the one-time configuration of client computers required for trusted application deployment.</span></span>  
  
 [<span data-ttu-id="6aa52-123">如何：指定部署更新的替代位置</span><span class="sxs-lookup"><span data-stu-id="6aa52-123">How to: Specify an Alternate Location for Deployment Updates</span></span>](/visualstudio/deployment/how-to-specify-an-alternate-location-for-deployment-updates)  
 <span data-ttu-id="6aa52-124">示範如何使用 SDK 工具設定 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式，來檢查其他位置是否有新版應用程式。</span><span class="sxs-lookup"><span data-stu-id="6aa52-124">Demonstrates configuring a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application, using SDK tools, to check a different location for new versions of an application.</span></span>  
  
 [<span data-ttu-id="6aa52-125">逐步解說：依需求以 ClickOnce 部署 API 下載組件</span><span class="sxs-lookup"><span data-stu-id="6aa52-125">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api)  
 <span data-ttu-id="6aa52-126">示範如何使用應用程式開發介面呼叫，在應用程式第一次嘗試載入組件時擷取組件。</span><span class="sxs-lookup"><span data-stu-id="6aa52-126">Demonstrates using API calls to retrieve an assembly the first time your application attempts to load it.</span></span>  
  
 [<span data-ttu-id="6aa52-127">如何：在線上 ClickOnce 應用程式中擷取查詢字串資訊</span><span class="sxs-lookup"><span data-stu-id="6aa52-127">How to: Retrieve Query String Information in an Online ClickOnce Application</span></span>](/visualstudio/deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application)  
 <span data-ttu-id="6aa52-128">示範如何從用來執行 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的 URL 擷取參數。</span><span class="sxs-lookup"><span data-stu-id="6aa52-128">Demonstrates retrieving parameters from the URL used to run a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application.</span></span>  
  
 [<span data-ttu-id="6aa52-129">ClickOnce 快取概觀</span><span class="sxs-lookup"><span data-stu-id="6aa52-129">ClickOnce Cache Overview</span></span>](/visualstudio/deployment/clickonce-cache-overview)  
 <span data-ttu-id="6aa52-130">描述本機電腦上用來儲存 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的快取。</span><span class="sxs-lookup"><span data-stu-id="6aa52-130">Describes the cache used to store [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications on the local computer.</span></span>  
  
 [<span data-ttu-id="6aa52-131">在 ClickOnce 應用程式中存取本機和遠端資料</span><span class="sxs-lookup"><span data-stu-id="6aa52-131">Accessing Local and Remote Data in ClickOnce Applications</span></span>](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)  
 <span data-ttu-id="6aa52-132">描述如何從 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式存取本機資料檔案和遠端資料來源。</span><span class="sxs-lookup"><span data-stu-id="6aa52-132">Describes how to access local data files and remote data sources from a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application.</span></span>  
  
 [<span data-ttu-id="6aa52-133">如何：在 ClickOnce 應用程式中納入資料檔案</span><span class="sxs-lookup"><span data-stu-id="6aa52-133">How to: Include a Data File in a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application)  
 <span data-ttu-id="6aa52-134">示範如何標記檔案，以便在 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 資料目錄中使用。</span><span class="sxs-lookup"><span data-stu-id="6aa52-134">Demonstrates how to mark a file so that it is available in the [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] data directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa52-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6aa52-135">See Also</span></span>  
 [<span data-ttu-id="6aa52-136">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="6aa52-136">Application Settings Overview</span></span>](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="6aa52-137">發行 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="6aa52-137">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)  
 [<span data-ttu-id="6aa52-138">從命令列建置 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="6aa52-138">Building ClickOnce Applications from the Command Line</span></span>](/visualstudio/deployment/building-clickonce-applications-from-the-command-line)  
 [<span data-ttu-id="6aa52-139">偵錯使用 System.Deployment.Application 的 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="6aa52-139">Debugging ClickOnce Applications That Use System.Deployment.Application</span></span>](https://msdn.microsoft.com/library/86f31948-2ca8-47c0-8e8b-c2b817bbf79f)  
 [<span data-ttu-id="6aa52-140">使用 ClickOnce 部署 COM 元件</span><span class="sxs-lookup"><span data-stu-id="6aa52-140">Deploying COM Components with ClickOnce</span></span>](/visualstudio/deployment/deploying-com-components-with-clickonce)  
 [<span data-ttu-id="6aa52-141">如何：使用發行精靈發行 ClickOnce 應用程式</span><span class="sxs-lookup"><span data-stu-id="6aa52-141">How to: Publish a ClickOnce Application using the Publish Wizard</span></span>](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)
