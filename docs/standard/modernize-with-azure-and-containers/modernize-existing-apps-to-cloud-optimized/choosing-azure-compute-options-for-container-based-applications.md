---
title: 選擇容器應用程式的 Azure 運算平台
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器 |選擇容器應用程式的 Azure 運算平台
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958008"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="38098-103">選擇容器應用程式的 Azure 運算平台</span><span class="sxs-lookup"><span data-stu-id="38098-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="38098-104">您已注意到閱讀上一節之後，Azure 會是提供了多個選項在開啟的雲端。</span><span class="sxs-lookup"><span data-stu-id="38098-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="38098-105">您可以使用最適合您的需求，不過，它也會提供諸如您容器化應用程式應該使用哪些產品/技術有關的問題。</span><span class="sxs-lookup"><span data-stu-id="38098-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="38098-106">做為*依預設*建議中，以下是建議您在本指南中的主要標準：</span><span class="sxs-lookup"><span data-stu-id="38098-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

  - <span data-ttu-id="38098-107">**單一龐大的應用程式：** 選擇 Azure App Service</span><span class="sxs-lookup"><span data-stu-id="38098-107">**Single monolithic app:** Choose Azure App Service</span></span>
  - <span data-ttu-id="38098-108">**多層式架構應用程式：** 選擇 orchestrators，例如 Azure Kubernetes 服務 (AKS)、 服務網狀架構 (SF) 或應用程式服務，如果您有一部或幾個後端服務</span><span class="sxs-lookup"><span data-stu-id="38098-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
  - <span data-ttu-id="38098-109">**Linux microservices:** 選擇 AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="38098-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
  - <span data-ttu-id="38098-110">**Windows microservices:** 選擇 Service Fabric</span><span class="sxs-lookup"><span data-stu-id="38098-110">**Windows microservices:** Choose Service Fabric</span></span>
  - <span data-ttu-id="38098-111">**無伺服器函式 （& s) 事件處理常式：** 選擇 Azure 函式</span><span class="sxs-lookup"><span data-stu-id="38098-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
  - <span data-ttu-id="38098-112">**大型批次：** 選擇 Azure 批次</span><span class="sxs-lookup"><span data-stu-id="38098-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="38098-113">不過，這項建議應採取的 salt 捏合與產品的選取項目會取決於特定應用程式的需求和特性。</span><span class="sxs-lookup"><span data-stu-id="38098-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="38098-114">一開始它們看起來類似的類型時，即使並非所有應用程式都是相同的。</span><span class="sxs-lookup"><span data-stu-id="38098-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="38098-115">應用程式的需求更深入分析後, 所選擇的產品可能會不同。</span><span class="sxs-lookup"><span data-stu-id="38098-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="38098-116">但是，做為起點，最好能夠從何處開始評估初始的指導方針，而且測試會依據特定的優先順序。</span><span class="sxs-lookup"><span data-stu-id="38098-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="38098-117">在下一個圖中，您可以分析更通用時詳細的決策表。</span><span class="sxs-lookup"><span data-stu-id="38098-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="38098-118">請注意如何基礎作業系統 （Windows 與。Linux) 也可以決策因數某些 orchestrators 更成熟 Linux 容器上與其他 Windows 容器上也不一樣。</span><span class="sxs-lookup"><span data-stu-id="38098-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="38098-119">比方說，Linux 容器是非常成熟 Kubernetes (在 Azure 中 AKS) 中但較不成熟服務網狀架構上。</span><span class="sxs-lookup"><span data-stu-id="38098-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="38098-120">相反地，Windows 容器是成熟 Service Fabric （2017 年發行） 中，較不成熟 AKS 中。</span><span class="sxs-lookup"><span data-stu-id="38098-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="38098-121">不過，OS 成熟度的這些差異會在未來淡出多個平台會比較 OS 成熟度，以及擁有決策會配置更詳細的喜好設定，根據您的應用程式可能需要或根據每個平台生態系統的特定功能原因。</span><span class="sxs-lookup"><span data-stu-id="38098-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="38098-122">[上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[下一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="38098-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
