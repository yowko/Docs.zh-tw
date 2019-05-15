---
title: 選擇容器應用程式的 Azure 計算平台
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |選擇容器型應用程式的 Azure 計算平台
ms.date: 05/04/2018
ms.openlocfilehash: 28e103c67f47d63582384c9ab468a5f631b5ce9e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638983"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="e5019-103">選擇容器應用程式的 Azure 計算平台</span><span class="sxs-lookup"><span data-stu-id="e5019-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="e5019-104">閱讀前幾節之後，您已經注意到，則 Azure 會是開放式的雲端，可提供多個選項。</span><span class="sxs-lookup"><span data-stu-id="e5019-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="e5019-105">您可以使用最適合您的需求，不過，它也會呈現有關容器化應用程式，您應該使用哪些產品/技術問題。</span><span class="sxs-lookup"><span data-stu-id="e5019-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="e5019-106">作為*預設為*建議，以下是主要的準則，建議您在本指南中：</span><span class="sxs-lookup"><span data-stu-id="e5019-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="e5019-107">**單一的單體式應用程式：** 選擇 Azure App Service</span><span class="sxs-lookup"><span data-stu-id="e5019-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="e5019-108">**多層式架構應用程式：** 如果您有單一或少數的後端服務，請選擇協調器，例如 Azure Kubernetes Service (AKS)、 Service Fabric (SF) 或 App Service</span><span class="sxs-lookup"><span data-stu-id="e5019-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="e5019-109">**Linux 的微服務：** 選擇 AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="e5019-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
- <span data-ttu-id="e5019-110">**Windows 的微服務：** 選擇 Service Fabric</span><span class="sxs-lookup"><span data-stu-id="e5019-110">**Windows microservices:** Choose Service Fabric</span></span>
- <span data-ttu-id="e5019-111">**無伺服器函式 （&) 事件處理常式：** 選擇 Azure 函式</span><span class="sxs-lookup"><span data-stu-id="e5019-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="e5019-112">**大規模的批次：** 選擇 Azure 批次</span><span class="sxs-lookup"><span data-stu-id="e5019-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="e5019-113">不過，這項建議應該隨著一小段 salt，如產品的選擇取決於特定應用程式的需求和特性。</span><span class="sxs-lookup"><span data-stu-id="e5019-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="e5019-114">一開始它們看起來類似的型別時，即使並非所有應用程式都是相同的。</span><span class="sxs-lookup"><span data-stu-id="e5019-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="e5019-115">在應用程式的需求的更深入的分析之後, 所選擇的產品可能不同。</span><span class="sxs-lookup"><span data-stu-id="e5019-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="e5019-116">不過，做為起點，最好能夠從何處開始評估的初始指導方針，並且測試根據特定優先權。</span><span class="sxs-lookup"><span data-stu-id="e5019-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="e5019-117">在下一個圖中，您可以分析詳細的決策表時更全域項目。</span><span class="sxs-lookup"><span data-stu-id="e5019-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="e5019-118">請注意如何基礎作業系統 （Windows 與。因為某些 orchestrator 更成熟 Linux 容器和 Windows 容器上其他 Linux) 也可以是決策因素。</span><span class="sxs-lookup"><span data-stu-id="e5019-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="e5019-119">比方說，Linux 容器是在 Kubernetes 中 (在 Azure 中的 AKS) 但較不成熟，Service Fabric 上非常成熟。</span><span class="sxs-lookup"><span data-stu-id="e5019-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="e5019-120">相反地，Windows 容器是較為成熟 （2017 年發行） 的 Service Fabric 中和在 AKS 中較不成熟。</span><span class="sxs-lookup"><span data-stu-id="e5019-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="e5019-121">不過，OS 成熟度的這些差異會在未來淡出多個平台會有類似的 OS 成熟度並決定將提供詳細說明根據您的應用程式可能需要或根據每個平台生態系統的特定功能的喜好設定原因。</span><span class="sxs-lookup"><span data-stu-id="e5019-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="e5019-122">[上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [下一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="e5019-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
