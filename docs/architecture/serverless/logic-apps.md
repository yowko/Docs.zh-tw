---
title: Azure Logic Apps 無伺服器應用程式
description: Azure Logic Apps 可讓您建立可跨雲端服務和內部部署系統整合應用程式和資料的自動化可調整工作流程。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 11fdf5b5f176eb0d66eee6dde7638d3eae1e1f55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171841"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](/azure/logic-apps) 提供無伺服器引擎來建立自動化工作流程，以整合雲端服務與內部部署系統之間的應用程式和資料。 您可以使用視覺化設計工具來建立工作流程。 您可以根據事件或計時器來觸發工作流程，並利用連接器來整合應用程式，並促進企業對企業 (B2B) 通訊。 Logic Apps 與 Azure Functions 緊密整合。

![Azure Logic Apps 標誌](./media/logic-apps-logo.png)

Logic Apps 可以不只是將您的雲端服務連線 (像是與雲端資源) 的函式一樣， (例如佇列和資料庫) 。 您也可以使用內部部署閘道來協調內部部署工作流程。 例如，您可以使用邏輯應用程式來觸發內部部署 SQL 預存程式，以回應工作流程中的雲端式事件或條件式邏輯。 深入瞭解如何 [使用 Azure 內部部署資料閘道連接至內部部署資料來源](/azure/analysis-services/analysis-services-gateway)。

![Logic Apps 架構](./media/logic-apps-architecture.png)

如同 Azure Functions，您會使用觸發程式來啟動邏輯應用程式工作流程。 有許多觸發程式可供您選擇。 下列的捕獲只顯示數百個可用的熱門專案。

![Logic Apps 觸發程序](./media/logic-app-triggers.png)

觸發應用程式之後，您可以使用視覺化設計工具來建立步驟、迴圈、條件和動作。 您可以在後續步驟中使用上一個步驟中內嵌的任何資料。 下列工作流程會從 CosmosDB 資料庫載入 Url。 它會尋找具有主機的主機， `t.co` 然後在 Twitter 上搜尋這些專案。 如果找到對應的推文，則會藉由呼叫函式，以相關的推文來更新檔。

![邏輯應用程式工作流程](./media/logic-app-workflow.png)

Logic Apps 儀表板會顯示執行工作流程的歷程記錄，以及每個回合是否已順利完成。 您可以流覽至任何指定的執行，並檢查每個步驟所使用的資料進行疑難排解。 Logic Apps 也提供您可以編輯的現有範本，而且非常適合複雜的企業工作流程。

若要深入瞭解，請參閱 [Azure Logic Apps](/azure/logic-apps)。

>[!div class="step-by-step"]
>[上一個](application-insights.md) 
>[下一步](event-grid.md)
