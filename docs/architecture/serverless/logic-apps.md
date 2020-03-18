---
title: Azure 邏輯應用 - 無伺服器應用
description: Azure 邏輯應用支援構建自動化可擴展工作流，跨雲服務和本地系統集成應用和資料。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577451"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="ac7fc-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="ac7fc-103">Azure Logic Apps</span></span>

<span data-ttu-id="ac7fc-104">[Azure 邏輯應用](https://docs.microsoft.com/azure/logic-apps)提供了一個無伺服器引擎來構建自動化工作流，以在雲服務和本地系統之間集成應用和資料。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="ac7fc-105">使用視覺化設計器生成工作流。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="ac7fc-106">您可以根據事件或計時器觸發工作流，並利用連接器集成應用程式，並促進企業對企業 （B2B） 通信。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="ac7fc-107">邏輯應用與 Azure 函數無縫集成。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Azure 邏輯應用徽標](./media/logic-apps-logo.png)

<span data-ttu-id="ac7fc-109">邏輯應用可以不僅僅將雲服務（如功能）與雲資源（如佇列和資料庫）連接。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="ac7fc-110">還可以使用本地閘道協調本地工作流。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="ac7fc-111">例如，可以使用邏輯應用觸發本地 SQL 預存程序，以回應工作流中的基於雲的事件或條件邏輯。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="ac7fc-112">瞭解有關使用[Azure 本地資料閘道連接到本地資料來源](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)的更多詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![邏輯應用體系結構](./media/logic-apps-architecture.png)

<span data-ttu-id="ac7fc-114">與 Azure 函數一樣，您使用觸發器啟動邏輯應用工作流。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="ac7fc-115">有許多觸發器供您選擇。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="ac7fc-116">以下捕獲僅顯示數百個可用中幾個更受歡迎的捕獲。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Logic Apps 觸發程序](./media/logic-app-triggers.png)

<span data-ttu-id="ac7fc-118">觸發應用後，可以使用視覺化設計器構建步驟、迴圈、條件和操作。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="ac7fc-119">在上一步中引入的任何資料都可用於後續步驟。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="ac7fc-120">以下工作流從 CosmosDB 資料庫載入 URL。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="ac7fc-121">它發現那些與主機`t.co`，然後搜索他們的推特。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="ac7fc-122">如果它找到相應的推文，它會通過調用函數來更新文檔與相關推文。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![邏輯應用工作流](./media/logic-app-workflow.png)

<span data-ttu-id="ac7fc-124">邏輯應用儀表板顯示運行工作流的歷史記錄，以及每次運行是否成功完成。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="ac7fc-125">您可以導航到任何給定的運行，並檢查每個步驟用於故障排除的資料。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="ac7fc-126">邏輯應用還提供您可以編輯的現有範本，非常適合複雜的企業工作流。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="ac7fc-127">要瞭解更多資訊，請參閱[Azure 邏輯應用](https://docs.microsoft.com/azure/logic-apps)。</span><span class="sxs-lookup"><span data-stu-id="ac7fc-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ac7fc-128">[上一個](application-insights.md)
>[下一個](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="ac7fc-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
