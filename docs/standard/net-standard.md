---
title: .NET Standard
description: 瞭解 .NET Standard、其版本，以及支援它的 .NET 支援。
ms.date: 10/05/2020
ms.prod: dotnet
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 93fb10538441d939e95bb48dcdd0e61d9267dde0
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765029"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) 是 .net api 的正式規格，可在多個 .net 執行中使用。 .NET Standard 背後的動機是在 .NET 生態系統中建立更高的一致性。 不過，.NET 5 採用不同的方法來建立一致性，而這種新方法在許多情況下都不需要 .NET Standard。 如需詳細資訊，請參閱本文稍後的 [.net 5 及 .NET Standard](#net-5-and-net-standard) 。

## <a name="net-implementation-support"></a>.NET 實作支援

不同的 .NET 實作會以特定版本的 .NET Standard 為目標。 每個 .NET 實作版本會宣佈它所支援的最高 .NET Standard 版本，此聲明表示它也會支援舊版。 例如，.NET Framework 4.6 會實 .NET Standard 1.3，這表示它會公開 .NET Standard 版1.0 至1.3 所定義的所有 Api。 同樣地，.NET Framework 4.6.1 會實 .NET Standard 1.4，而 .NET 5.0 則會執行 .NET Standard 2.1。

下表列出支援每個 .NET Standard 版本的 **最低** 執行版本。 這表示，較新版本的所列出的執行也支援對應的 .NET Standard 版本。 例如，.NET Core 2.1 和更新版本支援 .NET Standard 2.0 和更早版本。

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

若要尋找可作為您目標的最新版 .NET Standard，請執行下列步驟：

1. 尋找指出要作為您執行位置之 .NET 實作的資料列。
1. 在該資料列中，由左到右尋找指出您版本的資料行。
1. 資料行標題會指出您目標所支援的 .NET Standard 版本。 您也可以將目標設為任何較低的 .NET Standard 版本。 較高的 .NET Standard 版本也會支援您的實作。
1. 針對您想要作為目標的每個平台重複此程序。 如果您有多個目標平台，應該從中挑選最舊的版本。 例如，如果您想要在 .NET Framework 4.8 和 .NET 5.0 上執行，您可以使用的最高 .NET Standard 版本 .NET Standard 2.0。

### <a name="which-net-standard-version-to-target"></a>要以哪個 .NET Standard 版本作為目標

選擇要設為目標的 .NET Standard 版本時，請考慮這種取捨：

- 版本愈高，可供程式庫的程式碼使用的 Api 就越多。
- 版本越低，應用程式和程式庫可以使用您的程式庫。

建議您盡可能 *以最低* 版本的 .NET Standard 為目標。 因此，在您找到可作為目標的最新 .NET Standard 版本之後，請依照下列步驟操作：

1. 以次舊的 .NET Standard 版本為目標並建置您的專案。
2. 如果您的專案建置成功，便重複步驟 1。 否則，請將目標重新設定為次新版本，這會是您應該使用的版本。

不過，以較低的 .NET Standard 版本作為目標會產生數個支援相依性。 如果您的專案是以 .NET Standard 1.x 為目標，我們建議 *同時* 以 .NET Standard 2.0 作為目標。 這樣可簡化程式庫使用者的相依性圖形，而這些使用者會在 .NET Standard 2.0 相容的執行中執行，並減少需要下載的套件數目。

### <a name="net-standard-versioning-rules"></a>.NET Standard 版本控制規則

有兩個主要的版本控制規則：

- 累加：.NET Standard 版本就邏輯而言是同心圓：較新的版本會包含來自較舊版本的所有 API。 版本之間並沒有任何重大變更。
- 固定：.NET Standard 在出貨後，版本即凍結。

