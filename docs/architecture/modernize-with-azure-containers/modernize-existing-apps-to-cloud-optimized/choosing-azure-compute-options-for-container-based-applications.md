---
title: 選擇容器應用程式的 Azure 計算平台
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |選擇適用于容器型應用程式的 Azure 計算平臺
ms.date: 05/04/2018
ms.openlocfilehash: 2262d2cf4e69e19e8b78c07c239602dd5dccc3cd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318671"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="fbb57-103">選擇容器應用程式的 Azure 計算平台</span><span class="sxs-lookup"><span data-stu-id="fbb57-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="fbb57-104">如您在閱讀前幾節所注意，Azure 是一個開放雲端，可提供多個選擇。</span><span class="sxs-lookup"><span data-stu-id="fbb57-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="fbb57-105">您可以使用最適合您的需求，不過，它也會呈現您應該針對容器化應用程式使用之產品/技術的相關問題。</span><span class="sxs-lookup"><span data-stu-id="fbb57-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="fbb57-106">根據*預設*的建議，下列是本指南中建議的主要準則：</span><span class="sxs-lookup"><span data-stu-id="fbb57-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="fbb57-107">**單一整合型應用程式：** 選擇 Azure App Service</span><span class="sxs-lookup"><span data-stu-id="fbb57-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="fbb57-108">多**層式應用程式：** 如果您有單一或幾個後端服務，請選擇協調器，例如 Azure Kubernetes Service （AKS）或 App Service</span><span class="sxs-lookup"><span data-stu-id="fbb57-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS) or App Service if you have a single or a few back-end services</span></span>
- <span data-ttu-id="fbb57-109">**微服務：** 選擇適用于容器的 AKS 或 Azure Web Apps</span><span class="sxs-lookup"><span data-stu-id="fbb57-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="fbb57-110">**無伺服器函數 & 事件處理常式：** 選擇 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="fbb57-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="fbb57-111">**大規模批次：** 選擇 Azure Batch</span><span class="sxs-lookup"><span data-stu-id="fbb57-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="fbb57-112">不過，這項建議應以一種 salt 來進行，因為產品的選擇將取決於您的特定應用程式的需求和特性。</span><span class="sxs-lookup"><span data-stu-id="fbb57-112">However, this recommendation should be taken with a pinch of salt, as the product's selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="fbb57-113">並非所有的應用程式都相同，即使一開始可能看起來像這樣的類型也一樣。</span><span class="sxs-lookup"><span data-stu-id="fbb57-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="fbb57-114">在更深入分析應用程式的需求之後，所選取的產品可能會不同。</span><span class="sxs-lookup"><span data-stu-id="fbb57-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="fbb57-115">但是做為起點，您可以根據特定優先順序開始評估和測試的初始指引。</span><span class="sxs-lookup"><span data-stu-id="fbb57-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="fbb57-116">在 [圖 1] 中，您可以看到不同類型的應用程式及其理想 Azure 裝載案例的細目。</span><span class="sxs-lookup"><span data-stu-id="fbb57-116">In Figure 1, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![圖 1](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="fbb57-118">[上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [下一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="fbb57-118">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
