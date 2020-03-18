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
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure 邏輯應用](https://docs.microsoft.com/azure/logic-apps)提供了一個無伺服器引擎來構建自動化工作流，以在雲服務和本地系統之間集成應用和資料。 使用視覺化設計器生成工作流。 您可以根據事件或計時器觸發工作流，並利用連接器集成應用程式，並促進企業對企業 （B2B） 通信。 邏輯應用與 Azure 函數無縫集成。

![Azure 邏輯應用徽標](./media/logic-apps-logo.png)

邏輯應用可以不僅僅將雲服務（如功能）與雲資源（如佇列和資料庫）連接。 還可以使用本地閘道協調本地工作流。 例如，可以使用邏輯應用觸發本地 SQL 預存程序，以回應工作流中的基於雲的事件或條件邏輯。 瞭解有關使用[Azure 本地資料閘道連接到本地資料來源](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)的更多詳細資訊。

![邏輯應用體系結構](./media/logic-apps-architecture.png)

與 Azure 函數一樣，您使用觸發器啟動邏輯應用工作流。 有許多觸發器供您選擇。 以下捕獲僅顯示數百個可用中幾個更受歡迎的捕獲。

![Logic Apps 觸發程序](./media/logic-app-triggers.png)

觸發應用後，可以使用視覺化設計器構建步驟、迴圈、條件和操作。 在上一步中引入的任何資料都可用於後續步驟。 以下工作流從 CosmosDB 資料庫載入 URL。 它發現那些與主機`t.co`，然後搜索他們的推特。 如果它找到相應的推文，它會通過調用函數來更新文檔與相關推文。

![邏輯應用工作流](./media/logic-app-workflow.png)

邏輯應用儀表板顯示運行工作流的歷史記錄，以及每次運行是否成功完成。 您可以導航到任何給定的運行，並檢查每個步驟用於故障排除的資料。 邏輯應用還提供您可以編輯的現有範本，非常適合複雜的企業工作流。

要瞭解更多資訊，請參閱[Azure 邏輯應用](https://docs.microsoft.com/azure/logic-apps)。

>[!div class="step-by-step"]
>[上一個](application-insights.md)
>[下一個](event-grid.md)
