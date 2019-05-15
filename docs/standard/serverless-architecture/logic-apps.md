---
title: Azure Logic Apps-無伺服器應用程式
description: Azure Logic Apps 可讓您啟用建置自動化可調整的工作流程，整合應用程式，並跨雲端服務和資料在內部部署系統。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638814"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)提供無伺服器的引擎，來建置自動化工作流程來整合應用程式和雲端服務之間的資料，並在內部部署系統。 您建置使用視覺化設計工具中的工作流程。 您可以根據事件或計時器和整合的應用程式利用連接器工作流程觸發程序，並促進企業對企業 (B2B) 通訊。 Azure Functions 與 logic Apps 則無縫的整合。

![Azure Logic Apps 標誌](./media/logic-apps-logo.png)

Logic Apps 如何運用雲端資源 （例如佇列和資料庫） 的多個只連接您的雲端服務 （例如函式）。 您也可以協調內部部署閘道的內部部署工作流程。 例如，您可以使用邏輯應用程式來觸發以雲端為基礎的事件回應的內部部署 SQL 預存程序或工作流程中的條件式邏輯。 深入了解[連接到 Azure 內部部署資料閘道的內部部署資料來源](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)。

![邏輯應用程式架構](./media/logic-apps-architecture.png)

如同 Azure Functions，您開始以觸發程序的邏輯應用程式工作流程。 有許多的觸發程序，您可從中選擇。 下列擷取畫面顯示幾個較受歡迎的共數百個可用。

![邏輯應用程式觸發程序](./media/logic-app-triggers.png)

一旦觸發應用程式時，您可以使用視覺化設計工具來建置步驟、 迴圈、 條件和動作。 上一個步驟中內嵌任何資料可供您在後續步驟中使用。 下列工作流程從 CosmosDB 資料庫載入 Url。 找到的項目與主控件的`t.co`則搜尋它們在 Twitter 上。 如果它找到對應的推文時，它會更新文件的相關推文與所呼叫函式。

![邏輯應用程式工作流程](./media/logic-app-workflow.png)

邏輯應用程式儀表板會顯示執行您的工作流程和是否每次執行已完成成功與否的歷程記錄。 您可以瀏覽至任何特定的執行，並檢查每個步驟用於疑難排解的資料。 Logic Apps 也會提供現有的範本，您可以編輯，且不適合用於複雜的企業工作流程。

若要進一步了解，請參閱[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)。

>[!div class="step-by-step"]
>[上一頁](application-insights.md)
>[下一頁](event-grid.md)
