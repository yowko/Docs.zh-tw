---
title: 何時將 Windows 容器部署到 Azure 容器實體 (ACI)
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |何時將 Windows 容器部署到 Azure 容器實體 (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 6c889db6f0475f24a196144c7fb62faec4c173ed
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989151"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="1f99c-103">何時將 Windows 容器部署到 Azure 容器實體 (ACI)</span><span class="sxs-lookup"><span data-stu-id="1f99c-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="1f99c-104">Azure 容器實例的主要價值主張是,您可以立即向其部署容器,並且不需要維護該環境,無需升級/修補基礎操作系統或 VM,所有這些都是透明的,只需將容器部署到即用型環境中即可。</span><span class="sxs-lookup"><span data-stu-id="1f99c-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don't need to maintain that environment, you don't need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="1f99c-105">要使用 ACI 的原因和方案與將 Azure VM 與容器一起使用時的主要方案類似,因此,使用 Azure 容器實例的主要方案基本上是:</span><span class="sxs-lookup"><span data-stu-id="1f99c-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="1f99c-106">**開發/測試機制**</span><span class="sxs-lookup"><span data-stu-id="1f99c-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="1f99c-107">**工作自動化**</span><span class="sxs-lookup"><span data-stu-id="1f99c-107">**Task automation**</span></span>
- <span data-ttu-id="1f99c-108">**CI/CD 代理程式**</span><span class="sxs-lookup"><span data-stu-id="1f99c-108">**CI/CD agents**</span></span>
- <span data-ttu-id="1f99c-109">**小規模/規模批量處理**</span><span class="sxs-lookup"><span data-stu-id="1f99c-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="1f99c-110">**簡單的 Web 應用程式**</span><span class="sxs-lookup"><span data-stu-id="1f99c-110">**Simple web apps**</span></span>

<span data-ttu-id="1f99c-111">簡單的 Web 應用方案對於 ACI 來說是一個公平的方案,但考慮到在 ACI 中,每個容器映射只能有一個容器實例,因此您不會具有高可用性,並且只有有限的可擴充性。</span><span class="sxs-lookup"><span data-stu-id="1f99c-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won't have high availability and only have limited scalability.</span></span>

<span data-ttu-id="1f99c-112">但是,即使 ACI 被視為基礎結構,因為它只提供單個容器實例,但與具有 Windows Server 的常規 Azure VM 相比,也具有巨大的優勢。</span><span class="sxs-lookup"><span data-stu-id="1f99c-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="1f99c-113">使用 ACI,只需將容器部署到自我維護的環境中,只需為這些容器付費。</span><span class="sxs-lookup"><span data-stu-id="1f99c-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="1f99c-114">您無需維護/更新/修補 VM,因此對於大多數可能將 VM 與容器一起使用的方案來說,這是一個更好的平臺。</span><span class="sxs-lookup"><span data-stu-id="1f99c-114">You don't need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="1f99c-115">使用 ACI 是直接的,您只需部署一個容器,就無需創建僅部署容器的 VM 環境。</span><span class="sxs-lookup"><span data-stu-id="1f99c-115">Using ACI is straight forward, you just deploy a container, there's no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="1f99c-116">Azure 容器實例 (ACI) 的主要優點是:</span><span class="sxs-lookup"><span data-stu-id="1f99c-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="1f99c-117">執行容器而不管理伺服器</span><span class="sxs-lookup"><span data-stu-id="1f99c-117">Run containers without managing servers</span></span>
- <span data-ttu-id="1f99c-118">按需使用容器提高敏捷性</span><span class="sxs-lookup"><span data-stu-id="1f99c-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="1f99c-119">使用單個命令,以前所未有的簡單性和速度將容器部署到雲中。</span><span class="sxs-lookup"><span data-stu-id="1f99c-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="1f99c-120">使用虛擬機器管理程式隔離保護應用程式</span><span class="sxs-lookup"><span data-stu-id="1f99c-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="1f99c-121">簡而言之,藉助 ACI,您可以快速開發應用,而無需管理虛擬機或學習新工具。</span><span class="sxs-lookup"><span data-stu-id="1f99c-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="1f99c-122">它只是您的應用程式,在容器中,在雲中運行。</span><span class="sxs-lookup"><span data-stu-id="1f99c-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="1f99c-123">[前一個](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [下一個](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="1f99c-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
