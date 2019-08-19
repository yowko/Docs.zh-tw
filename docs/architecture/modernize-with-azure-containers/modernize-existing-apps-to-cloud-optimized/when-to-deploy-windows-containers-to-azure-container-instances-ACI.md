---
title: 將 Windows 容器部署至 Azure 容器實例 (ACI) 的時機
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |將 Windows 容器部署至 Azure 容器實例 (ACI) 的時機
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577931"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="0248a-103">將 Windows 容器部署至 Azure 容器實例 (ACI) 的時機</span><span class="sxs-lookup"><span data-stu-id="0248a-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="0248a-104">Azure 容器實例的主要價值主張是, 您可以立即將容器部署到該環境, 而不需要維護該環境, 您不需要升級/修補基礎作業系統或 Vm, 這一切都是透明的, 而且您剛部署容器進入立即可用的環境。</span><span class="sxs-lookup"><span data-stu-id="0248a-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="0248a-105">當您使用 Azure Vm 搭配容器時, 您會想要使用 ACI 的原因和案例, 基本上, 使用 Azure 容器實例的主要案例如下:</span><span class="sxs-lookup"><span data-stu-id="0248a-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="0248a-106">**開發/測試案例**</span><span class="sxs-lookup"><span data-stu-id="0248a-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="0248a-107">**任務自動化**</span><span class="sxs-lookup"><span data-stu-id="0248a-107">**Task automation**</span></span>
- <span data-ttu-id="0248a-108">**CI/CD 代理程式**</span><span class="sxs-lookup"><span data-stu-id="0248a-108">**CI/CD agents**</span></span>
- <span data-ttu-id="0248a-109">**小型/調整批次處理**</span><span class="sxs-lookup"><span data-stu-id="0248a-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="0248a-110">**簡單的 web 應用程式**</span><span class="sxs-lookup"><span data-stu-id="0248a-110">**Simple web apps**</span></span>

<span data-ttu-id="0248a-111">簡單的 web 應用程式案例是 ACI 的公平案例, 但請將其納入考慮, 因為在 ACI 中, 每個容器映射只能有一個容器實例, 所以您不會有高可用性, 而且只有有限的擴充性。</span><span class="sxs-lookup"><span data-stu-id="0248a-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="0248a-112">不過, 即使 ACI 被視為基礎結構, 因為它只提供單一容器實例, 相較于使用 Windows Server 的一般 Azure Vm, 這項優點相當大。</span><span class="sxs-lookup"><span data-stu-id="0248a-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="0248a-113">使用 ACI 時, 您只需將容器部署到自我維護的環境, 就能為這些容器付費。</span><span class="sxs-lookup"><span data-stu-id="0248a-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="0248a-114">您不需要維護/更新/修補 Vm, 因此在大部分情況下, 您可能會將 Vm 與容器搭配使用, 這是更好的平臺。</span><span class="sxs-lookup"><span data-stu-id="0248a-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="0248a-115">使用 ACI 是直接的, 您只要部署容器, 就不需要建立您剛部署容器的 VM 環境。</span><span class="sxs-lookup"><span data-stu-id="0248a-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="0248a-116">Azure 容器實例 (ACI) 的主要優點如下:</span><span class="sxs-lookup"><span data-stu-id="0248a-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="0248a-117">在不管理伺服器的情況下執行容器</span><span class="sxs-lookup"><span data-stu-id="0248a-117">Run containers without managing servers</span></span>
- <span data-ttu-id="0248a-118">使用容器隨選增加靈活性</span><span class="sxs-lookup"><span data-stu-id="0248a-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="0248a-119">使用單一命令, 以前所未有的簡單性和速度將容器部署到雲端。</span><span class="sxs-lookup"><span data-stu-id="0248a-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="0248a-120">以虛擬程式隔離來保護應用程式</span><span class="sxs-lookup"><span data-stu-id="0248a-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="0248a-121">簡單地說, 透過 ACI, 您可以快速開發應用程式, 而不需要管理虛擬機器或學習新工具。</span><span class="sxs-lookup"><span data-stu-id="0248a-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="0248a-122">它只是您在雲端中執行的應用程式, 位於容器中。</span><span class="sxs-lookup"><span data-stu-id="0248a-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="0248a-123">[上一頁](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [下一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="0248a-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
