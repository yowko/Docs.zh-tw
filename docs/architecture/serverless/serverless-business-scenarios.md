---
title: 無伺服器應用程式的範例商務案例和使用案例
description: 存取從影像處理到行動支援和 ETL 管線的範例，以學習無伺服器的方法。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: df76b132579eb3a6d05ce38c94cb9fceb9281aef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171607"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>無伺服器商務情節和使用案例

無伺服器應用程式有許多使用案例和案例。 本章包含說明不同案例的範例。 這些案例包括相關檔和公用原始程式碼存放庫的連結。 本章中的範例可讓您開始使用自己的組建和執行無伺服器解決方案。

## <a name="big-data-processing"></a>巨量資料處理

![地圖/減少圖表](/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

此範例會使用無伺服器，在大型資料集上進行對應/減少作業。 它會判斷2017中每天紐約每日出租車行程的平均速度。

[大型資料處理： Azure 上的無伺服器 MapReduce](/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a>建立無伺服器應用程式：實際操作實驗室

了解如何使用函式來執行伺服器端邏輯，並建置無伺服器架構。

- 為您的企業選擇最佳的 Azure 服務
- 建立 Azure Functions
- 使用觸發程序
- 連結函數
- 長時間執行的工作流程
- 監視
- 開發、測試和部署

[建立無伺服器應用程式](/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a>客戶評論

此範例示範 Visual Studio 中 c # 類別庫的新 Azure Functions 工具。 建立網站，讓客戶提交儲存在 Azure 儲存體 blob 和 CosmosDB 中的產品評論。 新增 Azure 函式，以使用 Azure 認知服務來執行客戶評論的自動審核。 使用 Azure 儲存體佇列來分離網站與函式。

[使用認知服務的客戶評論應用程式](/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a>Docker Linux 映射支援

這個範例會示範如何建立， `Dockerfile` 以在 Linux Docker 容器上建立並執行 Azure Functions。

[Linux 上的 Azure Functions](/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a>檔案處理和驗證

此範例會剖析假想客戶的一組 CSV 檔案。 它可確保客戶「批次」所需的所有檔案都已就緒，然後驗證每個檔案的結構。 使用 Azure Functions、Logic Apps 和 Durable Functions 會顯示不同的解決方案。

[使用 Azure Functions、Logic Apps 和 Durable Functions 進行檔案處理和驗證](/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a>遊戲資料視覺效果

![遊戲遙測](/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

開發人員如何為其遊戲執行編輯器內資料視覺效果解決方案的範例。 事實上，Unreal Engine 4 外掛程式和 Unity 外掛程式是使用此範例作為其後端來開發。 服務元件與遊戲引擎無關。

[編輯器內遊戲遙測視覺效果](/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a>GraphQL

建立可公開 GraphQL API 的無伺服器函式。

[適用于 GraphQL 的無伺服器函式](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a>物聯網 (IoT) 可靠的邊緣轉送

![IoT 架構](/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

此範例會執行新的通訊協定，以啟用來自 IoT 裝置的可靠上游通訊。 它會將資料間距偵測和回填自動化。

[IoT 可靠邊緣轉送](/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a>微服務參考架構

![參考架構](/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

此參考架構會逐步引導您完成將 Rideshare by Relecloud 應用程式設計、開發和傳遞的決策程式， (虛構的公司) 。 它包含設定和部署所有架構元件的實際操作指示。

[無伺服器微服務參考架構](/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a>將主控台應用程式遷移至無伺服器

這個範例是泛型函式 (檔案 `.csx`) ，可用來將任何主控台應用程式轉換成 Azure Functions 中的 HTTP web 服務。 您只需要編輯設定檔，並指定要將哪些輸入參數當作引數傳遞給 `.exe` 。

[在 Azure Functions 上執行主控台應用程式](/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a>無伺服器的行動裝置

Azure Functions 很容易執行和維護，而且可透過 HTTP 存取。 它們是針對行動應用程式執行 API 的絕佳方式。 Microsoft 透過 Xamarin 提供適用于 iOS、Android 和 Windows 的絕佳跨平臺工具。 因此，Xamarin 和 Azure Functions 可一起運作。 本文說明如何先在 Azure 入口網站或 Visual Studio 中執行 Azure 函數，並使用在 Android、iOS 和 Windows 上執行的 Xamarin 建立跨平臺用戶端。

[使用 Xamarin 用戶端執行簡單的 Azure 函數](/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a>無伺服器訊息

此範例示範如何利用 Durable Functions 的「展開傳送」模式，在任意數目的會話/分割區上載入任意數量的訊息。 其目標為服務匯流排、事件中樞或儲存體佇列。 此範例也會新增使用其他 Azure 函式來取用這些訊息的功能，並將產生的計時資料載入至另一個事件中樞。 然後，資料會內嵌至 Azure 資料總管等分析服務。

[透過 Azure Functions 的服務匯流排、事件中樞和儲存體佇列來產生和取用訊息](/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a>建議的資源

- [Linux 上的 Azure Functions](/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [大型資料處理： Azure 上的無伺服器 MapReduce](/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [建立無伺服器應用程式](/learn/paths/create-serverless-applications/)
- [使用認知服務的客戶評論應用程式](/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [使用 Azure Functions、Logic Apps 和 Durable Functions 進行檔案處理和驗證](/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [使用 Xamarin 用戶端執行簡單的 Azure 函數](/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [編輯器內遊戲遙測視覺效果](/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [IoT 可靠邊緣轉送](/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [透過 Azure Functions 的服務匯流排、事件中樞和儲存體佇列來產生和取用訊息](/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [在 Azure Functions 上執行主控台應用程式](/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [適用于 GraphQL 的無伺服器函式](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [無伺服器微服務參考架構](/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
>[上一個](orchestration-patterns.md) 
>[下一步](serverless-conclusion.md)
