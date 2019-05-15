---
title: 將 Windows 容器部署至 Azure Container Instances (ACI) 中的時機
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |將 Windows 容器部署至 Azure Container Instances (ACI) 中的時機
ms.date: 04/29/2018
ms.openlocfilehash: 9bfa0688d07bd04964a1b28f688f125b5bcd2299
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638929"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="f5758-103">將 Windows 容器部署至 Azure Container Instances (ACI) 中的時機</span><span class="sxs-lookup"><span data-stu-id="f5758-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="f5758-104">Azure 容器執行個體的主要價值主張是立即，您可以將容器部署到它，而且您不需要維護該環境，您不需要升級/修補基礎作業系統或所有的而言是透明的 Vm，並只需將部署準備使用環境的容器。</span><span class="sxs-lookup"><span data-stu-id="f5758-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="f5758-105">原因，以及在您想要使用 ACI 案例中的主要案例類似當您使用 Azure Vm 與容器，所以基本上，使用 Azure Container Instances 的主要案例包括：</span><span class="sxs-lookup"><span data-stu-id="f5758-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="f5758-106">**開發/測試案例**</span><span class="sxs-lookup"><span data-stu-id="f5758-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="f5758-107">**工作自動化**</span><span class="sxs-lookup"><span data-stu-id="f5758-107">**Task automation**</span></span>
- <span data-ttu-id="f5758-108">**CI/CD 代理程式**</span><span class="sxs-lookup"><span data-stu-id="f5758-108">**CI/CD agents**</span></span>
- <span data-ttu-id="f5758-109">**小型/擴展批次處理**</span><span class="sxs-lookup"><span data-stu-id="f5758-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="f5758-110">**簡單 web 應用程式**</span><span class="sxs-lookup"><span data-stu-id="f5758-110">**Simple web apps**</span></span>

<span data-ttu-id="f5758-111">簡單的 web 應用程式案例 ACI 公平案例，但請考慮在 ACI 中只能有單一的容器執行個體，每個容器映像，因為您不需要高可用性，並只會有有限延展性。</span><span class="sxs-lookup"><span data-stu-id="f5758-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="f5758-112">不過，即使在 ACI 被視為基礎結構，因為它只是提供單一容器執行個體，是相較於一般的 Azure 虛擬機器與 Windows Server 是一大福音。</span><span class="sxs-lookup"><span data-stu-id="f5758-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="f5758-113">使用 ACI，只需將容器部署到自我維護的環境，並只支付這些容器。</span><span class="sxs-lookup"><span data-stu-id="f5758-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="f5758-114">您不需要維護/更新/修補的 Vm，所以大部分的情況下，您也可以使用 Vm 與容器的太多的完美平台。</span><span class="sxs-lookup"><span data-stu-id="f5758-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="f5758-115">使用 ACI 很簡單，您只是將容器部署，則不需要建立 VM 環境，您只需將容器部署。</span><span class="sxs-lookup"><span data-stu-id="f5758-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="f5758-116">Azure Container Instances (ACI) 的主要優點為：</span><span class="sxs-lookup"><span data-stu-id="f5758-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="f5758-117">執行容器而不必管理伺服器</span><span class="sxs-lookup"><span data-stu-id="f5758-117">Run containers without managing servers</span></span>
- <span data-ttu-id="f5758-118">隨選容器增加彈性</span><span class="sxs-lookup"><span data-stu-id="f5758-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="f5758-119">將容器部署至雲端，前所未有的簡潔且高速 — 使用單一命令。</span><span class="sxs-lookup"><span data-stu-id="f5758-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="f5758-120">利用 hypervisor 隔離保護應用程式</span><span class="sxs-lookup"><span data-stu-id="f5758-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="f5758-121">簡單地說，透過 ACI 中，您可以開發應用程式快速而不需要管理虛擬機器或不必學習新工具。</span><span class="sxs-lookup"><span data-stu-id="f5758-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="f5758-122">它是只是您的應用程式，在容器中，在雲端中執行。</span><span class="sxs-lookup"><span data-stu-id="f5758-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="f5758-123">[上一頁](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [下一頁](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="f5758-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
