---
title: 狀態管理
description: 瞭解在 ASP.NET Web Forms 和 Blazor 中管理狀態的不同方法。
author: csharpfritz
ms.author: jefritz
ms.date: 05/15/2020
ms.openlocfilehash: bac2f00330113725f09259ca31bdf857a8769f24
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062336"
---
# <a name="state-management"></a>狀態管理

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

狀態管理是 Web form 應用程式的主要概念，透過檢視狀態、會話狀態、應用程式狀態和回傳功能來提供。 此架構的這些具狀態功能有助於隱藏應用程式所需的狀態管理，並可讓應用程式開發人員專注于傳遞其功能。 有了 ASP.NET Core 和 Blazor，其中部分功能已重新放置，而部分已完全移除。 本章將回顧如何維護狀態，並以 Blazor 中的新功能提供相同的功能。

## <a name="request-state-management-with-viewstate"></a>使用 ViewState 的要求狀態管理

在討論 Web form 應用程式中的狀態管理時，許多開發人員會立即思考 ViewState。 在 Web form 中，ViewState 會藉由將大型編碼的文字區塊來回傳送至瀏覽器，來管理 HTTP 要求之間的內容狀態。 ViewState 欄位可能會因為包含許多元素的頁面內容而淹沒，可能會擴大到數 mb 的大小。

使用 Blazor 伺服器時，應用程式會維護與伺服器之間的持續連接。 當連接被視為使用中時，應用程式的狀態（稱為*線路*）會保留在伺服器記憶體中。 只有當使用者離開應用程式或應用程式中的特定頁面時，才會處置狀態。 使用中元件的所有成員都可以在與伺服器的互動之間取得。

這項功能有幾項優點：

- 元件狀態可立即使用，而且不會在互動之間重建。
- 狀態不會傳送至瀏覽器。

不過，記憶體內部元件狀態持續性有一些缺點需要注意：

- 如果伺服器在要求之間重新開機，則會遺失狀態。
- 您的應用程式網頁伺服器負載平衡解決方案必須包含粘滯會話，以確保來自相同瀏覽器的所有要求都會回到相同的伺服器。 如果要求移至不同的伺服器，狀態將會遺失。
- 伺服器上元件狀態的持續性可能會導致 web 伺服器上的記憶體壓力。

基於上述原因，請不要只相依元件的狀態來存放在伺服器的記憶體中。 您的應用程式也應該包含要求之間資料的一些支援資料存放區。 此策略的一些簡單範例：

- 在購物車應用程式中，將新增至購物車的新專案內容保存在資料庫記錄中。 如果伺服器上的狀態遺失，您可以將它從資料庫記錄中重建。
- 在多部分的 web 表單中，您的使用者會預期您的應用程式會記住每個要求之間的值。 將您的每個使用者貼文之間的資料寫入資料存放區，以便在多部分表單完成時，可以提取並組合成最終表單回應結構。

如需在 Blazor 應用程式中管理狀態的詳細資訊，請參閱[ASP.NET Core Blazor 狀態管理](/aspnet/core/blazor/state-management)。

## <a name="maintain-state-with-session"></a>使用會話維護狀態

Web form 開發人員可以使用 dictionary 物件來維護目前作用中使用者的相關資訊 <xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> 。 將具有字串索引鍵的物件新增至，是很容易的 `Session` ，而且該物件會在使用者與應用程式互動期間的後續時間使用。 若要嘗試排除與 HTTP 互動的管理， `Session` 物件可以輕鬆地維護狀態。

.NET Framework 物件的簽章與 `Session` ASP.NET Core `Session` 物件不同。 請先考慮[新 ASP.NET Core 會話的檔](/dotnet/api/microsoft.aspnetcore.http.isession)，然後再決定是否要遷移和使用新的會話狀態功能。

會話適用于 ASP.NET Core 和 Blazor 伺服器，但不建議在適當的情況下，用來將資料儲存在資料存放庫中。 如果訪客因隱私權考慮而拒絕在應用程式中使用 HTTP cookie，則會話狀態也無法運作。

[ASP.NET Core 文章的會話和狀態管理](/aspnet/core/fundamentals/app-state#session-state)中提供 ASP.NET Core 和會話狀態的設定。

## <a name="application-state"></a>應用程式狀態

`Application`Web form 架構中的物件會提供大規模的跨要求存放庫，以便與應用程式範圍的設定和狀態互動。 應用程式狀態是儲存各種應用程式設定內容的理想位置，這些屬性會由所有要求所參考，而不論提出要求的使用者為何。 物件的問題 `Application` 在於，資料不會跨多部伺服器保存。 重新開機之間的應用程式物件狀態已遺失。

如同 `Session` ，建議您將資料移至可由多個伺服器實例存取的持續性備份存放區。 如果您想要在要求和使用者之間存取的變動性資料，您可以輕鬆地將它儲存在單一服務中，以插入需要此資訊或互動的元件。

用來維護應用程式狀態和其耗用量的物件的結構，可能類似于下列的執行：

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

`MyApplicationState`物件只會在伺服器上建立一次，而且 `VisitorCounter` 會提取值並輸出到元件的標籤中。 `VisitorCounter`值應該保存並從支援的資料存放區中取出，以提供持久性和擴充性。

## <a name="in-the-browser"></a>在瀏覽器中

應用程式資料也可以在使用者的裝置上儲存在用戶端，以供稍後使用。 有兩種瀏覽器功能可讓使用者在不同範圍的瀏覽器中持續保存資料：

- `localStorage`-範圍限定于使用者的整個瀏覽器。 如果重載頁面，則會關閉並重新開啟瀏覽器，或以相同的 URL 開啟另一個索引標籤，而 `localStorage` 瀏覽器會提供相同的
- `sessionStorage`-範圍設定為使用者目前的瀏覽器索引標籤。如果重載索引標籤，則狀態會保持不變。 不過，如果使用者在應用程式中開啟另一個索引標籤，或關閉並重新開啟瀏覽器，則狀態會是 [遺失]。

您可以撰寫一些自訂的 JavaScript 程式碼來與這些功能互動，或者您可以使用許多 NuGet 套件來提供這項功能。 其中一個封裝是[AspNetCore. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage)。

如需利用此封裝與和互動的 `localStorage` 指示 `sessionStorage` ，請參閱[Blazor 狀態管理](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package)一文。

>[!div class="step-by-step"]
>[上一個](pages-routing-layouts.md) 
>[下一步](forms-validation.md)
