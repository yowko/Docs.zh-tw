---
title: Azure Logic Apps-無伺服器應用程式
description: Azure Logic Apps 可讓您啟用建置自動化可調整的工作流程，整合應用程式，並跨雲端服務和資料在內部部署系統。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 14670a8459db3b80b8fbe3139c2675321cf9592c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147941"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="0ecc8-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="0ecc8-103">Azure Logic Apps</span></span>

<span data-ttu-id="0ecc8-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)提供無伺服器的引擎，來建置自動化工作流程來整合應用程式和雲端服務之間的資料，並在內部部署系統。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="0ecc8-105">您建置使用視覺化設計工具中的工作流程。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="0ecc8-106">您可以根據事件或計時器和整合的應用程式利用連接器工作流程觸發程序，並促進企業對企業 (B2B) 通訊。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="0ecc8-107">Azure Functions 與 logic Apps 則無縫的整合。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Azure Logic Apps 標誌](./media/logic-apps-logo.png)

<span data-ttu-id="0ecc8-109">Logic Apps 如何運用雲端資源 （例如佇列和資料庫） 的多個只連接您的雲端服務 （例如函式）。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="0ecc8-110">您也可以協調內部部署閘道的內部部署工作流程。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="0ecc8-111">例如，您可以使用邏輯應用程式來觸發以雲端為基礎的事件回應的內部部署 SQL 預存程序或工作流程中的條件式邏輯。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="0ecc8-112">深入了解[連接到 Azure 內部部署資料閘道的內部部署資料來源](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![邏輯應用程式架構](./media/logic-apps-architecture.png)

<span data-ttu-id="0ecc8-114">如同 Azure Functions，您開始以觸發程序的邏輯應用程式工作流程。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="0ecc8-115">有許多的觸發程序，您可從中選擇。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="0ecc8-116">下列擷取畫面顯示幾個較受歡迎的共數百個可用。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![邏輯應用程式觸發程序](./media/logic-app-triggers.png)

<span data-ttu-id="0ecc8-118">一旦觸發應用程式時，您可以使用視覺化設計工具來建置步驟、 迴圈、 條件和動作。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="0ecc8-119">上一個步驟中內嵌任何資料可供您在後續步驟中使用。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="0ecc8-120">下列工作流程從 CosmosDB 資料庫載入 Url。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="0ecc8-121">找到的項目與主控件的`t.co`則搜尋它們在 Twitter 上。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="0ecc8-122">如果它找到對應的推文時，它會更新文件的相關推文與所呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![邏輯應用程式工作流程](./media/logic-app-workflow.png)

<span data-ttu-id="0ecc8-124">邏輯應用程式儀表板會顯示執行您的工作流程和是否每次執行已完成成功與否的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="0ecc8-125">您可以瀏覽至任何特定的執行，並檢查每個步驟用於疑難排解的資料。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="0ecc8-126">Logic Apps 也會提供現有的範本，您可以編輯，且不適合用於複雜的企業工作流程。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="0ecc8-127">若要進一步了解，請參閱[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)。</span><span class="sxs-lookup"><span data-stu-id="0ecc8-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0ecc8-128">[上一頁](application-insights.md)
>[下一頁](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="0ecc8-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>