2.1 之後將不會有新的 .NET Standard 版本。 如需詳細資訊，請參閱本文稍後的 [.net 5 及 .NET Standard](#net-5-and-net-standard) 。

## <a name="specification"></a>規格

.NET Standard 規格是一組標準化的 API。 此規格是由 .NET 實作者維護，具體來說，Microsoft (包括 .NET Framework、.NET Core 和 Mono) 和 Unity。

### <a name="official-artifacts"></a>正式成品

正式規格是一組 *.cs* 檔案，可定義屬於標準的 api。 [dotnet/standard 存放庫](https://github.com/dotnet/standard)中的 [ref 目錄](https://github.com/dotnet/standard/tree/master/src/netstandard/ref)定義 .NET Standard API。

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) 中繼套件 ([原始檔](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)) 描述定義 (部分) 一或多個 .NET Standard 版本的程式庫集合。

像是 `System.Runtime` 等指定的元件，其描述：

- .NET Standard 的組件 (僅限其範圍)。
- 適用於該範圍的多個 .NET Standard 版本。

為了更方便閱讀及支援特定開發人員案例 (例如使用編譯器)，已提供衍生成品。

- [以 Markdown 撰寫的 API 清單](https://github.com/dotnet/standard/tree/master/docs/versions)
- 以 NuGet 套件散發並由 [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) 中繼套件參考的參考組件。

### <a name="package-representation"></a>封裝表示

.NET Standard 參考組件的主要散發工具是 NuGet 套件。 傳遞實作的方法有許多種，各自適合每種 .NET 實作。

NuGet 套件是以一個或多個[架構](frameworks.md)為目標。 .NET Standard 套件以 ".NET Standard" 架構為目標。 您可以使用 `netstandard` [compact TFM](frameworks.md) (以 .NET Standard framework 為目標，例如 `netstandard1.4`) 。 要在多個 .NET 上執行的程式庫應以此架構為目標。 對大多數的 API 來說，會以 `netstandard2.0` 為目標，因為提供的 API 數目，超過 .NET Standard 1.6 與 2.0 之間的一倍。

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/)中繼套件會參考定義 .NET Standard 的一組完整 NuGet 套件。  若要將 `netstandard` 設為目標，最常見方式是參考這個中繼套件。 它描述大約 40 種定義 .NET Standard 的 .NET 程式庫和相關 API，並提供其存取權。 您可以參考目標為 `netstandard` 的其他套件，以存取其他 API。

### <a name="versioning"></a>版本控制

規格不是單數的，而是以線性方式設定的一組 Api。 此標準的第一個版本會建立一組基準 API。 後續版本會新增 API，並繼承舊版所定義的 API。 從標準移除 Api 沒有任何已建立的布建。

.NET Standard 不是任何一個 .NET 執行特有的，也不符合任何這些執行的版本控制配置。

如先前所述，2.1 之後將不會有新的 .NET Standard 版本。

## <a name="target-net-standard"></a>目標 .NET Standard

您可以使用架構和中繼套件的組合來 [建立 .NET Standard 程式庫](../core/tutorials/libraries.md) `netstandard` `NETStandard.Library` 。

## <a name="net-framework-compatibility-mode"></a>.NET Framework 相容性模式

從 .NET Standard 2.0 開始，引進了 .NET Framework 相容性模式。 此相容性模式可讓 .NET Standard 專案可參考 .NET Framework 程式庫，就如同是為 .NET Standard 編譯一般。 並非所有專案都適合參考 .NET Framework 程式庫。例如，像是使用 Windows Presentation Foundation (WPF) API 的程式庫。

如需詳細資訊，請參閱 [.NET Framework 相容模式](../core/porting/third-party-deps.md#net-framework-compatibility-mode)。

## <a name="net-standard-libraries-and-visual-studio"></a>.NET Standard 程式庫與 Visual Studio

若要在 Visual Studio 中建立 .NET Standard 程式庫，請確定您已在 Windows 上安裝 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 或 Visual Studio 2017 15.3 版或更新版本，或在 macOS 上安裝 [Visual Studio for Mac 7.1 版](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 或更新版本。

若在您專案中只需要使用 .NET Standard 2.0 程式庫，也可於 Visual Studio 2015 中執行。 但需要安裝 NuGet 用戶端 3.6 或更新版本。 您可從 [NuGet下載](https://www.nuget.org/downloads)頁面，下載 Visual Studio 2015 的 NuGet 用戶端。

## <a name="net-5-and-net-standard"></a>.NET 5 和 .NET Standard

.NET 5 是 Microsoft 積極開發的 .NET 的實作為。 它是單一產品，具有一組統一的功能和 Api，可用於 Windows 傳統型應用程式和跨平臺主控台應用程式、雲端服務和網站。 .NET 5.0 [tfm](frameworks.md) 會反映這範圍廣泛的案例：

* `net5.0`

  這個 TFM 適用于隨處執行的程式碼。 有幾個例外狀況，它只包含可跨平臺運作的技術。 針對 .NET 5 程式碼， `net5.0` 取代 `netcoreapp` 和 `netstandard` tfm。

* `net5.0-windows`

  這是 [作業系統特定 tfm](frameworks.md#net-5-os-specific-tfms) 的範例，可將作業系統特定功能新增至所指的所有專案 `net5.0` 。

### <a name="when-to-target-net50-vs-netstandard"></a>何時將目標設為 net 5.0 與 netstandard

若為目標的現有程式碼 `netstandard` ，則不需要將 TFM 變更為 `net5.0` 。 .NET 5.0 會實 .NET Standard 2.1 及更早版本。 從 .NET Standard 重定為 .NET 5.0 的唯一原因是，要取得更多執行時間功能、語言功能或 Api 的存取權。 例如，為了使用 c # 9，您需要將目標設為 .NET 5.0。 您可以使用多目標 .NET 5.0 和 .NET Standard 來存取較新的功能，但仍可將程式庫提供給其他 .NET 執行。

以下是適用于 .NET 5 的新程式碼的一些指導方針：

* 應用程式元件

  如果您要使用程式庫將應用程式細分成數個元件，建議您將目標設 `net5.x` `5.x` 為您的應用程式可設為目標的最早 .net 5 版本。 為了簡單起見，最好將構成應用程式的所有專案都保留在相同版本的 .NET 上。 然後，您可以在任何地方採用相同的 BCL 功能。

* 可重複使用的程式庫

  如果您要建立可重複使用的程式庫，而您打算在 NuGet 上寄出，請考慮在觸達和可用功能集之間的取捨。 .NET Standard 2.0 是 .NET Framework 所支援的最新版本，因此它會對相當大的功能集提供良好的觸及範圍。 我們不建議將 .NET Standard 1.x 的目標設為目標，因為您會限制可用的功能集，以達到最大程度的增加。

  如果您不需要支援 .NET Framework，可以使用 .NET Standard 2.1 或 .NET 5。 建議您略過 .NET Standard 2.1，並直接移至 .NET 5。 最廣泛使用的程式庫最後會有 .NET Standard 2.0 和 .NET 5 的多目標。 支援 .NET Standard 2.0 可提供您最多的支援，而支援 .NET 5 可確保您可以針對已在 .NET 5 上的客戶運用最新的平臺功能。

### <a name="net-standard-problems"></a>.NET Standard 問題

以下是一些 .NET Standard 的問題，可協助說明為什麼 .NET 5 是在各平臺和工作負載之間共用程式碼的較佳方式：

- 緩慢以新增 Api

  .NET Standard 是建立成所有 .NET 執行都必須支援的 API 集，所以有建議的評論程式來加入新的 Api。 目標是只將可在所有目前和未來的 .NET 平臺中執行的 Api 標準化。 結果是，如果某項功能遺漏了特定版本，您可能必須先等幾年的時間，再將其新增至某個版本的標準。 然後，您會想要更長的時間，讓新版本的 .NET Standard 更加廣泛地受到支援。

  **.Net 5 的解決方案：** 當功能完成時，它已經可用於每個 .NET 5 應用程式和程式庫，因為程式碼基底是共用的。 而且因為 API 規格和其執行方式沒有任何差異，所以您可以利用新功能，比 .NET Standard 更快。

- 複雜版本控制

  將 API 規格與其實作為區隔，會導致 API 規格版本與實版之間的複雜對應。 這種複雜性在本文稍早所示的表格中很明顯，以及如何解讀的指示。

  **.Net 5 的解決方案：** .NET 5.x API 規格與其執行之間沒有區隔。 結果是簡化的 TFM 配置。 所有工作負載都有一個 TFM 前置詞： `net5.0` 用於程式庫、主控台應用程式和 web 應用程式。 唯一的變化是一個 [尾碼，可指定特定平臺的平臺特定 api](frameworks.md#net-5-os-specific-tfms) （例如） `net5.0-windows` 。 由於此 TFM 命名慣例，您可以輕鬆地分辨指定的應用程式是否可以使用指定的程式庫。 不需要任何版本號碼對應的資料表，例如 .NET Standard 的資料表。

- 平臺-執行時間不支援的例外狀況

  .NET Standard 會公開平臺特定的 Api。 您的程式碼可能會在沒有錯誤的情況下進行編譯，並且看似可移植到任何平臺，即使它無法移植。 當它在沒有指定 API 之執行的平臺上執行時，您會收到執行階段錯誤。

  **.Net 5 的解決方案：** .NET 5 SDK 包含預設啟用的程式碼分析器。 平臺相容性分析器會偵測到您想要在其上執行的平臺上不支援的 Api 的意外使用。 如需詳細資訊，請參閱 [平臺相容性分析器](analyzers/platform-compat-analyzer.md)。

### <a name="net-standard-not-deprecated"></a>.NET Standard 未淘汰

可供多個 .NET 執行使用的程式庫仍需要 .NET Standard。 建議您在下列案例中以 .NET Standard 為目標：

* 用 `netstandard2.0` 來在 .NET Framework 與其他所有 .net 的執行之間共用程式碼。
* 用 `netstandard2.1` 來在 Mono、Xamarin 和 .Net Core 3.x 之間共用程式碼。

## <a name="see-also"></a>請參閱

- [.NET Standard 版本 (來源) ](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [.NET Standard 版本 (互動式 UI) ](https://dotnet.microsoft.com/platform/dotnet-standard#versions)
- [建立 .NET Standard 程式庫](../core/tutorials/library-with-visual-studio.md)
- [跨平台目標設定](./library-guidance/cross-platform-targeting.md)
