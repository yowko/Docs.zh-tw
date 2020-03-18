---
title: 無伺服器應用的業務方案和用例示例
description: 通過訪問從映射處理到移動後端和 ETL 管道的樣本，通過動手方法學習無伺服器。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f0d7a4c5cd736d1168ec76c1c0ea19627505f15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76787886"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>無伺服器商務情節和使用案例

對於無伺服器應用程式，有許多用例和方案。 本章包括說明不同方案的示例。 這些方案包括指向相關文檔和公共原始程式碼存儲庫的連結。 本章中的示例使您能夠開始構建和實現無伺服器解決方案。

## <a name="analyze-and-archive-images"></a>分析和存檔圖像

此示例演示無伺服器事件（事件網格）、工作流（邏輯應用）和代碼（Azure 函數）。 它還演示如何與其他資源集成，在這種情況下，用於圖像分析的認知服務。

主控台應用程式允許您傳遞指向 Web 上 URL 的連結。 應用將 URL 發佈為事件網格消息。 並行，無伺服器函數應用和邏輯應用訂閱消息。 無伺服器函數應用將映射序列化到 blob 存儲。 它還在 Azure 表存儲中存儲資訊。 中繼資料存儲原始圖像 URL 和 blob 圖像的名稱。 邏輯應用與自訂視覺 API 交互以分析圖像並創建電腦生成的字幕。 標題存儲在中繼資料表中。

![分析和存檔圖像體系結構](./media/image-processing-example.png)

單獨的單頁應用程式 （SPA） 調用無伺服器函數來獲取圖像和中繼資料的清單。 對於每個映射，它調用另一個從存檔中傳遞圖像資料的函數。 最終結果是具有自動字幕的庫。

![自動圖像庫](./media/automated-image-gallery.png)

