---
title: 功能旗標
description: 利用 Azure App Config 在雲端原生應用程式中執行功能旗標
ms.date: 05/03/2020
ms.openlocfilehash: 72e1bfe777854a74fcac926811caf97e59986146
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83398306"
---
# <a name="feature-flags"></a>功能旗標

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在第1章中，我們 affirmed 雲端原生與速度和靈活性有關。 使用者預期快速回應能力、創新功能和零停機時間。 `Feature flags`是現代化的部署技術，可協助提升雲端原生應用程式的靈活性。 它們可讓您將新功能部署到生產環境，但限制其可用性。 使用交換器的筆勢，您可以為特定使用者啟用新功能，而不需要重新開機應用程式或部署新的程式碼。 它們會將新功能的發行與程式碼部署分開。

功能旗標是以條件式邏輯為基礎所建立，可在執行時間控制使用者的功能可見度。 在新式雲端原生系統中，通常會提早將新功能部署到生產環境，但會以有限的物件進行測試。 隨著信心增加，您可以將此功能累加地推出給更廣泛的觀眾。

功能旗標的其他使用案例包括：

- 將 premium 功能限制為願意支付較高訂閱費用的特定客戶群組。
- 藉由快速停用問題功能來讓系統穩定，避免回復或立即提供者的風險。
- 在尖峰使用期間，停用具有高資源耗用量的選用功能。
- 執行 `experimental feature releases` 小型使用者區段，以驗證可行性和熱門程度。

功能旗標也會提升 `trunk-based` 開發。 它是一個原始檔控制分支模型，開發人員會在其中對單一分支中的功能進行共同作業。 此方法可將合併大量長時間執行之功能分支的風險和複雜度降到最低。 功能在啟用之前無法使用。

## <a name="implementing-feature-flags"></a>執行功能旗標

就核心而言，功能旗標是簡單的參考 `decision object` 。 它會傳回或的布林 `on` 狀態 `off` 。 旗標通常會包裝封裝功能的程式碼區塊。 旗標的狀態會決定是否要針對指定的使用者執行該程式碼區塊。 圖10-11 顯示執行的方式。

```c#
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

**圖 10-11** -簡單的功能旗標執行。

請注意此方法如何將決策邏輯與功能程式碼分開。

在第1章中，我們討論了 `Twelve-Factor App` 。 建議的指引是保留應用程式可執行程式碼外部的設定。 如有需要，可以從外部來源讀取設定。 功能旗標設定值也應該獨立于其程式碼基底。 藉由具體化個別存放庫中的旗標設定，您可以在不修改和重新部署應用程式的情況下變更旗標狀態。

[Azure 應用程式組態](https://docs.microsoft.com/azure/azure-app-configuration/overview)提供功能旗標的集中式存放庫。 使用它，您可以定義不同種類的功能旗標，並快速且安心地操作其狀態。 您會將應用程式組態用戶端程式庫新增至應用程式，以啟用功能旗標功能。 支援各種程式設計語言架構。

功能旗標可以在[ASP.NET Core 服務](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core)中輕鬆地執行。 安裝 .NET 功能管理程式庫和應用程式組態提供者，可讓您以宣告方式將功能旗標新增至程式碼。 它們會啟用 `FeatureGate` 屬性，如此一來，您就不需要在程式碼基底中手動撰寫 if 語句。

一旦在啟動類別中設定之後，您就可以在控制器、動作或中介軟體層級新增功能旗標功能。 圖10-12 顯示控制器和動作的執行：

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

**圖 10-12** -控制器和動作中的功能旗標執行。

如果功能旗標已停用，使用者會收到404（找不到）狀態碼，且沒有回應主體。

功能旗標也可以直接插入 c # 類別中。 圖10-13 顯示功能旗標插入：

```c#
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

**圖 10-13** -將功能旗標插入至類別。

功能管理程式庫會管理幕後的功能旗標生命週期。 例如，若要將設定存放區的大量呼叫降到最低，程式庫快取旗標會指出指定的持續時間。 它們可以保證在要求呼叫期間不會有旗標狀態。 它們也會提供 `Point-in-time snapshot` 。 您可以重建任何索引鍵/值的歷程記錄，並在前七天內的任何時間提供其過去的值。

>[!div class="step-by-step"]
>[上一個](devops.md) 
>[下一步](infrastructure-as-code.md)
