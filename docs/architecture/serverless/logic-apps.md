---
title: Azure Logic Apps-無伺服器應用程式
description: Azure Logic Apps 可讓您建立可在雲端服務和內部部署系統之間整合應用程式和資料的自動化可擴充工作流程。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577451"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="02d97-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="02d97-103">Azure Logic Apps</span></span>

<span data-ttu-id="02d97-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)提供無伺服器引擎來建立自動化工作流程, 以整合雲端服務與內部部署系統之間的應用程式和資料。</span><span class="sxs-lookup"><span data-stu-id="02d97-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="02d97-105">您可以使用視覺化設計工具來建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="02d97-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="02d97-106">您可以根據事件或計時器觸發工作流程, 並運用連接器來整合應用程式, 並加速企業對企業 (B2B) 通訊。</span><span class="sxs-lookup"><span data-stu-id="02d97-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="02d97-107">Logic Apps 與 Azure Functions 緊密整合。</span><span class="sxs-lookup"><span data-stu-id="02d97-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Azure Logic Apps 標誌](./media/logic-apps-logo.png)

<span data-ttu-id="02d97-109">Logic Apps 除了將雲端服務 (例如函式) 與雲端資源 (例如佇列和資料庫) 連接之外, 還可以做更多的工作。</span><span class="sxs-lookup"><span data-stu-id="02d97-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="02d97-110">您也可以使用內部部署閘道來協調內部部署工作流程。</span><span class="sxs-lookup"><span data-stu-id="02d97-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="02d97-111">例如, 您可以使用邏輯應用程式來觸發內部部署 SQL 預存程式, 以回應工作流程中的雲端式事件或條件式邏輯。</span><span class="sxs-lookup"><span data-stu-id="02d97-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="02d97-112">深入瞭解如何[使用 Azure 內部部署資料閘道連接到內部部署資料來源](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)。</span><span class="sxs-lookup"><span data-stu-id="02d97-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Logic Apps 架構](./media/logic-apps-architecture.png)

<span data-ttu-id="02d97-114">如同 Azure Functions, 您可以使用觸發程式來啟動邏輯應用程式工作流程。</span><span class="sxs-lookup"><span data-stu-id="02d97-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="02d97-115">有許多觸發程式可供您選擇。</span><span class="sxs-lookup"><span data-stu-id="02d97-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="02d97-116">下列的「捕捉」只顯示數百個可用的熱門功能。</span><span class="sxs-lookup"><span data-stu-id="02d97-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Logic Apps 觸發程式](./media/logic-app-triggers.png)

<span data-ttu-id="02d97-118">觸發應用程式之後, 您可以使用視覺化設計工具來建立步驟、迴圈、條件和動作。</span><span class="sxs-lookup"><span data-stu-id="02d97-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="02d97-119">在後續步驟中, 您可以使用上一個步驟中所內嵌的任何資料。</span><span class="sxs-lookup"><span data-stu-id="02d97-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="02d97-120">下列工作流程會從 CosmosDB 資料庫載入 Url。</span><span class="sxs-lookup"><span data-stu-id="02d97-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="02d97-121">它會尋找具有主機的`t.co` , 然後在 Twitter 上搜尋它們。</span><span class="sxs-lookup"><span data-stu-id="02d97-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="02d97-122">如果找到對應的推文, 它會藉由呼叫函式來更新具有相關推文的檔。</span><span class="sxs-lookup"><span data-stu-id="02d97-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![邏輯應用程式工作流程](./media/logic-app-workflow.png)

<span data-ttu-id="02d97-124">[Logic Apps] 儀表板會顯示執行工作流程的歷程記錄, 以及每個回合是否已順利完成。</span><span class="sxs-lookup"><span data-stu-id="02d97-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="02d97-125">您可以流覽至任何指定的執行, 並檢查每個步驟所使用的資料, 以進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="02d97-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="02d97-126">Logic Apps 也會提供您可以編輯的現有範本, 而且很適合用於複雜的企業工作流程。</span><span class="sxs-lookup"><span data-stu-id="02d97-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="02d97-127">若要深入瞭解, 請參閱[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)。</span><span class="sxs-lookup"><span data-stu-id="02d97-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="02d97-128">[上一頁](application-insights.md)
>[下一頁](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="02d97-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
