---
title: 範例商務案例和無伺服器應用程式的使用案例
description: 了解實際動手的方法與無伺服器行動後端和 ETL 管線，從映像處理存取範圍的範例。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 177fb1d7f79a0067ab185e520778b593d4b8eaf6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017179"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>無伺服器商務情節和使用案例

有許多使用案例和無伺服器應用程式的案例。 此章節包含範例將示範不同的案例。 案例包括相關文件和公用原始程式碼儲存機制的連結。 這一章中的範例可讓您將開始自行建置和實作無伺服器解決方案。

## <a name="analyze-and-archive-images"></a>分析並將映像的封存

此範例示範無伺服器的事件 (Event Grid)、 工作流程 （邏輯應用程式），以及程式碼 (Azure Functions)。 它也會顯示如何整合與另一個資源，在此案例的認知服務，影像分析。

主控台應用程式可讓您將 URL 中的連結，在網站上。 應用程式會做為事件格線訊息發佈的 URL。 以平行方式，無伺服器函式應用程式和邏輯應用程式訂閱訊息。 無伺服器函式應用程式將序列化至 blob 儲存體的映像。 它也會儲存在 Azure 資料表儲存體中的資訊。 中繼資料會儲存原始的映像 URL 和 blob 映像的名稱。 使用自訂視覺 API 分析影像並建立機器產生的原文字幕，邏輯應用程式互動。 標題會儲存在中繼資料資料表。

![分析並將映像架構的封存](./media/image-processing-example.png)

個別的單一頁面應用程式 (SPA) 呼叫來取得一份映像和中繼資料的無伺服器函式。 針對每個映像，它會呼叫從封存中提供的影像資料的另一個函式。 最終的結果會是自動的原文字幕的資源庫。

![自動化映像庫](./media/automated-image-gallery.png)

