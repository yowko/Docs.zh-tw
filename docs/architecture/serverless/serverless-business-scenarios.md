---
title: 無伺服器應用程式的範例商務案例和使用案例
description: 存取從影像處理到行動後端和 ETL 管線範圍的範例，以瞭解無伺服器的實際操作方法。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7024a33f8a7fccd6afa51c126454afedd87cceee
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834292"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>無伺服器商務情節和使用案例

無伺服器應用程式有許多使用案例和情節。 本章包含說明不同案例的範例。 這些案例包括相關檔和公用原始程式碼存放庫的連結。 本章中的範例可讓您開始建立自己的建築物和執行無伺服器解決方案。

## <a name="analyze-and-archive-images"></a>分析和封存映射

這個範例示範無伺服器事件（事件方格）、工作流程（邏輯應用程式）和程式碼（Azure Functions）。 它也會示範如何與另一個資源整合，在此案例中認知服務用於影像分析。

主控台應用程式可讓您將連結傳遞至 web 上的 URL。 應用程式會將 URL 發佈為事件方格訊息。 以平行方式，無伺服器函式應用程式和邏輯應用程式會訂閱該訊息。 無伺服器函數應用程式會將映射序列化至 blob 儲存體。 它也會將資訊儲存在 Azure 表格儲存體。 中繼資料會儲存原始的影像 URL 和 blob 映射的名稱。 邏輯應用程式會與自訂視覺 API 互動，以分析影像並建立電腦產生的標題。 標題會儲存在中繼資料資料表中。

![分析和封存映射架構](./media/image-processing-example.png)

個別的單一頁面應用程式（SPA）會呼叫無伺服器函式，以取得映射和中繼資料的清單。 針對每個映射，它會呼叫另一個函式，以從封存傳遞影像資料。 最終結果是具有自動字幕的資源庫。

![自動映射庫](./media/automated-image-gallery.png)

