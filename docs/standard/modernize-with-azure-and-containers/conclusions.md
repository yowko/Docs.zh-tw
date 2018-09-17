---
title: 結論
description: 將現有.NET 應用程式與 Azure 雲端和 Windows 容器現代化 |結論
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: af6151d04622c72acdb7f27ebb220bf611418b4c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743965"
---
# <a name="conclusions"></a><span data-ttu-id="1ca3c-103">結論</span><span class="sxs-lookup"><span data-stu-id="1ca3c-103">Conclusions</span></span>

- <span data-ttu-id="1ca3c-104">以容器為基礎的解決方案最終提供的成本節省效益。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-104">Container-based solutions ultimately provide cost savings benefits.</span></span> <span data-ttu-id="1ca3c-105">容器是部署問題的解決方案，因為它們會移除在生產環境中的相依性不存在所造成的不便。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-105">Containers are a solution to deployment problems because they remove the friction caused by an absence of dependencies in production environments.</span></span> <span data-ttu-id="1ca3c-106">藉由移除這些問題，它會大幅改善開發/測試、 DevOps 和生產環境的作業。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-106">By removing those issues, it improves Dev/Test, DevOps, and production operations significantly.</span></span>

- <span data-ttu-id="1ca3c-107">Docker 容器會變成任何以伺服器為基礎之應用程式或服務的標準部署單位。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-107">A Docker container is becoming the standard unit of deployment for any server-based application or service.</span></span>

- <span data-ttu-id="1ca3c-108">針對生產環境，您應該使用協調器 （例如 Service Fabric 或 Kubernetes） 來裝載可調整 Windows 容器型應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-108">For production environments, you should use an orchestrator (like Service Fabric or Kubernetes) to host scalable Windows Containers­­–based applications.</span></span>

- <span data-ttu-id="1ca3c-109">主控容器的 azure Vm 是快速又簡單的方式，在雲端中建立小型的開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-109">Azure VMs hosting containers are a fast and simple way to create small Dev/Test environments in the cloud.</span></span>

- <span data-ttu-id="1ca3c-110">Azure SQL Database 受控執行個體，建議您使用預設將您的關聯式資料庫移轉至 Azure 的現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-110">Azure SQL Database Managed Instance is recommended by default when migrating your relational databases from existing applications to Azure.</span></span>

- <span data-ttu-id="1ca3c-111">Visual Studio 2017 和 Image2Docker 是基本的工具，讓您開始將您現有的.NET 應用程式與 Windows 容器現代化加速取得啟動的學習曲線。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-111">Visual Studio 2017 and Image2Docker are basic tools for you to start modernizing your existing .NET applications with Windows Containers by accelerating the getting started learning curve.</span></span>

- <span data-ttu-id="1ca3c-112">放置在生產環境中的容器化應用程式時將會永遠建立，或採用 DevOps 文化特性和 CI/CD 管線，例如 Azure DevOps 服務或 Jenkins 的 DevOps 工具。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-112">When placing containerized applications in production you will always create or adopt a DevOps culture and DevOps tools for CI/CD pipelines, like Azure DevOps Services or Jenkins.</span></span>

- <span data-ttu-id="1ca3c-113">Microsoft Azure 提供最全面且最完整的環境，以將您現有的.NET Framework 應用程式，Windows 容器、 雲端基礎結構與 PaaS 服務現代化。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-113">Microsoft Azure provides the most comprehensive and complete environment to modernize your existing .NET Framework applications with Windows Containers, cloud infrastructure and PaaS services.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="1ca3c-114">上一步</span><span class="sxs-lookup"><span data-stu-id="1ca3c-114">Previous</span></span>](walkthroughs-technical-get-started-overview.md)