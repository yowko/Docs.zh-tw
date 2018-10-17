---
title: Azure Functions-無伺服器應用程式
description: Azure functions 提供無伺服器的功能 （C#、 JavaScript、 Java） 的多種語言，並立即提供事件驅動的平台擴充程式碼。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: f08ba20b485197acd3bb5cdfe5699cd6be991d7c
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "49369740"
---
# <a name="azure-functions"></a>Azure Functions

Azure functions 提供無伺服器計算體驗。 函式會叫用*觸發程序*（例如存取 HTTP 端點或計時器），並執行的程式碼或商務邏輯區塊。 函式也支援特製化*繫結*，連接到儲存體和佇列等資源。

![Azure functions 標誌](./media/azure-functions-logo.png)

有兩個版本的 Azure Functions 架構。 舊版的版本可支援完整的.NET Framework，新的執行階段支援跨平台.NET Core 應用程式。 除了 C# JavaScript、 F # 和 Java 等其他語言支援。 在入口網站中建立的函式提供豐富的指令碼語法。 做為獨立專案所建立的函式可以部署與完整的平台支援和功能。

如需詳細資訊，請參閱 < [Azure Functions 文件](https://docs.microsoft.com/azure/azure-functions)。

## <a name="functions-v1-vs-v2"></a>函式 v1 與 v2

有兩個 Azure Functions 執行階段版本： 1.x 和 2.x。 版本 1.x 已正式推出 (GA)。 它支援從入口網站或 Windows 電腦的.NET 開發，並使用.NET Framework。 1.x 支援 C#、 JavaScript 和 F # 中，使用 Python、 PHP、 TypeScript、 Batch、 Bash、 和 PowerShell 的實驗性支援。

版本 2.x 處於預覽狀態。 它會利用.NET Core，而且支援在 Windows、 macOS 和 Linux 機器上跨平台開發。 2.x 新增適用於 Java 的頂級支援，但尚不直接支援的任何實驗性語言。 版本 2.x 使用新的繫結擴充性模型，可讓協力廠商擴充功能的平台獨立的版本設定的繫結，並更精簡的執行環境。

> **與 1.x 中沒有已知的問題[繫結重新導向支援](https://github.com/Azure/azure-functions-host/issues/992)。** 問題在於專用的.NET 開發。 受影響的相依性會包含在執行階段程式庫中的不同版本的程式庫的專案。 Functions 小組已致力於問題的具體進度。 小組會在它進入正式運作之前解決在 2.x 中的繫結重新導向。 建議的修正和因應措施的官方團隊陳述式，請參閱這裡：[在 Azure Functions 中的組件解析](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions)。

如需詳細資訊，請參閱 <<c0> [ 比較 1.x 和 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)。

## <a name="programming-language-support"></a>程式設計語言支援

支援下列語言版本可能是一般情況下運作 (GA)，預覽，或實驗性。

|語言      |1.x         |2.x      |
|--------------|------------|---------|
|**C#**        |正式運作          |預覽  |
|**JavaScript**|正式運作          |預覽  |
|**F#**        |正式運作          |         |
|**Java**      |            |預覽  |
|**Python**    |實驗|         |
|**PHP**       |實驗|         |
|**TypeScript**|實驗|         |
|**Batch**     |實驗|         |
|**Bash**      |實驗|         |
|**PowerShell**|實驗|         |

如需詳細資訊，請參閱 <<c0> [ 支援的語言](https://docs.microsoft.com/azure/azure-functions/supported-languages)。

## <a name="app-service-plans"></a>App service 方案

函式都會受到*app service 方案*。 方案會定義函式應用程式所使用的資源。 您可以指派至區域的計劃，決定大小和數目，將會使用，並選擇定價層的虛擬機器。 函式應用程式可能使用真正的無伺服器方法，如**耗用量**計劃。 取用方案會調整後端會自動根據負載。

如需詳細資訊，請參閱 < [App service 方案](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)。

## <a name="create-your-first-function"></a>建立您的第一個函式

有三種常見的方式，您可以建立函式應用程式。

* 在入口網站中的指令碼函式。
* 建立所需的資源使用 Azure 命令列介面 (CLI)。
* 建立使用您最喜愛的 IDE，在本機的函式，並將其發行至 Azure。

如需有關如何在入口網站中建立的指令碼式的函式的詳細資訊，請參閱[在 Azure 入口網站中建立您的第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)。

若要建立從 Azure CLI，請參閱[建立第一個函式中，使用 Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)。

若要從 Visual Studio 中建立函式，請參閱[建立第一個函式使用 Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)。

## <a name="understand-triggers-and-bindings"></a>了解觸發程序和繫結

函式會叫用*觸發程序*，而且可以有一個。 除了叫用函數，特定觸發程序也做為繫結。 您也可以定義多個繫結，除了觸發程序。 *繫結*以宣告方式將資料連接至您的程式碼。 它們可以傳入 （輸入），或接收資料 （輸出）。 觸發程序和繫結都函式讓您輕鬆地使用。 繫結移除以手動方式建立資料庫或檔案系統連線的額外負荷。 所有的繫結所需的資訊都包含在特殊*functions.json*指令碼檔案，或使用程式碼中的屬性宣告。

某些常見的觸發程序包括：

* 上傳或儲存體中變更檔案或資料夾時，blob 儲存體： 叫用您的函式。
* HTTP： 叫用您的函式，例如 REST API。
* 當佇列中的項目存在，佇列： 叫用您的函式。
* 計時器： 叫用您的函式，在一般的頻率。

繫結的範例包括：

* CosmosDB： 輕鬆地連接至資料庫以載入或儲存檔案。
* 資料表儲存體： 使用您的函式應用程式中的索引鍵/值儲存體。
* 佇列儲存體： 輕鬆地從佇列擷取項目，或將新的項目放在佇列上。

下例*functions.json*檔案會定義觸發程序和繫結：

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

在此範例中，變更至 blob 儲存體所觸發的函式`images`容器。 檔案的資訊會傳入，因此觸發程序也可以當做繫結。 另一個繫結存在，將資訊放入佇列，名為`images`。

以下是 C# 指令碼函式：

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

範例是檔案的簡單的函式可接受名稱已修改或上傳至 blob 儲存體，且將它放入佇列，以供稍後處理。

如需觸發程序和繫結的完整清單，請參閱 < [Azure Functions 觸發程序和繫結概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)。

## <a name="proxies"></a>Proxy

Proxy 提供您的應用程式重新導向功能。 Proxy 公開的端點，並將該端點對應至另一個資源。 使用 proxy，您可以：

* 重新路由傳送至另一個端點的連入要求。
* 它會傳遞之前，請修改連入要求。
* 修改或提供回應。

是這類情況下使用 proxy:

* 簡化、 縮短兩次，或變更 URL。
* 提供一致的 API 前置詞，多個後端服務。
* 模擬正在開發的端點的回應。
* 提供已知端點的靜態回應。
* 後端正在移動或移轉時，讓 API 端點為一致的。

Proxy 會儲存為 JSON 定義中。 請看以下範例：

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

`Domain Redirect` Proxy 會縮短的路由，並將其對應至較長的函式資源。 轉換看起來像：

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

`Root` Proxy 會傳送至根 URL 的任何項目 (`https://--shorturl--/`) 並將它重新導向的文件網站。

使用 proxy 的範例所示的影片[Azure： 將應用程式帶至雲端，無伺服器 Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102)。 即時本機 SQL Server 上執行的 ASP.NET Core 應用程式移轉到 Azure 雲端。 為了重構傳統的 Web API 專案，使用函式會使用 proxy。

如需 Proxy 的詳細資訊，請參閱[使用 Azure Functions Proxy](https://docs.microsoft.com/azure/azure-functions/functions-proxies)。

>[!div class="step-by-step"]
[上一頁](azure-serverless-platform.md)
[下一頁](application-insights.md)