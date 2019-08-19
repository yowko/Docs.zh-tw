---
title: Azure Functions-無伺服器應用程式
description: Azure 函式提供跨多種語言 (C#、JavaScript、JAVA) 和平臺的無伺服器功能, 以提供事件驅動的立即調整程式碼。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577601"
---
# <a name="azure-functions"></a>Azure Functions

Azure 函式提供無伺服器計算體驗。 函式是由*觸發*程式 (例如存取 HTTP 端點或計時器) 所叫用, 並執行程式碼區塊或商務邏輯。 函式也支援特定的系結, 這些系結會連接到儲存體和佇列之類的資源。

![Azure 函數標誌](./media/azure-functions-logo.png)

Azure Functions framework 有兩個版本。 舊版支援完整的 .NET Framework, 而新的執行時間支援跨平臺 .NET Core 應用程式。 除了 JavaScript、 C# F#和 JAVA 以外, 還支援其他語言。 在入口網站中建立的函數會提供豐富的腳本語法。 建立為獨立專案的函式可以使用完整的平臺支援和功能進行部署。

如需詳細資訊, 請參閱[Azure Functions 檔](https://docs.microsoft.com/azure/azure-functions)。

## <a name="functions-v1-vs-v2"></a>函數 v1 與 v2 的比較

Azure Functions 執行時間有兩個版本:1.x 和2.x。 1\.x 版正式推出 (GA)。 它支援從入口網站或 Windows 電腦進行 .NET 開發, 並使用 .NET Framework。 1.x 支援C#PYTHON、PHP、TypeScript、 F#Batch、Bash 和 PowerShell 的實驗性支援、JavaScript 和。

2\.x[版現在也已正式推出](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/)。 它會利用 .NET Core, 並在 Windows、macOS 和 Linux 電腦上支援跨平臺開發。 2.x 新增了 JAVA 的第一級支援, 但尚未直接支援任何實驗語言。 2\.x 版使用新的系結擴充性模型, 可啟用平臺的協力廠商延伸、系結的獨立版本控制, 以及更簡化的執行環境。

> **1.x 具有系結重新[導向支援](https://github.com/Azure/azure-functions-host/issues/992)的已知問題。** 問題僅適用于 .NET 開發。 具有相依性的專案, 與執行時間中包含的程式庫不同版本會受到影響。 函數小組致力於對問題做出具體的進度。 小組會先解決2.x 中的系結重新導向, 再進入正式運作狀態。 如有建議的修正和因應措施, 請參閱此官方小組聲明:[Azure Functions 中的元件解析](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions)。

如需詳細資訊, 請參閱[比較1.x 和](https://docs.microsoft.com/azure/azure-functions/functions-versions)2.x。

## <a name="programming-language-support"></a>程式設計語言支援

公開上市 (GA)、預覽或實驗性都支援下列語言。

|語言      |1.x         |2.x      |
|--------------|------------|---------|
|**C#**        |GA          |預覽  |
|**JavaScript**|GA          |預覽  |
|**F#**        |GA          |         |
|**Java**      |            |預覽  |
|**Python**    |實驗|         |
|**PHP**       |實驗|         |
|**TypeScript**|實驗|         |
|**Batch**     |實驗|         |
|**狂歡**      |實驗|         |
|**PowerShell**|實驗|         |

如需詳細資訊, 請參閱[支援的語言](https://docs.microsoft.com/azure/azure-functions/supported-languages)。

## <a name="app-service-plans"></a>App service 方案

函數是由*app service 方案*支援。 此方案會定義函數應用程式所使用的資源。 您可以將方案指派給區域、判斷將使用的虛擬機器大小和數量, 以及挑選定價層。 針對真正的無伺服器方法, 函數應用程式可能會使用取用方案。 取用方案會根據負載自動調整後端。

如需詳細資訊, 請參閱[App service 方案](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)。

## <a name="create-your-first-function"></a>建立您的第一個函式

有三種常見的方式可供您建立函數應用程式。

* 在入口網站中編寫函式的腳本。
* 使用 Azure 命令列介面 (CLI) 來建立必要的資源。
* 使用您最愛的 IDE 在本機建立函式, 並將其發佈至 Azure。

如需在入口網站中建立腳本函式的詳細資訊, 請參閱在[Azure 入口網站中建立您的第一個函數](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)。

若要從 Azure CLI 建立, 請參閱[使用 Azure CLI 建立您的第一個](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)函式。

若要從 Visual Studio 建立函數, 請參閱[使用 Visual Studio 建立您的第一個](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)函式。

## <a name="understand-triggers-and-bindings"></a>瞭解觸發程式和系結

函式是由*觸發*程式叫用, 而且可以只有一個。 除了叫用函式, 某些觸發程式也會做為系結。 除了觸發程式之外, 您也可以定義多個系結。 系結會提供宣告式方式, 將資料連線到您的程式碼。 它們可以傳入 (輸入) 或接收資料 (輸出)。 觸發程式和系結可讓函式便於使用。 系結會移除手動建立資料庫或檔案系統連接的額外負荷。 系結所需的所有資訊都包含在腳本的特殊函式*json*檔案中, 或以程式碼中的屬性宣告。

一些常見的觸發套裝程式括:

* Blob 儲存體: 在儲存體中上傳或變更檔案或資料夾時, 叫用您的函式。
* HTTP: 叫用您的函式, 例如 REST API。
* Queue: 當專案存在於佇列中時, 叫用您的函式。
* 計時器: 定期叫用您的函式。

系結的範例包括:

* CosmosDB: 輕鬆地連接到資料庫以載入或儲存檔案。
* 表格儲存體: 使用函數應用程式中的索引鍵/值儲存體。
* 佇列儲存體: 輕鬆地從佇列取出專案, 或將新專案放在佇列上。

下列範例*函數. json*檔案會定義觸發程式和系結:

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

在此範例中, 函式是由`images`容器中的 blob 儲存體變更所觸發。 檔案的資訊會傳入, 因此觸發程式也會做為系結。 有另一個系結可將資訊放在`images`名為的佇列上。

以下是函數C#的腳本:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

此範例是一個簡單的函式, 會採用已修改或上傳至 blob 儲存體的檔案名稱, 並將它放在佇列上以供稍後處理。

如需觸發程式和系結的完整清單, 請參閱[Azure Functions 觸發程式和](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)系結概念。

## <a name="proxies"></a>Proxy

Proxy 會為您的應用程式提供重新導向功能。 Proxy 會公開端點, 並將該端點對應至另一個資源。 使用 proxy, 您可以:

* 將連入要求重新路由至另一個端點。
* 在傳入要求傳遞之前進行修改。
* 修改或提供回應。

Proxy 用於下列案例:

* 簡化、縮短或變更 URL。
* 提供一致的 API 前置詞給多個後端服務。
* 模擬正在開發之端點的回應。
* 提供對知名端點的靜態回應。
* 移動或遷移後端時, 讓 API 端點保持一致。

Proxy 會儲存為 JSON 定義。 請看以下範例：

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

`Domain Redirect` Proxy 會使用較短的路由, 並將其對應至較長的函式資源。 轉換看起來像這樣:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

Proxy 會接受傳送至根 URL (`https://--shorturl--/`) 的任何專案, 並將其重新導向至檔網站。 `Root`

如需使用 proxy 的範例, 請觀看[Azure:透過無伺服器 Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102)將您的應用程式帶入雲端。 在本機 SQL Server 上執行的 ASP.NET Core 應用程式會即時移轉至 Azure 雲端。 Proxy 是用來協助重構傳統的 Web API 專案以使用函式。

如需 proxy 的詳細資訊, 請參閱使用[Azure Functions Proxy](https://docs.microsoft.com/azure/azure-functions/functions-proxies)。

>[!div class="step-by-step"]
>[上一頁](azure-serverless-platform.md)
>[下一頁](application-insights.md)