完整的存放庫和指示，來建置邏輯應用程式有以下：[事件格線黏附](https://github.com/JeremyLikness/Event-Grid-Glue)。

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>使用 Xamarin.Forms 和函式的跨平台行動裝置用戶端

了解如何在 Azure 入口網站或 Visual Studio 中，實作簡單的無伺服器 Azure Function。 建置 Android、 iOS 和 Windows 上執行的 xamarin.forms 用戶端。 應用程式是使用 JavaScript Object Notation (JSON) 做為伺服器和行動裝置的用戶端無伺服器的後端之間的通訊媒體調整。

如需詳細資訊，請參閱[使用 Xamarin.Forms 用戶端實作簡單的 Azure 函式](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>產生無伺服器的映像辨識的相片 mosaic

此範例使用 Azure Functions 和 Microsoft 認知服務 Custom Vision Service 來產生相片 mosaic 從輸入映像。 訓練模型可辨識這些映像。 上傳映像時，它會辨識映像，並使用 Bing 搜尋。 原始的映像已撰寫使用搜尋結果。

![奧蘭多市舉辦的眼睛相片與 mosaic](./media/orlando-eye-both.png)

例如，您可以訓練您奧蘭多市舉辦的地標，例如佛羅里達州眼睛的模型。 自訂辨識會辨識的奧蘭多市舉辦的眼睛，映像和函式會建立相片 mosaic Bing 的圖像搜尋結果所組成的 「 奧蘭多市舉辦的眼睛"。

如需詳細資訊，請參閱 < [Azure Functions 相片 mosaic generator](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)。

## <a name="migrate-an-existing-application-to-the-cloud"></a>移轉至雲端的現有應用程式

如先前章節中所述，通常會採用多層式架構，來裝載您的應用程式內部。 雖然移轉資源 「 現況 」 使用的虛擬機器是前往雲端風險最低的路徑，許多公司都選擇利用這個機會來重構應用程式。 幸運的是，重整不一定要是 「 孤注一擲"的工作。 事實上，就能夠移轉您的應用程式，然後分次取代雲端原生的對應中的元件。

應用程式使用 Azure Functions proxy 功能時啟用重構舊版內部部署的程式碼的無伺服器的端點的端點。

![移轉架構](./media/migration-architecture.png)

Proxy 提供單一的 API 端點更新為移動的執行無伺服器函式，將個別要求重新路由傳送。

您可以檢視進行整個移轉逐步解說的影片：[撤銷並轉移使用無伺服器 Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102)。 存取的範例程式碼：[攜帶您自己的應用程式](https://github.com/JeremyLikness/bring-own-app-connect-17)。

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>剖析 CSV 檔案，並將插入資料庫

擷取、 轉換和載入 (ETL) 是整合不同系統的一般商務函式。 傳統方法通常會涉及設定專用的 FTP 伺服器，然後部署來剖析檔案，並將它們轉譯針對商業用途使用的排程的工作。 無伺服器架構可讓工作更容易因為上傳檔案時，可以引發觸發程序。 Azure Functions 釣具工作，例如 ETL 透過其理想撰寫的程式碼片段將焦點放在特定的問題。

![如果螢幕擷取畫面顯示 csv 剖析程序。](./media/serverless-business-scenarios/csv-parse-database-import.png)

原始程式碼和實際操作實驗室，請參閱[CSV 匯入實驗室](https://github.com/JeremyLikness/azure-fn-file-process-hol)。

## <a name="shorten-links-and-track-metrics"></a>請縮短連結，並追蹤計量

縮短原本幫助簡單地說編碼 Url 之工具的連結 twitter 貼文，以容納在 140 個字元限制。 它們會愈來愈包含幾種用途，最常以追蹤按一下指出進行分析。 連結 shortener 案例是完全無伺服器應用程式可管理的連結，並報告度量資訊。

Azure Functions 用來提供單一頁面應用程式 (SPA)，可讓您貼上完整的 URL，並產生簡短的 Url。 Url 會標記為要追蹤行銷活動 （主題） 和媒體 （例如連結已張貼到社交網路） 等項目。 簡短的程式碼會儲存在 Azure 資料表儲存體，做為索引鍵，做為值的長 url。 當您按一下的簡短連結時，另一個函式會尋找完整的 URL、 傳送重新導向，並置於佇列中的事件的相關資訊。 另一個 Azure 函式會處理佇列，並將資訊放入 Azure Cosmos DB。

![連結縮網址程式架構](./media/link-shortener-architecture.png)

然後，您可以建立 Power BI 儀表板，以收集深入解析所收集的資料。 在後端，Application Insights 會提供重要計量。 遙測會包含重新導向的平均使用者花多少時間，並存取 Azure 資料表儲存體所花費。

![Power BI 範例](./media/power-bi-example.png)

這裡有指示的完整連結縮網址程式存放庫：[無伺服器 URL 縮網址程式](https://github.com/jeremylikness/serverless-url-shortener)。 您可以閱讀以下的簡化版本：[無伺服器的.NET 應用程式，以分鐘為單位的 azure 儲存體](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)。

## <a name="verify-device-connectivity-using-a-ping"></a>確認裝置的連線，使用 ping

此範例是由 Azure IoT 中樞和 Azure 函式所組成。 IoT 中樞上的新訊息會觸發 Azure 函式。 無伺服器程式碼將相同的訊息內容傳回給送出該裝置。 專案會有所有和解決方案所需的程式碼並部署設定。

如需詳細資訊，請參閱 < [Azure IoT 中樞 ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)。

## <a name="recommended-resources"></a>建議的資源

* [Azure Functions 相片 mosaic 產生器](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [Azure IoT 中樞 ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [無伺服器的.NET 應用程式，以分鐘為單位的 azure 儲存體](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [攜帶您自己的應用程式](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [CSV 匯入實驗室](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [事件格線黏附](https://github.com/JeremyLikness/Event-Grid-Glue)
* [使用 Xamarin.Forms 用戶端實作簡單的 Azure 函式](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [撤銷並轉移使用無伺服器的 Azure 函式](https://channel9.msdn.com/Events/Connect/2017/E102)
* [無伺服器 URL 縮網址程式](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[上一頁](orchestration-patterns.md)
>[下一頁](serverless-conclusion.md)