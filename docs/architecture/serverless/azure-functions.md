---
title: Azure 功能 - 無伺服器應用
description: Azure 函數提供跨多種語言（C#、JavaScript、JAVA）和平臺的無伺服器功能，以提供事件驅動的即時縮放代碼。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401610"
---
# <a name="azure-functions"></a>Azure Functions

Azure 函數提供無伺服器計算體驗。 函數由*觸發器*調用（例如訪問 HTTP 終結點或計時器），並執行代碼或業務邏輯塊。 函數還支援連接到存儲和佇列等資源的專用*綁定*。

![Azure 函數徽標](./media/azure-functions-logo.png)

Azure 函數框架有兩個版本。 舊版本支援完整的 .NET 框架，新的運行時支援跨平臺 .NET Core 應用程式。 除了 C# 之外，還支援其他語言，如 JavaScript、F# 和 JAVA。 在門戶中創建的函數提供了豐富的腳本語法。 作為獨立專案創建的函數可以使用完整的平臺支援和功能進行部署。

有關詳細資訊，請參閱[Azure 函數文檔](https://docs.microsoft.com/azure/azure-functions)。

## <a name="functions-v1-vs-v2"></a>功能 v1 vs. v2

Azure 函數運行時有兩個版本：1.x 和 2.x。 版本 1.x 通常可用 （GA）。 它支援來自門戶或 Windows 電腦的 .NET 開發，並使用 .NET 框架。 1.x 支援 C#、JavaScript 和 F#，支援 Python、PHP、TypeScript、批次處理、Bash 和 PowerShell 的實驗支援。

[版本 2.x 現在也通常可用](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/)。 它利用 .NET Core 並支援 Windows、macOS 和 Linux 電腦上跨平臺開發。 2.x 增加了對 JAVA 的一流支援，但尚未直接支援任何實驗語言。 版本 2.x 使用新的綁定擴充性模型，支援平臺的協力廠商擴展、綁定的獨立版本控制以及更簡化的執行環境。

> **1.x 中存在[具有綁定重定向支援的](https://github.com/Azure/azure-functions-host/issues/992)已知問題。** 此問題特定于 .NET 開發。 對庫的依賴項與運行時中包含的庫不同的專案將受到影響。 職能小組已承諾在問題上取得具體進展。 團隊將在 2.x 中處理綁定重定向，然後再進入常規可用性。 此處提供了包含建議的修補程式和解決方法的官方團隊聲明[：Azure 函數中的程式集解析](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions)。

有關詳細資訊，請參閱比較[1.x 和 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)。

## <a name="programming-language-support"></a>程式設計語言支援

以下語言在通用 （GA）、預覽版或實驗版中支援。

|Language      |1.x         |2.x      |
|--------------|------------|---------|
|**C#**        |GA          |預覽  |
|**JAVAscript**|GA          |預覽  |
|**F#**        |GA          |         |
|**JAVA**      |            |預覽  |
|**Python**    |Experimental|         |
|**Php**       |Experimental|         |
|**TypeScript**|Experimental|         |
|**批**     |Experimental|         |
|**Bash**      |Experimental|         |
|**電源外殼**|Experimental|         |

有關詳細資訊，請參閱[支援的語言](https://docs.microsoft.com/azure/azure-functions/supported-languages)。

## <a name="app-service-plans"></a>應用服務方案

函數由*應用服務方案*支援。 計畫定義函數應用使用的資源。 您可以將計畫分配給區域、確定將使用的虛擬機器的大小和數量，並選擇定價層。 對於真正的無伺服器方法，函數應用可以使用**消耗**計畫。 消耗計畫將根據負載自動縮放後端。

有關詳細資訊，請參閱[應用服務方案](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)。

## <a name="create-your-first-function"></a>建立您的第一個函式

有三種常見方法可以創建函數應用。

- 腳本在門戶中功能。
- 使用 Azure CLI 創建必要的資源。
- 使用您最喜愛的 IDE 在本地生成函數，並將它們發佈到 Azure。

有關在門戶中創建腳本化函數的詳細資訊，請參閱[在 Azure 門戶中創建第一個函數](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)。

要從 Azure CLI 生成，請參閱[使用 Azure CLI 創建第一個函數](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)。

要從視覺化工作室創建函數，請參閱[使用 Visual Studio 創建第一個函數](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)。

## <a name="understand-triggers-and-bindings"></a>瞭解觸發器和綁定

函數由*觸發器*調用，並且可以有一個。 除了調用函數之外，某些觸發器還用作綁定。 除了觸發器之外，您還可以定義多個綁定。 *綁定*提供了將資料連線到代碼的聲明性方法。 它們可以傳入（輸入）或接收資料（輸出）。 觸發器和綁定使功能便於使用。 綁定消除了手動創建資料庫或檔案系統連接的開銷。 綁定所需的所有資訊都包含在腳本的特殊*函數.json*檔中，或者使用代碼中的屬性聲明。

一些常見的觸發器包括：

- Blob 存儲：在存儲中上載或更改檔或資料夾時調用函數。
- HTTP：像 REST API 一樣調用函數。
- 佇列：當佇列中存在項時調用函數。
- 計時器：在常規節奏上調用函數。

綁定的示例包括：

- CosmosDB：輕鬆連接到資料庫以載入或保存檔。
- 表存儲：使用函數應用中的金鑰/值存儲。
- 佇列存儲：輕鬆從佇列中檢索項，或將新專案放在佇列中。

以下示例*函數.json*檔定義了觸發器和綁定：

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

在此示例中，函數由容器中 blob 存儲的`images`更改觸發。 檔的資訊傳入，因此觸發器也充當綁定。 存在另一個綁定，用於將資訊放到名為`images`的佇列中。

下面是函數的 C# 腳本：

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

該示例是一個簡單的函數，該函數獲取已修改或上載到 Blob 存儲的檔的名稱，並將其放在佇列中，以便以後處理。

有關觸發器和綁定的完整清單，請參閱[Azure 函數觸發器和綁定概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)。

## <a name="proxies"></a>Proxy

代理為您的應用程式提供重定向功能。 代理公開終結點並將該終結點映射到其他資源。 使用代理，您可以：

- 將傳入請求重新路由到另一個終結點。
- 在傳入請求傳遞之前對其進行修改。
- 修改或提供回應。

代理用於以下方案：

- 簡化、縮短或更改 URL。
- 為多個後端服務提供一致的 API 首碼。
- 類比對正在開發的終結點的回應。
- 向已知終結點提供靜態回應。
- 在移動或遷移後端時保持 API 終結點的一致性。

代理存儲為 JSON 定義。 範例如下：

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

代理`Domain Redirect`採用縮短的路由並將其映射到較長的函數資源。 轉換如下所示：

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

代理`Root`會獲取發送到根 URL （`https://--shorturl--/`） 的任何內容，並將其重定向到文檔網站。

使用代理的示例顯示在視頻[Azure 中：使用無伺服器 Azure 函數將應用帶到雲](https://channel9.msdn.com/events/Connect/2017/E102)中。 即時，在本地 SQL 伺服器上運行ASP.NET核心應用程式將遷移到 Azure 雲。 代理用於説明重構傳統的 Web API 專案以使用函數。

有關代理的詳細資訊，請參閱使用 Azure[函數代理](https://docs.microsoft.com/azure/azure-functions/functions-proxies)。

>[!div class="step-by-step"]
>[上一個](azure-serverless-platform.md)
>[下一個](application-insights.md)
