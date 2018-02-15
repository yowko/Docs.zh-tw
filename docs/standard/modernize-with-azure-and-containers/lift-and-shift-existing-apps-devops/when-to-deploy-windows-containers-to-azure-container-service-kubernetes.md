---
title: "當 Azure 容器服務 (也就是 Kubernetes) 部署 Windows 容器"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |當 Azure 容器服務 (也就是 Kubernetes) 部署 Windows 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f7ed0c9ebf1c80ae6cae4311b2682d3cc161623
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="c88b1-103">當 Azure 容器服務 (也就是 Kubernetes) 部署 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="c88b1-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="c88b1-104">Azure 容器服務進行最佳化的熱門的開放原始碼工具和技術的組態，特別針對 Azure。</span><span class="sxs-lookup"><span data-stu-id="c88b1-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="c88b1-105">您會取得開啟的方案，提供可攜性適用於您的容器和應用程式組態。</span><span class="sxs-lookup"><span data-stu-id="c88b1-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="c88b1-106">您選取大小、 主機、 數目和 orchestrator 工具。</span><span class="sxs-lookup"><span data-stu-id="c88b1-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="c88b1-107">Azure 容器服務會為您處理基礎結構。</span><span class="sxs-lookup"><span data-stu-id="c88b1-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="c88b1-108">如果您已經使用開放原始碼 orchestrators Kubernetes、 Docker Swarm，或 DC/OS 等，您不需要變更您現有的管理作法，若要將容器的工作負載移到雲端。</span><span class="sxs-lookup"><span data-stu-id="c88b1-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="c88b1-109">使用您已經熟悉的而且您選擇的 orchestrator 透過標準的應用程式開發介面端點連線時，應用程式管理工具。</span><span class="sxs-lookup"><span data-stu-id="c88b1-109">Use the application management tools that you're already familiar with, and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="c88b1-110">如果您使用 Linux Docker 容器，但它們也支援 Windows 容器 （部分前面，一些還要新，取決於 orchestrator） 時，所有這些 orchestrators 是 2017 的成熟的環境。</span><span class="sxs-lookup"><span data-stu-id="c88b1-110">All these orchestrators are mature environments if you are using Linux Docker containers, but they also support Windows Containers as of 2017 (some earlier, some more recently, depending on the orchestrator).</span></span>

<span data-ttu-id="c88b1-111">例如，在 Kubernetes，對支援容器是原生 （第一級棒），所以使用 Windows 容器上 Kubernetes 也是非常有效且可靠 （直到預覽中及早切換 2017年）。</span><span class="sxs-lookup"><span data-stu-id="c88b1-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also very effective and reliable (in preview until early fall 2017).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="c88b1-112">[上一頁](when-to-deploy-windows-containers-to-service-fabric.md)
[下一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="c88b1-112">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
