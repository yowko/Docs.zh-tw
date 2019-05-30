---
title: 使用可為 Null 的參考類型進行設計
description: 本進階教學課程提供可為 Null 的參考類型簡介。 您將了解如何在參考值可能為 Null 時表達您的設計意圖，以及在它們不能為 Null 時強制執行編譯器。
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 289b864aaa0380a31e93ef223fb5b5780e35892a
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195840"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>教學課程：使用可為 Null 的參考型別遷移現有程式碼

C# 8 引進了**可為 Null 的參考類型**，其可利用可為 Null 的實值類型補充實值類型的相同方式來補充參考類型。 您可以藉由將 `?` 附加至類型，來將變數宣告為**可為 Null 的參考類型**。 例如，`string?` 代表可為 Null 的 `string`。 您可以使用這些新類型更清楚地表達設計意圖：部分變數「永遠都必須有值」，而其他變數「可能會遺漏值」。 任何參考型別的現有變數都會解譯成不可為 Null 的參考型別。 

在本教學課程中，您將了解如何：

> [!div class="checklist"]
> * 在您使用程式碼時啟用 Null 參考檢查。
> * 診斷並修正與 Null 值相關的不同警告。
> * 管理啟用可為 Null 內容及停用可為 Null 內容之間的介面。
> * 控制可為 Null 的註釋內容。

## <a name="prerequisites"></a>必要條件

