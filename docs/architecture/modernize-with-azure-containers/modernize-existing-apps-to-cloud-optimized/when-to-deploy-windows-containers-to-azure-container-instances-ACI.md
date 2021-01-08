---
title: '當您將 Windows 容器部署至 Azure 容器實例時 (ACI) '
description: '使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |當您將 Windows 容器部署至 Azure 容器實例時 (ACI) '
ms.date: 12/21/2020
ms.openlocfilehash: 556fe7cbec7d259db9ec886b777feda9eed09116
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025129"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="d142e-103">當您將 Windows 容器部署至 Azure 容器實例時 (ACI) </span><span class="sxs-lookup"><span data-stu-id="d142e-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="d142e-104">Azure 容器實例的主要價值主張是您可以立即將容器部署到該環境，而且您不需要維護該環境，您就不需要升級/修補基礎作業系統或 Vm，而且全都是透明的，而且只是將容器部署到現成可用的環境。</span><span class="sxs-lookup"><span data-stu-id="d142e-104">The main value proposition of Azure Container Instances is that you can right away deploy containers to it and you don't need to maintain that environment, you don't need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="d142e-105">當您使用 Azure Vm 搭配容器時，您想要使用 ACI 的原因和案例，基本上是使用 Azure 容器實例的主要案例如下：</span><span class="sxs-lookup"><span data-stu-id="d142e-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="d142e-106">**開發/測試案例**</span><span class="sxs-lookup"><span data-stu-id="d142e-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="d142e-107">**工作自動化**</span><span class="sxs-lookup"><span data-stu-id="d142e-107">**Task automation**</span></span>
- <span data-ttu-id="d142e-108">**CI/CD 代理程式**</span><span class="sxs-lookup"><span data-stu-id="d142e-108">**CI/CD agents**</span></span>
- <span data-ttu-id="d142e-109">**小規模/調整批次處理**</span><span class="sxs-lookup"><span data-stu-id="d142e-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="d142e-110">**簡單的 web 應用程式**</span><span class="sxs-lookup"><span data-stu-id="d142e-110">**Simple web apps**</span></span>

<span data-ttu-id="d142e-111">簡單的 web 應用程式案例是 ACI 的公平案例，但請考慮，因為在 ACI 中，每個容器映射只能有一個容器實例，您將不會有高可用性，而且只會有有限的擴充性。</span><span class="sxs-lookup"><span data-stu-id="d142e-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won't have high availability and only have limited scalability.</span></span>

<span data-ttu-id="d142e-112">不過，即使 ACI 被視為基礎結構，因為它只提供單一容器實例，相較于使用 Windows Server 的一般 Azure Vm，有相當大的好處。</span><span class="sxs-lookup"><span data-stu-id="d142e-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="d142e-113">使用 ACI，您只需將容器部署到自我維護環境中，就可以為這些容器付費。</span><span class="sxs-lookup"><span data-stu-id="d142e-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="d142e-114">您不需要維護/更新/修補 Vm，因此在大部分情況下，您可能會使用具有容器的 Vm，因此是更好的平臺。</span><span class="sxs-lookup"><span data-stu-id="d142e-114">You don't need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="d142e-115">使用 ACI 相當簡單，您只需要部署容器，就不需要建立您只部署容器的 VM 環境。</span><span class="sxs-lookup"><span data-stu-id="d142e-115">Using ACI is straight forward, you just deploy a container, there's no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="d142e-116">Azure 容器實例 (ACI) 的主要優點如下：</span><span class="sxs-lookup"><span data-stu-id="d142e-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="d142e-117">在不管理伺服器的情況下執行容器</span><span class="sxs-lookup"><span data-stu-id="d142e-117">Run containers without managing servers</span></span>
- <span data-ttu-id="d142e-118">隨選容器提高靈活性</span><span class="sxs-lookup"><span data-stu-id="d142e-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="d142e-119">透過單一命令，以前所未有的簡潔性和速度將容器部署至雲端。</span><span class="sxs-lookup"><span data-stu-id="d142e-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="d142e-120">使用虛擬程式隔離來保護應用程式</span><span class="sxs-lookup"><span data-stu-id="d142e-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="d142e-121">簡單地說，您可以透過 ACI 快速開發應用程式，而不需要管理虛擬機器或學習新工具。</span><span class="sxs-lookup"><span data-stu-id="d142e-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="d142e-122">它只是您在雲端中執行的應用程式，在容器中執行。</span><span class="sxs-lookup"><span data-stu-id="d142e-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="d142e-123">[上一個](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md) 
> [下一步](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="d142e-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
