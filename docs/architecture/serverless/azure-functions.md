---
title: Azure Functions 無伺服器應用程式
description: 'Azure 函式提供多種語言的無伺服器功能 (c #、JavaScript、JAVA) 和平臺，以提供事件驅動的立即調整程式碼。'
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 08e1aaecdee753dc25cca0d6356caaafae1ad510
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557112"
---
# <a name="azure-functions"></a>Azure Functions

Azure Functions 提供無伺服器計算體驗。 函式是由 *觸發* 程式叫用 (例如存取 HTTP 端點或計時器) ，並執行程式碼區塊或商務邏輯。 函式也支援連接到儲存體和佇列等資源 *的特製化* 系結。

![Azure 函數標誌](./media/azure-functions-logo.png)

目前的執行階段版本3.0 支援跨平臺 .NET Core 3.1 應用程式。 除了 c # 以外的其他語言（例如 JavaScript、F # 和 JAVA）也受到支援。 在入口網站中建立的函式會提供豐富的腳本語法。 建立為獨立專案的函式可以使用完整的平臺支援和功能進行部署。

如需詳細資訊，請參閱 [Azure Functions 檔](/azure/azure-functions)。

## <a name="programming-language-support"></a>程式設計語言支援

正式運作 (GA) 都支援下列語言。

|語言      |支援的執行時間|
|--------------|------------------|
|**C#**        |.NET Core 3.1     |
|**JavaScript**|節點 10 & 12      |
|**F#**        |.NET Core 3.1     |
|**Java**      |Java 8            |
|**Python**    |Python 3.6、3.7、& 3。8|
|**TypeScript**|節點 10 & 12 (via JavaScript) |
|**PowerShell**|PowerShell Core 6|

如需詳細資訊，請參閱[支援的語言](/azure/azure-functions/supported-languages)。

## <a name="app-service-plans"></a>App service 方案

函數是由 *app service 方案* 支援。 此方案會定義函數應用程式所使用的資源。 您可以將方案指派給區域、判斷將使用的虛擬機器大小和數量，以及挑選定價層。 針對真正的無伺服器方法，函數應用程式可能會使用 **取用方案。** 取用方案會根據負載自動調整後端。

函數應用程式的另一個裝載選項是 [Premium 方案](/azure/azure-functions/functions-premium-plan)。 此方案提供「永遠開啟」實例來避免冷啟動、支援 VNet 連線等 advanced 功能，並可在 premium 硬體上執行。

如需詳細資訊，請參閱 [App service 方案](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)。

## <a name="create-your-first-function"></a>建立您的第一個函式

有三種常見的方式可供您建立函數應用程式。

- 在入口網站中編寫函數的腳本。
- 使用 Azure CLI 建立必要的資源。
- 使用您最愛的 IDE 在本機建立函式，並將其發佈至 Azure。

如需在入口網站中建立腳本函式的詳細資訊，請參閱在 [Azure 入口網站中建立您的第一個函數](/azure/azure-functions/functions-create-first-azure-function)。

若要從 Azure CLI 建立，請參閱 [使用 Azure CLI 建立您的第一個函數](/azure/azure-functions/functions-create-first-azure-function-azure-cli)。

若要從 Visual Studio 建立函式，請參閱 [使用 Visual Studio 建立您的第一個函數](/azure/azure-functions/functions-create-your-first-function-visual-studio)。

## <a name="understand-triggers-and-bindings"></a>瞭解觸發程式和系結

函式是由 *觸發* 程式叫用的，而且可以只有一個。 除了叫用函式之外，某些觸發程式也會作為系結。 除了觸發程式之外，您也可以定義多個系結。 系結 *會提供宣告* 式方式，將資料連線到您的程式碼。 您可以在 (輸入中傳遞它們) 或接收資料 (輸出) 。 觸發程式和系結可讓函式便於使用。 系結會移除手動建立資料庫或檔案系統連接的額外負荷。 系結所需的所有資訊都包含在腳本的特殊 *functions.js* 中，或使用程式碼中的屬性來宣告。

一些常見的觸發套裝程式括：

- Blob 儲存體：當檔案或資料夾在儲存體中上傳或變更時，就會叫用您的函式。
- HTTP：叫用您的函數，例如 REST API。
- 佇列：當專案存在於佇列中時，叫用您的函式。
- 計時器：定期叫用您的函數。

系結的範例包括：

- CosmosDB：輕鬆地連接到資料庫以載入或儲存檔案。
- 資料表儲存體：使用函式應用程式中的索引鍵/值儲存體。
- 佇列儲存體：輕鬆地從佇列中取出專案，或將新專案放在佇列上。

下列範例 *functions.json* file 會定義觸發程式和系結：

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

在此範例中，此函式是由容器中 blob 儲存體的變更所觸發 `images` 。 會傳入檔案的資訊，因此觸發程式也會作為系結。 有另一個系結可將資訊放入名為的佇列 `images` 。

以下是函式的 c # 腳本：

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

此範例是一個簡單的函式，它會採用已修改或上傳至 blob 儲存體的檔案名稱，並將它放在佇列上以供稍後處理。

如需觸發程式和系結的完整清單，請參閱 [Azure Functions 觸發程式和](/azure/azure-functions/functions-triggers-bindings)系結概念。

>[!div class="step-by-step"]
>[上一個](azure-serverless-platform.md) 
>[下一步](application-insights.md)