您將需要設定您的機器，以執行 .NET Core (包括 C# 8.0 搶鮮版 (Beta) 編譯器)。 您可以在 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 或最新 [.NET Core 3.0 Preview](https://dotnet.microsoft.com/download/dotnet-core/3.0) 中找到 C# 8 搶鮮版 (Beta) 編譯器。

本教學課程假設您已熟悉 C# 和 .NET，包括 Visual Studio 或 .NET Core CLI。

## <a name="explore-the-sample-application"></a>探索應用程式範例

您將遷移的應用程式範例是一個 RSS 摘要讀取器 Web 應用程式。 它會從單一 RSS 摘要讀取，並顯示最新文章的摘要。 您可以按一下任何一篇文章，前往網站。 應用程式相對較新，但是在可為 Null 參考型別開放使用前撰寫的。 應用程式的設計決策代表了健全的準則，但並未利用這項重要的語言功能。

應用程式範例包含了單元測試程式庫，可驗證應用程式的主要功能。 若您根據所產生的警告變更任何實作，該專案可使安全升級更為容易。 您可以從 [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) GitHub 存放庫下載起始程式碼。

您的遷移專案目標應利用新的語言功能，使您可以清楚地表達您在變數可 NULL 性上的意圖，而透過這種方式進行此操作時，編譯器不會在您將可為 Null 註釋內容及可為 Null 警告內容設為 `enabled` 時產生警告。

## <a name="upgrade-the-projects-to-c-8"></a>將專案升級至 C# 8

良好的第一個步驟，便是判斷移轉任務的範圍。 請從將專案升級至 C# 8.0 (或更新版本) 開始。 將 `LangVersion` 項目新增到 Web 專案及單元測試專案的 csproj 檔案：

```xml
<LangVersion>8.0</LangVersion>
```

升級語言版本會選取 C# 8.0，但不會啟用可為 Null 註釋內容或可為 Null 警告內容。 重建專案，確保建置過程中沒有任何警告。

良好的下一個步驟，便是開啟可為 Null 註釋內容，查看產生了多少警告。 將下列項目直接新增至解決方案中兩個 csproj 檔案的 `LangVersion` 項目下方：

```xml
<Nullable>enable</Nullable>
```

> [!IMPORTANT]
> `Nullable` 元素先前稱為 `NullableContextOptions`。 重新命名是在 Visual Studio 2019，16.2-p1 中發生的。 .NET Core SDK 3.0.100-preview5-011568 沒有此變更。 若您使用 .NET Core CLI，您將必須使用 `NullableContextOptions`，直到下一個預覽版推出。

執行測試建置，並注意警告清單。 在這個小型應用程式中，編譯器產生五個警告，因此您很有可能會將可為 Null 註釋內容維持在啟用狀態，並開始修正整個專案的警告。

但這種策略僅適用於較小的專案。 針對較大的專案，為整個程式碼基底啟用可為 Null 註釋內容，所產生警告數量可能會讓系統化修正警告的過程變得更為困難。 針對較大的企業專案，建議您一次遷移一個專案。 在每個專案中，一次遷移一個類別或檔案。

## <a name="warnings-help-discover-original-design-intent"></a>警告可協助您探索原始的設計意圖

有兩個類別會產生多個警告。 從 `NewsStoryViewModel` 類別開始。 從兩個 csproj 檔案中移除 `Nullable` 項目，可讓您將警告範圍限制在您目前使用的程式碼區段。 開啟 *NewsStoryViewModel.cs* 檔案，新增下列指示詞，以啟用 `NewsStoryViewModel` 的可為 Null 註釋內容，並遵循該類別定義來還原它：

```csharp
#nullable enable
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; }
    public string Uri { get; set; }
}
#nullable restore
```

這兩個指示詞可協助您專注在移轉的工作上。 可為 Null 警告會針對您目前正在使用的程式碼區域產生。 您會將它們維持在開啟狀態，直到您準備好為整個專案開啟警告為止。 您應使用 `restore` 而非 `disable` 值，避免稍後在您開啟整個專案的可為 Null 註釋時意外停用內容。 一旦您開啟了整個專案的可為 Null 註釋內容，您便可以移除該專案所有的 `#nullable` pragma。

`NewsStoryViewModel` 類別是資料轉送物件 (DTO)，而其中兩個屬性為讀取/寫入字串：

[!code-csharp[InitialViewModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

這兩個屬性會造成 `CS8618`，「不可為 Null 屬性尚未初始化」。 這已相當清楚：兩個 `string` 屬性在建構 `NewsStoryViewModel` 時都具備了 `null` 預設值。 重要的是探索 `NewsStoryViewModel` 物件的建構方式。 查看此類別，您無法辨識 `null` 值究竟是設計的一部分，還是這些物件會在建立其中一個時設為非 Null 值。 `NewsService` 類別的 `GetNews` 方法中建立了新的故事：

[!code-csharp[StarterCreateNewsItem](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

先前的程式碼區塊中此時又發生了一些事情。 此應用程式使用 [AutoMapper](https://automapper.org/) NuGet 套件來從 `ISyndicationItem` 建構新的項目。 您發現新的故事項目已經建構完成，而屬性也已在單一陳述式中設定。 這表示 `NewsStoryViewModel` 的設計指出這些屬性永遠都不應該具備 `null` 值。 這些屬性應為**不可為 Null 參考型別**。 這種方式最能表達原始的設計意圖。 事實上，任何 `NewsStoryViewModel`「都會」使用非 Null 值正確具現化。 這可讓下列的初始化程式碼成為有效修正：

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

將 `Title` 和 `Uri` 指派為 `default` (針對 `string` 型別為 `null`) 不會變更程式的執行階段行為。 `NewsStoryViewModel` 仍然會使用 Null 值建構，但現在編譯器不會再回報警告。 **Null 寬恕運算子** (即跟隨在 `default` 後方的 `!` 字元) 會告知編譯器先前的運算式並非 Null。 這項技術在其他變更對程式碼基底強制產生較大的變更時非常方便，但在此應用程式中，有另外一種相較之下更快且更好的解決方案：將 `NewsStoryViewModel` 設為固定型別，並在建構函式中設定所有屬性。 對 `NewsStoryViewModel` 進行下列變更：

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

完成之後，您需要更新設定 AutoMapper 的程式碼，讓其使用建構函式而非設定屬性。 開啟 `NewsService.cs`，在檔案的底部尋找下列程式碼：

[!code-csharp[StarterAutoMapper](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

該程式碼會將 `ISyndicationItem` 物件的屬性對應到 `NewsStoryViewModel` 屬性。 您想要 AutoMapper 改為使用建構函式來提供對應。 請使用下列 automapper 組態，取代以上程式碼：

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

請注意，由於這個類別相當小且您已仔細地檢查過，您應在此類別的宣告上方開啟 `#nullable enable` 指示詞。 對建構函式的變更可能會中斷某些東西，因此建議您在繼續之前執行所有測試並測試應用程式。

第一組變更示範了在原始設計指出變數不應設為 `null` 時探索的方式。 這項技術稱為**以建構修正**。 您宣告物件及其屬性不可在建構時為 `null`。 編譯器的流程分析會保證那些屬性在建構完成後不會設為 `null`。 請注意，此建構函式是由外部程式碼呼叫，而程式碼並非**可為 Null 遺忘**。 新的語法不會提供執行階段檢查。 外部程式碼可能會規避編譯器的流程分析。 

其他時候，類別的結構會提供意圖的不同線索。 開啟 *Pages* 資料夾中的 *Error.cshtml.cs* 檔案。 `ErrorViewModel` 包含下列程式碼：

[!code-csharp[StarterErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

將 `#nullable enable` 新增到類別宣告之前，並將 `#nullable restore` 指示詞新增到該宣告之後。 您會收到一個警告，告知您 `RequestId` 並未初始化。 藉由查看類別，您應判斷該 `RequestId` 屬性在某些情況下應為 Null。 `ShowRequestId` 屬性的存在指出可能遺失值。 因為 `null` 是有效的，請在 `string` 型別上新增 `?` 來指出 `RequestId` 屬性是「可為 Null 的參考型別」。 最終類別看起來會和下列範例相似：

[!code-csharp[FinishedErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

檢查屬性的使用方式，您便會發現在與其建立關聯的頁面上，會在於標記中轉譯它之前檢查該屬性是否為 Null。 這便是可為 Null 參考型別的安全使用方式，因此您已不須再對此類別進行任何操作。

## <a name="fixing-nulls-causes-change"></a>修正 Null 會造成變更

通常，修正一組警告會在相關程式碼中建立新的警告。 讓我們透過修正 `index.cshtml.cs` 類別，查看警告實際運作的方式。 請開啟 `index.cshtml.cs` 檔案並檢查程式碼。 此檔案包含索引頁背後的程式碼：

[!code-csharp[StarterIndexModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

新增 `#nullable enable` 指示詞，您便會看到兩個警告。 `ErrorText` 屬性或 `NewsItems` 屬性都並未初始化。 檢查此類別，可能會讓您相信兩個屬性都應是可為 Null 參考型別：兩個屬性都具有私人 setter。 其中剛好有一個已在 `OnGet` 方法中指派。 在進行變更前，請先觀察兩個屬性的消費者。 在頁面本身中，會在為任何錯誤產生標記前再度檢查 `ErrorText` 是否為 Null。 `NewsItems` 集合也會受到檢查是否為 `null`，以及檢查其是否具有項目。 一種快速修正的方式，便是將兩個屬性設為可為 Null 的參考型別。 更佳修正方式是將集合設為不可為 Null 的參考型別，並在擷取新聞時將項目新增到現有集合。 第一個修正是將 `?` 新增到 `ErrorText` 的 `string` 型別：

[!code-csharp[UpdateErrorText](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

這項變更不會影響其他程式碼，因為任何對 `ErrorText` 屬性的存取都已由 Null 檢查防護。 接下來，請初始化 `NewsItems` 清單並移除屬性 setter，使其成為唯讀屬性：

[!code-csharp[InitializeNewsItems](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

這會修正警告，但會引進另一項錯誤。 `NewsItems` 清單現在已是**以建構修正**，但在 `OnGet` 中設定清單的程式碼也必須變更，才能符合新的 API。 取代指派，請改為呼叫 `AddRange` 來將新的項目新增到現有清單：

[!code-csharp[AddRange](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

使用 `AddRange` 而非指派，表示 `GetNews` 方法可傳回 `IEnumerable` 而非 `List`。 這會省下一個配置。 變更方法的簽章並移除 `ToList` 呼叫，如下列程式碼範例所示：

[!code-csharp[GetNews](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

變更簽章也會中斷其中一項測試。 開啟 `SimpleFeedReader.Tests` 專案 `Services` 資料夾中的 `NewsServiceTests.cs` 檔案。 巡覽至 `Returns_News_Stories_Given_Valid_Uri` 測試，並將 `result` 變數的型別變更為 `IEnumerable<NewsItem>`。 變更型別表示 `Count` 屬性不再開放使用，因此請將 `Assert` 中的 `Count` 屬性取代為對 `Any()` 的呼叫：

[!code-csharp[FixTests](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

您也需要將一個 `using System.Linq` 陳述式新增到檔案的開頭。

這組變更醒目提示更新包含泛型具現化之程式碼時的特別考量事項。 不可為 Null 型別清單及清單中的項目。 其中之一或兩者都可以是可為 Null 型別。 允許下列所有宣告：

- `List<NewsStoryViewModel>`：不可為 Null 檢視模型的不可為 Null 清單。
- `List<NewsStoryViewModel?>`：可為 Null 檢視模型的不可為 Null 清單。
- `List<NewsStoryViewModel>?`：不可為 Null 檢視模型的可為 Null 清單。
- `List<NewsStoryViewModel?>?`：可為 Null 檢視模型的可為 Null 清單。

## <a name="interfaces-with-external-code"></a>連接外部程式碼

您已對 `NewsService` 類別進行變更，因此請開啟該類別的 `#nullable enable` 註釋。 這將不會產生任何新的警告。 但是，仔細檢查類別有助於說明編譯器流程分析的一些限制。 檢查建構函式：

[!code-csharp[ServiceConstructor](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

`IMapper` 參數型別為不可為 Null 的參考。 ASP.NET Core 基礎結構程式碼會呼叫它，因此編譯器並不真的了解 `IMapper` 永遠不會為 Null。 若無法解析必要服務，預設 ASP.NET Core 相依性 (DI) 容器會擲回例外狀況，因此程式碼是正確的。 編譯器無法驗證所有對您公用 API 進行的呼叫，即使程式碼是在啟用可為 Null 註釋內容的情況下編譯也一樣。 此外，您的程式庫可能會由專案取用，但那些專案可能尚未加入使用可為 Null 的參考型別。 即使您已將它們宣告為不可為 Null 類型，也請驗證針對公用 API 進行的輸入。

## <a name="get-the-code"></a>取得程式碼

您已修正您在初始測試編譯中識別的警告，因此現在您可以開啟兩個專案的可為 Null 註釋內容。 重建專案，編譯器不會回報任何警告。 您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished) GitHub 存放庫取得完成專案的程式碼。

支援可為 Null 參考型別的新功能，可協助您尋找並修正處理您程式碼中 `null` 值方式中潛在的錯誤。 啟用可為 Null 註釋內容，可讓您表達您的設計意圖：有些變數永遠不該為 Null，其他變數則可以包含 Null 值。 這些功能可讓您更輕易地宣告設計意圖。 同樣的，可為 Null 警告內容會指示編譯器，在您違反該意圖時發出警告。 這些警告會引導您進行更新，讓您的程式碼復原性更佳，並降低在執行期間擲回 `NullReferenceException` 的機率。 您可以控制這些內容的範圍，讓您專注在要遷移的程式碼本機區域，而無須更動剩餘的程式碼基底。 在實務上，您可以將此移轉任務作為您類別一般維護的一部分。 本教學課程示範了遷移應用程式，以使用可為 Null 參考型別的過程。 您可以透過檢查 [Jon Skeet](https://github.com/jskeet) 為了將可為 Null 參考型別併入 [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits) 所製作的 PR，來探索這項程序的更大實際範例。
