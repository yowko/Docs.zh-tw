---
title: 當 Azure 容器執行個體 (ACI) 部署 Windows 容器
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器 |當 Azure 容器執行個體 (ACI) 部署 Windows 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 3dc23c96543d9611763b571105f52b150dfec06f
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="157d1-103">當 Azure 容器執行個體 (ACI) 部署 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="157d1-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="157d1-104">Azure 容器執行個體主要價值主張是以立即開始，您可以將容器部署它，而且您不需要維護該環境，您不需要升級/修補程式 underlaying 作業系統或 Vm，所有透明的而且您只部署已備妥要使用環境的容器。</span><span class="sxs-lookup"><span data-stu-id="157d1-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlaying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="157d1-105">原因和案例時，您會想要使用 ACI 類似的主要案例搭配使用 Azure Vm 和容器，因此基本上，使用 Azure 容器執行個體的主要案例包括：</span><span class="sxs-lookup"><span data-stu-id="157d1-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

-   <span data-ttu-id="157d1-106">**開發/測試案例**</span><span class="sxs-lookup"><span data-stu-id="157d1-106">**Dev/Test scenarios**</span></span>
-   <span data-ttu-id="157d1-107">**工作自動化**</span><span class="sxs-lookup"><span data-stu-id="157d1-107">**Task automation**</span></span>
-   <span data-ttu-id="157d1-108">**CI/CD 代理程式**</span><span class="sxs-lookup"><span data-stu-id="157d1-108">**CI/CD agents**</span></span>
-   <span data-ttu-id="157d1-109">**小型/小數位數批次處理**</span><span class="sxs-lookup"><span data-stu-id="157d1-109">**Small/scale batch processing**</span></span>
-   <span data-ttu-id="157d1-110">**簡單 web 應用程式**</span><span class="sxs-lookup"><span data-stu-id="157d1-110">**Simple web apps**</span></span>

<span data-ttu-id="157d1-111">簡單的 web 應用程式案例是普通的 ACI 狀況，但納入考量，因為 ACI 中只能有單一容器每個執行個體的容器映像，您不需要高可用性，並只具有有限的延展性。</span><span class="sxs-lookup"><span data-stu-id="157d1-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="157d1-112">不過，即使 ACI 會被視為基礎結構，因為它只提供單一容器執行個體，是一大優勢，相較於一般的 Azure Vm 與 Windows Server。</span><span class="sxs-lookup"><span data-stu-id="157d1-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="157d1-113">ACI，只要將容器部署到自我維護的環境與您只需支付這些容器。</span><span class="sxs-lookup"><span data-stu-id="157d1-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="157d1-114">您不需要維護/更新/修補的 Vm，所以較佳 platform 大部分的情況下，您也可以使用 Vm 與容器。</span><span class="sxs-lookup"><span data-stu-id="157d1-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="157d1-115">使用 ACI 直截了當，您只要部署容器，來建立您剛部署容器在 VM 環境不需要。</span><span class="sxs-lookup"><span data-stu-id="157d1-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="157d1-116">Azure 容器執行個體 (ACI) 的主要優點為：</span><span class="sxs-lookup"><span data-stu-id="157d1-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

-   <span data-ttu-id="157d1-117">執行的容器，而不需要管理伺服器</span><span class="sxs-lookup"><span data-stu-id="157d1-117">Run containers without managing servers</span></span>
-   <span data-ttu-id="157d1-118">增加靈活性視容器</span><span class="sxs-lookup"><span data-stu-id="157d1-118">Increase agility with containers on demand</span></span>
-   <span data-ttu-id="157d1-119">部署至雲端與前所未有的簡單和速度的容器，使用單一命令。</span><span class="sxs-lookup"><span data-stu-id="157d1-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span> 
-   <span data-ttu-id="157d1-120">安全 hypervisor 隔離的應用程式</span><span class="sxs-lookup"><span data-stu-id="157d1-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="157d1-121">簡單地說，ACI 與您可以快速而不需要管理虛擬機器或需要了解新的工具開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="157d1-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="157d1-122">只要您的應用程式，在容器中，在雲端中執行它。</span><span class="sxs-lookup"><span data-stu-id="157d1-122">It's just your application, in a container, running in the cloud.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="157d1-123">[上一頁](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[下一頁](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="157d1-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