您可以在這裡找到完整的存放庫和建立邏輯應用程式的指示：[事件格線粘附](https://github.com/JeremyLikness/Event-Grid-Glue)。

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>使用 Xamarin 的跨平臺行動用戶端。表單和函式

請參閱如何在 Azure 入口網站中或 Visual Studio 中執行簡單的無伺服器 Azure 函式。 使用在 Android、iOS 和 Windows 上執行的 Xamarin 來建立用戶端。 然後，應用程式會經過精簡，以使用 JavaScript 物件標記法（JSON）做為伺服器和行動用戶端之間的通訊媒介（具有無伺服器後端）。

如需詳細資訊，請參閱[使用 Xamarin. Forms client 來執行簡單的 Azure 函數](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)。

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>使用無伺服器影像辨識產生相片馬賽克

此範例會使用 Azure Functions 和 Microsoft 認知服務自訂視覺服務，從輸入影像產生相片馬賽克。 模型已定型，可辨識影像。 上傳影像時，它會辨識影像，並使用 Bing 進行搜尋。 使用搜尋結果重新組合原始影像。

![奧蘭多眼相片和馬賽克](./media/orlando-eye-both.png)

例如，您可以使用奧蘭多地標（例如佛羅里達眼）來定型您的模型。 自訂視覺會辨識奧蘭多眼的影像，而此函式會建立相片馬賽克，其中包含「奧蘭多眼」的 Bing 影像搜尋結果。

如需詳細資訊，請參閱[Azure Functions 相片馬賽克](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)產生器。

## <a name="migrate-an-existing-application-to-the-cloud"></a>將現有的應用程式遷移至雲端

如先前章節所討論，通常會採用多層式架構來裝載您在內部部署的應用程式。 雖然使用虛擬機器以「原樣」遷移資源是雲端最具風險的途徑，但許多公司選擇使用此機會來重構其應用程式。 幸好，重構不一定要有「全有或無」的成果。 事實上，您可以遷移您的應用程式，然後將元件分次取代為雲端原生對應專案。

應用程式會使用 Azure Functions 的 proxy 功能，啟用將端點從舊版內部部署程式碼重構至無伺服器端點。

![遷移架構](./media/migration-architecture.png)

Proxy 提供單一 API 端點，其會在將個別要求移至無伺服器函式時進行更新，以重新路由傳送它們。

您可以觀看影片來逐步完成整個遷移：[使用無伺服器 Azure](https://channel9.msdn.com/Events/Connect/2017/E102)函式的隨即轉移。 存取範例程式碼：[攜帶您自己的應用程式](https://github.com/JeremyLikness/bring-own-app-connect-17)。

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>剖析 CSV 檔案並插入資料庫

「解壓縮」、「轉換」和「載入」（ETL）是整合不同系統的常見商務功能。 傳統的方法通常會牽涉到設定專用的 FTP 伺服器，然後部署排程的工作來剖析檔案並加以轉譯，以供企業使用。 無伺服器架構可讓工作變得更容易，因為上傳檔案時會引發觸發程式。 Azure Functions 透過其適用于特定問題的小型程式碼片段，來 esposito 著手處理 ETL 之類的工作。

![顯示 csv 剖析進程的螢幕擷取畫面。](./media/serverless-business-scenarios/csv-parse-database-import.png)

如需原始碼和實際操作實驗室，請參閱[CSV 匯入實驗室](https://github.com/JeremyLikness/azure-fn-file-process-hol)。

## <a name="shorten-links-and-track-metrics"></a>縮短連結和追蹤計量

連結縮短工具原本有助於在短 twitter 文章中編碼 Url，以配合140字元的限制。 它們已成長成包含數個用途，最常用來追蹤解說以進行分析。 連結 shortener 案例是一個完全無伺服器的應用程式，可管理連結和報告計量。

Azure Functions 可用來提供單一頁面應用程式（SPA），讓您可以貼上長 URL 並產生簡短的 url。 Url 會加上標籤，以追蹤行銷活動（主題）和媒體（例如，連結張貼的社交網路）等專案。 簡短的程式碼會以金鑰的形式儲存在 Azure 表格儲存體中，並以完整的 URL 做為值。 當您按一下 [簡短] 連結時，另一個函式會查閱完整的 URL、傳送重新導向，並將事件的相關資訊放在佇列上。 另一個 Azure 函式會處理佇列，並將資訊放入 Azure Cosmos DB。

![連結 shortener 架構](./media/link-shortener-architecture.png)

接著，您可以建立 Power BI 儀表板，以收集所收集資料的深入解析。 在後端，Application Insights 提供重要的計量。 遙測包含平均使用者重新導向所需的時間，以及存取 Azure 表格儲存體所需的時間。

![Power BI 範例](./media/power-bi-example.png)

您可以在這裡取得完整連結 shortener 存放庫與指示：[無伺服器 URL shortener](https://github.com/jeremylikness/serverless-url-shortener)。 您可以在這裡閱讀簡化版本的相關資訊：[幾分鐘內就能 Azure 儲存體無伺服器 .net 應用程式](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)。

## <a name="verify-device-connectivity-using-a-ping"></a>使用 ping 來驗證裝置連線能力

此範例是由 Azure IoT 中樞和 Azure 函數所組成。 IoT 中樞上的新訊息會觸發 Azure Function。 無伺服器程式碼會將相同的訊息內容傳回給傳送它的裝置。 專案具有方案所需的所有程式碼和部署設定。

如需詳細資訊，請參閱[Azure IoT 中樞 ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)。

## <a name="recommended-resources"></a>建議的資源

* [Azure Functions 相片馬賽克產生器](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [Azure IoT 中樞 ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [幾分鐘內無伺服器 .NET 應用程式的 Azure 儲存體](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
* [攜帶您自己的應用程式](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [CSV 匯入實驗室](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [事件方格粘附](https://github.com/JeremyLikness/Event-Grid-Glue)
* [使用 Xamarin. Forms 用戶端來執行簡單的 Azure 函數](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [無伺服器 Azure 函式的隨即轉移](https://channel9.msdn.com/Events/Connect/2017/E102)
* [無伺服器 URL shortener](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[上一頁](orchestration-patterns.md)
>[下一頁](serverless-conclusion.md)
