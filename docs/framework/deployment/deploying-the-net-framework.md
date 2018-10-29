---
title: 部署 .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac17993a4980e96cbd05fc2523567138e7b56262
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196437"
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="2c0ac-102">部署 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2c0ac-102">Deploying the .NET Framework</span></span>
<span data-ttu-id="2c0ac-103">本節 .NET Framework 文件為想要與應用程式一起安裝 .NET Framework 的開發人員，和想要在網路上部署 .NET Framework 系統管理員提供資訊。</span><span class="sxs-lookup"><span data-stu-id="2c0ac-103">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="2c0ac-104">它也討論與部署相關的啟用及重新啟動問題，以及如何監視 .NET Framework 安裝進度。</span><span class="sxs-lookup"><span data-stu-id="2c0ac-104">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c0ac-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="2c0ac-105">In This Section</span></span>  
 [<span data-ttu-id="2c0ac-106">開發人員部署手冊</span><span class="sxs-lookup"><span data-stu-id="2c0ac-106">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 <span data-ttu-id="2c0ac-107">說明開發人員如何將 .NET Framework 隨使用者的應用程式安裝在其電腦上。</span><span class="sxs-lookup"><span data-stu-id="2c0ac-107">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="2c0ac-108">系統管理員部署手冊</span><span class="sxs-lookup"><span data-stu-id="2c0ac-108">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
 <span data-ttu-id="2c0ac-109">說明系統管理員如何使用 System Center Configuration Manager (SCCM)，在整個網路上部署 .NET Framework 及其系統相依性。</span><span class="sxs-lookup"><span data-stu-id="2c0ac-109">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>  
  
 [<span data-ttu-id="2c0ac-110">在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數</span><span class="sxs-lookup"><span data-stu-id="2c0ac-110">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
 <span data-ttu-id="2c0ac-111">描述可防止在任何可能的情況下重新開機的重新啟動管理員，並說明安裝 .NET Framework 的應用程式如何利用 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="2c0ac-111">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="2c0ac-112">如何：取得 .NET Framework 4.5 安裝程式的進度</span><span class="sxs-lookup"><span data-stu-id="2c0ac-112">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="2c0ac-113">描述如何以無訊息模式啟動並追蹤 .NET Framework 安裝程序，並同時顯示您自己的安裝進度檢視。</span><span class="sxs-lookup"><span data-stu-id="2c0ac-113">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="2c0ac-114">.NET Framework 初始化錯誤：管理使用者體驗</span><span class="sxs-lookup"><span data-stu-id="2c0ac-114">.NET Framework Initialization Errors: Managing the User Experience</span></span>](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="2c0ac-115">說明 .NET Framework 應用程式需要無效或未安裝在使用者電腦上的 CLR 版本時，會發生什麼事、如何解決這些錯誤，以及如何控制向使用者顯示的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="2c0ac-115">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="2c0ac-116">如何：偵錯 CLR 啟用問題</span><span class="sxs-lookup"><span data-stu-id="2c0ac-116">How to: Debug CLR Activation Issues</span></span>](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="2c0ac-117">說明如何檢視並偵錯 CLR 啟用記錄，解決讓您的應用程式搭配正確的 CLR 版本執行時時可能發生的問題。</span><span class="sxs-lookup"><span data-stu-id="2c0ac-117">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0ac-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="2c0ac-118">See Also</span></span>  
- [<span data-ttu-id="2c0ac-119">開發指南</span><span class="sxs-lookup"><span data-stu-id="2c0ac-119">Development Guide</span></span>](../../../docs/framework/development-guide.md)
