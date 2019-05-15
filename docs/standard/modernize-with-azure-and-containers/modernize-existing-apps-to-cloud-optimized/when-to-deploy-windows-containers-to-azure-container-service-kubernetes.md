---
title: 將 Windows 容器部署至 Azure Container Service (亦即 Kubernetes) 的時機
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |將 Windows 容器部署至 Azure Container Service (亦即 Kubernetes) 的時機
ms.date: 04/30/2018
ms.openlocfilehash: 921767b52f2b0d80f2d31d972b65ac7551d2f7c5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643564"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="72bc8-103">將 Windows 容器部署至 Azure Container Service (亦即 Kubernetes) 的時機</span><span class="sxs-lookup"><span data-stu-id="72bc8-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="72bc8-104">Azure Container Service 的最佳化組態受歡迎的開放原始碼工具和技術特別適用於 Azure。</span><span class="sxs-lookup"><span data-stu-id="72bc8-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="72bc8-105">您取得開啟的方案，可提供適用於您容器和應用程式組態的可攜性。</span><span class="sxs-lookup"><span data-stu-id="72bc8-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="72bc8-106">您選取大小、 主機數量及協調工具。</span><span class="sxs-lookup"><span data-stu-id="72bc8-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="72bc8-107">Azure Container Service 會為您處理基礎結構。</span><span class="sxs-lookup"><span data-stu-id="72bc8-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="72bc8-108">如果您已經使用 Kubernetes、 Docker Swarm 或 DC/OS 等的開放原始碼協調器，您不需要變更您現有的管理作法，將容器工作負載移至雲端。</span><span class="sxs-lookup"><span data-stu-id="72bc8-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="72bc8-109">使用您已經熟悉的應用程式管理工具，並透過標準 API 端點連線，為您選擇的 orchestrator。</span><span class="sxs-lookup"><span data-stu-id="72bc8-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="72bc8-110">如果您使用 Linux 的 Docker 容器，但可能只會處於預覽狀態適用於 Windows 容器，所有這些 orchestrator 是成熟的環境。</span><span class="sxs-lookup"><span data-stu-id="72bc8-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="72bc8-111">例如，在 Kubernetes 中，支援容器是原生 （第一等公民），因此在 Kubernetes 上使用 Windows 容器也很有效 （在 ACS 中 2018 年初起為預覽版）。</span><span class="sxs-lookup"><span data-stu-id="72bc8-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="72bc8-112">重要事項：進化版和 「 多個 PaaS"kubernetes 的 ACS (Azure Container Service) 的版本不 AKS (Azure Kubernetes Service)，不過，自 Q2 2018 起，仍不支援 Windows 容器，但它即將推出支援。</span><span class="sxs-lookup"><span data-stu-id="72bc8-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="72bc8-113">[上一頁](when-to-deploy-windows-containers-to-service-fabric.md)
>[下一頁](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="72bc8-113">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
