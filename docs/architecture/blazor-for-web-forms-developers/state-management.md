---
title: 狀態管理
description: 瞭解在 ASP.NET Web Forms 和 Blazor 中管理狀態的不同方法。
author: csharpfritz
ms.author: jefritz
ms.date: 05/15/2020
ms.openlocfilehash: 2ca811f886c6a245ac16c2bd66a68ff16e5bfc44
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267720"
---
# <a name="state-management"></a>狀態管理

狀態管理是 Web Form 應用程式的重要概念，可透過檢視狀態、會話狀態、應用程式狀態和回傳功能來提供。 這些架構的可設定狀態功能有助於隱藏應用程式所需的狀態管理，並讓應用程式開發人員專注于提供其功能。 在 ASP.NET Core 和 Blazor 中，其中有些功能已重新放置，而且已完全移除部分功能。 本章將探討如何使用 Blazor 中的新功能來維護狀態，並提供相同的功能。

## <a name="request-state-management-with-viewstate"></a>使用 ViewState 的要求狀態管理

在 Web Form 應用程式中討論狀態管理時，許多開發人員都會立即考慮 ViewState。 在 Web Form 中，ViewState 會藉由將大型編碼的文字區塊來回傳送至瀏覽器，來管理 HTTP 要求之間的內容狀態。 ViewState 欄位可能會因為包含許多專案的頁面內容而淹沒，可能會擴充到數 mb 的大小。

使用 Blazor 伺服器時，應用程式會維持與伺服器的持續連線。 當連接被視為使用中時，應用程式的狀態（稱為 *線路*）會保留在伺服器記憶體中。 只有當使用者導覽離開應用程式或應用程式中的特定頁面時，才會處置狀態。 使用中元件的所有成員都可以在與伺服器之間的互動之間使用。

這項功能有幾個優點：

- 元件狀態可立即使用，且不會在互動之間重建。
- 狀態不會傳送到瀏覽器。

不過，記憶體內部元件狀態持續性有一些缺點需要注意：

- 如果伺服器在要求之間重新開機，則狀態會遺失。
- 您的應用程式網頁伺服器負載平衡解決方案必須包含「粘滯話」，以確保來自相同瀏覽器的所有要求都會回到相同的伺服器。 如果要求移至不同的伺服器，狀態將會遺失。
- 伺服器上的元件狀態持續性可能會導致 web 伺服器上的記憶體壓力。

基於上述原因，請不要只相依元件的狀態，以存放在伺服器的記憶體中。 您的應用程式也應該針對要求之間的資料包含一些支援資料存放區。 此策略的一些簡單範例：

- 在購物車應用程式中，將新增至購物車的新專案內容保存在資料庫記錄中。 如果伺服器上的狀態遺失，您可以從資料庫記錄重新組成。
- 在多部分的 web 表單中，您的使用者會預期您的應用程式會記住每個要求之間的值。 將每個使用者的貼文之間的資料寫入資料存放區，以便在多部分表單完成時，將資料提取和組合成最終的表單回應結構。

如需在 Blazor apps 中管理狀態的其他詳細資料，請參閱 [ASP.NET Core Blazor 狀態管理](/aspnet/core/blazor/state-management)。

## <a name="maintain-state-with-session"></a>維護會話的狀態

Web Form 開發人員可以使用 dictionary 物件來維護目前作用中使用者的相關資訊 <xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> 。 您可以使用字串索引鍵將物件加入至 `Session` ，並在使用者與應用程式互動時，稍後再使用該物件。 在嘗試消除與 HTTP 互動的管理時， `Session` 物件讓您能夠輕鬆地維護狀態。

.NET Framework 物件的簽章與 `Session` ASP.NET Core 物件不相同 `Session` 。 在決定遷移和使用新的會話狀態功能之前，請先考慮 [新 ASP.NET Core 會話的檔](/dotnet/api/microsoft.aspnetcore.http.isession) 。

會話可在 ASP.NET Core 和 Blazor Server 中使用，但不建議您在適當的情況下將資料儲存在資料存放庫中。 如果訪客因隱私權考慮而拒絕在您的應用程式中使用 HTTP cookie，則會話狀態也無法運作。

ASP.NET Core 和會話狀態的設定可在 [ASP.NET Core 文章的會話和狀態管理](/aspnet/core/fundamentals/app-state#session-state)中取得。

## <a name="application-state"></a>應用程式狀態

`Application`Web Form 架構中的物件提供大量、跨要求的存放庫，可與應用程式範圍設定和狀態進行互動。 應用程式狀態是儲存各種應用程式設定屬性的理想位置，所有要求都會參考這些屬性，不論提出要求的使用者為何。 物件的問題 `Application` 在於，資料不會跨多個伺服器保存。 重新開機之間的應用程式物件狀態已遺失。

如同 `Session` ，建議將資料移至可供多個伺服器實例存取的持續性備份存放區。 如果有您想要能夠跨要求和使用者存取的變動性資料，您可以輕鬆地將它儲存在單一服務中，以插入需要此資訊或互動的元件中。

用來維護應用程式狀態和其耗用量的物件結構，可能類似于下列實作為：

```csharp
public class MyApplicationState
{
    public int VisitorCounter { get; private set; } = 0;

    public void IncrementCounter() => VisitorCounter += 1;
}
```

```csharp
app.AddSingleton<MyApplicationState>();
```

```razor
@inject MyApplicationState AppState

<label>Total Visitors: @AppState.VisitorCounter</label>
```

`MyApplicationState`物件只會在伺服器上建立一次，而且 `VisitorCounter` 會提取值並在元件的標籤中輸出。 `VisitorCounter`值應該保存並從支援資料存放區中抓取，以提供持久性和擴充性。

## <a name="in-the-browser"></a>在瀏覽器中

應用程式資料也可以儲存在使用者裝置上的用戶端，以供稍後使用。 有兩種瀏覽器功能可在使用者瀏覽器的不同範圍中保存資料：

- `localStorage` -範圍限定于使用者的整個瀏覽器。 如果頁面已重載，則會關閉並重新開啟瀏覽器，或使用相同的 URL 開啟另一個索引標籤，而 `localStorage` 瀏覽器會提供相同的索引標籤。
- `sessionStorage` -範圍設定為使用者目前的瀏覽器索引標籤。如果重載索引標籤，則狀態會持續存在。 不過，如果使用者對您的應用程式開啟另一個索引標籤，或關閉並重新開啟瀏覽器，則狀態會遺失。

您可以撰寫一些自訂 JavaScript 程式碼來與這些功能互動，或有許多可供您使用的 NuGet 套件，以提供這項功能。 其中一個這類套件是 [AspNetCore. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage)。

如需使用此封裝來與和互動的指示 `localStorage` `sessionStorage` ，請參閱 [Blazor 狀態管理](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package) 文章。

>[!div class="step-by-step"]
>[上一個](pages-routing-layouts.md) 
>[下一步](forms-validation.md)
