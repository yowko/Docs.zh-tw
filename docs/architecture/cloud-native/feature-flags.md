---
title: 功能旗標
description: 利用 Azure App Config 在雲端原生應用程式中執行功能旗標
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: be4ab307069065975dc22d6bd984e12a2ea1457d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540461"
---
# <a name="feature-flags"></a>功能旗標

在第1章中，我們 affirmed 雲端原生相當於速度和靈活性。 使用者預期快速回應性、創新功能和零停機時間。 `Feature flags` 是新式的部署技術，可協助提高雲端原生應用程式的靈活性。 它們可讓您將新功能部署到生產環境中，但限制其可用性。 使用開關的筆勢，您可以為特定使用者啟用新功能，而不需要重新開機應用程式或部署新的程式碼。 它們會將新功能的發行與程式碼部署分開。

功能旗標是以條件式邏輯為基礎，可在執行時間控制使用者的功能可視性。 在新式的雲端原生系統中，通常會提早將新功能部署到生產環境中，但以有限的物件進行測試。 當信賴度增加時，可以將此功能以累加方式推出給更廣大的觀眾。

功能旗標的其他使用案例包括：

- 將 premium 功能限制為願意支付更高訂用帳戶費用的特定客戶群組。
- 藉由快速停用問題功能來穩定系統，避免復原或立即修正的風險。
- 在尖峰使用期間停用具有高資源耗用量的選用功能。
- 對 `experimental feature releases` 小型使用者區段進行驗證，以驗證可行性和熱門程度。

功能旗標也會促進 `trunk-based` 開發。 它是一種原始檔控制分支模型，開發人員會在此模型中對單一分支中的功能進行共同作業。 此方法可將合併大量長時間執行功能分支的風險和複雜性降至最低。 功能在啟用之前無法使用。

## <a name="implementing-feature-flags"></a>執行功能旗標

在其核心中，功能旗標是簡單的參考 `decision object` 。 它會傳回或的布林 `on` 狀態 `off` 。 旗標通常會包裝封裝功能功能的程式碼區塊。 旗標的狀態會決定是否要為指定的使用者執行該程式碼區塊。 圖10-11 顯示執行。

```csharp
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

**圖 10-11** -簡單的功能旗標實行。

請注意這個方法如何分隔決策邏輯與功能程式碼。

在第1章中，我們討論過 `Twelve-Factor App` 。 建議在應用程式可執行程式碼外部保留設定設定的指導方針。 如有需要，可以從外部來源讀取設定。 功能旗標設定值也應該獨立于其程式碼基底。 藉由在不同的儲存機制中具體化旗標設定，您可以變更旗標狀態，而不需要修改和重新部署應用程式。

[Azure 應用程式組態](https://docs.microsoft.com/azure/azure-app-configuration/overview) 提供功能旗標的集中式存放庫。 使用它，您可以定義不同種類的功能旗標，並快速且安心地操作其狀態。 您可以將應用程式設定用戶端程式庫新增至您的應用程式，以啟用功能旗標功能。 支援各種程式設計語言架構。

功能旗標可以在 [ASP.NET Core 服務](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core)中輕鬆地執行。 安裝 .NET 功能管理程式庫和應用程式設定提供者，可讓您以宣告方式將功能旗標新增至您的程式碼。 它們可啟用 `FeatureGate` 屬性，讓您不必在程式碼基底中手動寫入 if 語句。

在啟動類別中設定之後，您可以在控制器、動作或中介軟體層級新增功能旗標功能。 圖10-12 顯示控制器和動作執行：

```csharp
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```csharp
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

**圖 10-12** -控制器和動作中的功能旗標實行。

如果停用功能旗標，使用者將會收到 404 (找不到) 狀態碼，且沒有回應主體。

功能旗標也可以直接插入 c # 類別。 圖10-13 顯示功能旗標插入：

```csharp
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

**圖 10-13** -功能旗標插入類別中。

功能管理程式庫會管理幕後的功能旗標生命週期。 例如，為了將大量呼叫設定存放區的次數降到最低，程式庫快取旗標會指出指定的持續時間。 它們可以保證在要求呼叫期間不會有旗標狀態。 它們也提供 `Point-in-time snapshot` 。 您可以重建任何索引鍵/值的歷程記錄，並在過去七天內的任何時間都提供其過去的值。

>[!div class="step-by-step"]
>[上一個](devops.md) 
>[下一步](infrastructure-as-code.md)