完整的存儲庫和說明，以建立邏輯應用程式在這裡可用：[事件網格膠水](https://github.com/JeremyLikness/Event-Grid-Glue)。

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>使用 Xamarin 的跨平臺移動用戶端。

瞭解如何在 Azure Web 門戶或視覺化工作室中實現簡單的無伺服器 Azure 函數。 使用在 Android、iOS 和 Windows 上運行的 Xamarin.表單構建用戶端。 然後，對應用程式進行優化，使用 JavaScript 物件標記法 （JSON） 作為伺服器和具有無伺服器後端的移動用戶端之間的通信介質。

有關詳細資訊，請參閱使用[Xamarin.Forms 用戶端實現簡單的 Azure 函數](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)。

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>生成具有無伺服器圖像識別的照片鑲嵌

該示例使用 Azure 函數和 Microsoft 認知服務自訂視覺服務從輸入圖像生成照片鑲嵌。 模型經過培訓，可以識別圖像。 上傳圖像時，它會識別圖像，並使用必應搜索。 使用搜尋結果重新組合原始圖像。

![奧蘭多眼照片和馬賽克](./media/orlando-eye-both.png)

例如，您可以使用奧蘭多地標（如奧蘭多眼）訓練模型。 自訂視覺將識別奧蘭多眼的圖像，該功能將創建由必應圖像搜尋結果組成的"奧蘭多眼"照片馬賽克。

有關詳細資訊，請參閱[Azure 函數照片鑲嵌產生器](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)。

## <a name="migrate-an-existing-application-to-the-cloud"></a>將現有應用程式遷移到雲

如前幾章所述，通常採用 N-Tier 體系結構在本地託管應用程式。 儘管使用虛擬機器遷移資源是雲風險最小的路徑，但許多公司選擇利用這個機會重構其應用程式。 幸運的是，重構不一定是"全無"的努力。 事實上，可以遷移應用，然後零敲碎打地將元件替換為雲本機組件。

應用程式使用 Azure 函數的代理功能來啟用重構終結點，從舊本地代碼到無伺服器終結點。

![移轉架構](./media/migration-architecture.png)

代理提供單個 API 終結點，該終結點在移動到無伺服器函數時可重新路由各個請求。

您可以查看貫穿整個遷移的視頻：[使用無伺服器 Azure 函數提升和移動](https://channel9.msdn.com/Events/Connect/2017/E102)。 訪問示例代碼：[自取自己的應用](https://github.com/JeremyLikness/bring-own-app-connect-17)。

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>分析 CSV 檔並插入資料庫

擷取、轉換和下載 （ETL） 是集成不同系統的常見業務功能。 傳統方法通常涉及設置專用 FTP 伺服器，然後部署計畫作業來分析檔並將其轉換為業務用途。 無伺服器體系結構使作業更容易，因為上載檔時可能會觸發觸發器。 Azure 函數通過專注于特定問題的小型程式碼片段的理想組合來處理 ETL 等任務。

![顯示 csv 解析過程的螢幕截圖。](./media/serverless-business-scenarios/csv-parse-database-import.png)

有關原始程式碼和動手實驗，請參閱[CSV 導入實驗室](https://github.com/JeremyLikness/azure-fn-file-process-hol)。

## <a name="shorten-links-and-track-metrics"></a>縮短連結並跟蹤指標

連結縮短工具最初説明編碼URL在短推特帖子，以適應140個字元的限制。 它們已發展到包括多種用途，最常見的是跟蹤分析的點擊率。 連結縮短器方案是一個完全無伺服器的應用程式，用於管理連結和報告指標。

Azure 函數用於為單頁應用程式 （SPA） 提供服務，該應用程式允許您粘貼長 URL 並生成短 URL。 URL 被標記以跟蹤市場活動（主題）和媒介（如連結發佈到的社交網路）等內容。 短代碼作為鍵存儲在 Azure 表存儲中，長 URL 作為值。 按一下短連結時，另一個函數會查找長 URL，發送重定向，並將有關事件的資訊放在佇列中。 另一個 Azure 函數處理佇列並將資訊放入 Azure Cosmos DB 中。

![連結縮短器體系結構](./media/link-shortener-architecture.png)

然後，您可以創建 Power BI 儀表板來收集有關收集的資料的見解。 在後端，應用程式見解提供了重要的指標。 遙測包括普通使用者重定向所需的時間以及訪問 Azure 表存儲所需的時間。

![電源 BI 示例](./media/power-bi-example.png)

完整的連結縮短器存儲庫與說明可在這裡：[無伺服器 URL 縮短器](https://github.com/jeremylikness/serverless-url-shortener). 您可以在此處閱讀有關簡化版本[：Azure 存儲，用於無伺服器 .NET 應用，在幾分鐘內](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)即可。

## <a name="verify-device-connectivity-using-a-ping"></a>使用 ping 驗證設備連接

該示例由 Azure IoT 中心和 Azure 函陣列成。 IoT 中心上的新消息將觸發 Azure 函數。 無伺服器代碼將相同的消息內容發送回發送它的設備。 專案具有解決方案所需的所有代碼和部署配置。

有關詳細資訊，請參閱[Azure IoT 中心 ping](https://github.com/Azure-Samples/iot-hub-node-ping)。

## <a name="recommended-resources"></a>建議的資源

- [Azure 功能照片鑲嵌產生器](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)
- [Azure IoT 中樞 ping](https://github.com/Azure-Samples/iot-hub-node-ping)
- [用於無伺服器 .NET 應用的 Azure 存儲，在幾分鐘內](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
- [自帶應用](https://github.com/JeremyLikness/bring-own-app-connect-17)
- [CSV 導入實驗室](https://github.com/JeremyLikness/azure-fn-file-process-hol)
- [事件網格粘合](https://github.com/JeremyLikness/Event-Grid-Glue)
- [使用 Xamarin 實現簡單的 Azure 函數。](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [使用無伺服器 Azure 功能提升和移動](https://channel9.msdn.com/Events/Connect/2017/E102)
- [無伺服器 URL 縮短器](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[上一個](orchestration-patterns.md)
>[下一個](serverless-conclusion.md)
