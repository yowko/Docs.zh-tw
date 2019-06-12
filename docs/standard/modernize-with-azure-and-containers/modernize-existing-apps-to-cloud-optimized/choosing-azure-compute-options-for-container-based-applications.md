---
title: 選擇容器應用程式的 Azure 計算平台
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |選擇容器型應用程式的 Azure 計算平台
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833847"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="c7fc6-103">選擇容器應用程式的 Azure 計算平台</span><span class="sxs-lookup"><span data-stu-id="c7fc6-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="c7fc6-104">閱讀前幾節之後，您已經注意到，則 Azure 會是開放式的雲端，可提供多個選項。</span><span class="sxs-lookup"><span data-stu-id="c7fc6-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="c7fc6-105">您可以使用最適合您的需求，不過，它也會呈現有關容器化應用程式，您應該使用哪些產品/技術問題。</span><span class="sxs-lookup"><span data-stu-id="c7fc6-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="c7fc6-106">作為*預設為*建議，以下是主要的準則，建議您在本指南中：</span><span class="sxs-lookup"><span data-stu-id="c7fc6-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="c7fc6-107">**單一的單體式應用程式：** 選擇 Azure App Service</span><span class="sxs-lookup"><span data-stu-id="c7fc6-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="c7fc6-108">**多層式架構應用程式：** 如果您有單一或少數的後端服務，請選擇協調器，例如 Azure Kubernetes Service (AKS) 或 App Service</span><span class="sxs-lookup"><span data-stu-id="c7fc6-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="c7fc6-109">**微服務：** 選擇 AKS or Azure Web Apps for Containers</span><span class="sxs-lookup"><span data-stu-id="c7fc6-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="c7fc6-110">**無伺服器函式 （&) 事件處理常式：** 選擇 Azure 函式</span><span class="sxs-lookup"><span data-stu-id="c7fc6-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="c7fc6-111">**大規模的批次：** 選擇 Azure 批次</span><span class="sxs-lookup"><span data-stu-id="c7fc6-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="c7fc6-112">不過，這項建議應該隨著一小段 salt，如產品的選擇取決於特定應用程式的需求和特性。</span><span class="sxs-lookup"><span data-stu-id="c7fc6-112">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="c7fc6-113">一開始它們看起來類似的型別時，即使並非所有應用程式都是相同的。</span><span class="sxs-lookup"><span data-stu-id="c7fc6-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="c7fc6-114">在應用程式的需求的更深入的分析之後, 所選擇的產品可能不同。</span><span class="sxs-lookup"><span data-stu-id="c7fc6-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="c7fc6-115">不過，做為起點，最好能夠從何處開始評估的初始指導方針，並且測試根據特定優先權。</span><span class="sxs-lookup"><span data-stu-id="c7fc6-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="c7fc6-116">在下一個圖中，您可以看到各種不同的應用程式和其理想的 Azure 裝載案例的細目。</span><span class="sxs-lookup"><span data-stu-id="c7fc6-116">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="c7fc6-117">[上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [下一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="c7fc6-117">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
