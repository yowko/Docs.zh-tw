---
title: '使用記錄類型-c # 教學課程'
description: 瞭解如何使用記錄類型、建立記錄的階層，以及選擇要在類別上選擇記錄的時機。
ms.date: 11/12/2020
ms.openlocfilehash: 8a2cb6966ab4f93432723fd6f82618efa86b26aa
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688582"
---
# <a name="create-record-types"></a>建立記錄類型

C # 9 引進了 *記錄*，這是您可以建立的新參考型別，而不是類別或結構。 記錄與類別的不同之處是，記錄類型使用以 *值為基礎的相等*。 如果記錄類型定義相同，記錄類型的兩個變數會相等，而且如果是針對每個欄位，則兩筆記錄中的值都相等。 如果參考的物件是相同的類別類型，而且變數參考相同的物件，則類別型別的兩個變數會相等。 以值為基礎的相等表示您可能會想要在記錄類型中的其他功能。 當您宣告而不是時，編譯器會產生許多這些成員 `record` `class` 。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> - 決定您是否要宣告 `class` 或 `record` 。
> - 宣告記錄類型和位置記錄類型。
> - 以您的方法取代記錄中編譯器產生的方法。

## <a name="prerequisites"></a>先決條件

您必須設定電腦以執行 .NET 5 或更新版本，包括 c # 9.0 或更新版本的編譯器。 從 [Visual Studio 2019 16.8 版](https://visualstudio.microsoft.com/vs) 或 [.net 5.0 SDK](https://dotnet.microsoft.com/download)開始，可以使用 c # 9.0 編譯器。

## <a name="characteristics-of-records"></a>記錄的特性

您可以使用 *record* 關鍵字來宣告型別 `record` ，而不是使用 `class` 或關鍵字來定義記錄 `struct` 。 記錄是參考型別，並遵循以值為基礎的相等語義。 為了強制執行值語義，編譯器會為您的記錄類型產生數個方法：

- 的覆寫 <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> 。
- `Equals`其參數為記錄類型的虛擬方法。
- 的覆寫 <xref:System.Object.GetHashCode?displayProperty=nameWithType> 。
- 和的 `operator ==` 方法 `operator !=` 。
- 執行記錄類型 <xref:System.IEquatable%601?displayProperty=nameWithType> 。

此外，記錄會提供的覆寫 <xref:System.Object.ToString?displayProperty=nameWithType> 。 編譯器會會合成使用來顯示記錄的方法 <xref:System.Object.ToString?displayProperty=nameWithType> 。 當您撰寫本教學課程的程式碼時，將會探索這些成員。 記錄支援 `with` 運算式，以啟用記錄的非破壞性變化。

您也可以使用更簡潔的語法來宣告 *位置記錄* 。 當您宣告位置記錄時，編譯器會會合成更多的方法：

- 主要的函式，其參數符合記錄宣告上的位置參數。
- 主要函式之每個參數的公用初始化屬性。
- `Deconstruct`從記錄中解壓縮屬性的方法。

## <a name="build-temperature-data"></a>建立溫度資料

資料和統計資料是您想要使用記錄的案例中。 在本教學課程中，您將會建立應用程式，以計算不同用途的 *程度* 。 「*程度*」是一種熱度 (的量值，或在一段時間、幾周或幾個月內缺少熱度) 。 學位天的追蹤和預測能源使用量。 更高的日子表示更多的空調，低天則表示更 furnace 的使用量。 學位天有助於管理工廠人口。 隨著季節的變化，與廠成長的程度會產生關聯。 學位天有助於追蹤物種的動物旅程，以符合氣候。

此公式是以指定日期的平均溫度和基準溫度為基礎。 若要在一段時間內計算一段時間，您每天都需要最高和最低溫度。 讓我們從建立新的應用程式開始。 建立新的主控台應用程式。 在名為 "DailyTemperature.cs" 的新檔案中建立新的記錄類型：

:::code language="csharp" source="snippets/record-types/InterimSteps.cs" ID="DailyRecord":::

上述程式碼會定義 *位置記錄*。 您已建立包含兩個屬性的參考型別： `HighTemp` 、和 `LowTemp` 。 這些屬性是 *僅初始化的屬性*，表示可以在函式中設定或使用屬性初始化運算式。 此 `DailyTemperature` 類型也有 *主要* 的函式，其具有兩個符合兩個屬性的參數。 您可以使用主要的函式來初始化 `DailyTemperature` 記錄：

:::code language="csharp" source="snippets/record-types/Program.cs" ID="DeclareData":::

您可以將自己的屬性或方法新增至記錄，包括位置記錄。 您必須計算每日的平均溫度。 您可以將該屬性加入至 `DailyTemperature` 記錄：

:::code language="csharp" source="snippets/record-types/DailyTemperature.cs" ID="TemperatureRecord":::

讓我們確認您可以使用此資料。 將下列程式碼新增至 `Main` 方法：

```csharp
foreach (var item in data)
    Console.WriteLine(item);
```

執行您的應用程式，您會看到類似下列顯示的輸出 (針對空間) 移除數個數據列：

```dotnetcli
DailyTemperature { HighTemp = 57, LowTemp = 30, Mean = 43.5 }
DailyTemperature { HighTemp = 60, LowTemp = 35, Mean = 47.5 }


DailyTemperature { HighTemp = 80, LowTemp = 60, Mean = 70 }
DailyTemperature { HighTemp = 85, LowTemp = 66, Mean = 75.5 }
```

上述程式碼顯示編譯器合成的覆寫輸出 `ToString` 。 如果您偏好使用不同的文字，您可以撰寫自己的版本 `ToString` 。 這可防止編譯器為您合成版本。

## <a name="compute-degree-days"></a>計算度的單位

若要計算的時間點，您可以從基準溫度和指定一天的平均溫度來算起差異。 若要測量一段時間的熱度，您會捨棄平均溫度低於基準的任何天數。 若要在一段時間內測量冷，您會捨棄平均溫度高於基準的任何天數。 例如，美國使用65F 作為加熱和冷卻學位的基礎。 這就是不需要加熱或冷卻的溫度。 如果某一天的平均溫度為70F，那一天會是5冷卻學位和0加熱度。 相反地，如果平均溫度是55F，那一天就是10個加熱度，而0冷卻度的單位。

您可以將這些公式表示為一小部分的記錄類型：抽象度的日型別，以及兩個代表加熱度和冷卻度的具體類型。 這些類型也可以是位置記錄。 它們採用基準溫度和一連串的每日溫度記錄作為主要函式的引數：

:::code language="csharp" source="snippets/record-types/InterimSteps.cs" ID="DegreeDaysRecords":::

抽象 `DegreeDays` 記錄是和記錄的共用基類 `HeatingDegreeDays` `CoolingDegreeDays` 。 衍生記錄上的主要函式宣告會顯示如何管理基底記錄初始化。 您的衍生記錄會宣告基底記錄主要函式中所有參數的參數。 基底記錄會宣告並初始化這些屬性。 衍生的記錄不會隱藏它們，但只會針對其基底記錄中未宣告的參數建立和初始化屬性。 在此範例中，衍生記錄不會加入新的主要函式參數。 將下列程式碼新增至您的方法，以測試您的程式碼 `Main` ：

:::code language="csharp" source="snippets/record-types/Program.cs" ID="HeatingAndCooling":::

您將會得到類似下列顯示的輸出：

```dotnetcli
HeatingDegreeDays { BaseTemperature = 65, TempRecords = record_types.DailyTemperature[], DegreeDays = 85 }
CoolingDegreeDays { BaseTemperature = 65, TempRecords = record_types.DailyTemperature[], DegreeDays = 71.5 }
```

## <a name="define-compiler-synthesized-methods"></a>定義編譯器合成的方法

您的程式碼會在一段時間內計算出正確的加熱和冷卻角度。 但是，這個範例會示範為何您可能想要取代某些記錄的合成方法。 您可以在記錄類型中宣告您自己的任何編譯器合成方法版本（複製方法除外）。 Clone 方法具有編譯器產生的名稱，而且您無法提供不同的執行方式。 這些合成方法包括複製的函式、介面的成員 <xref:System.IEquatable%601?displayProperty=nameWithType> 、相等和不等測試，以及 <xref:System.Object.GetHashCode> 。 基於這個目的，您將會合成 `PrintMembers` 。 您也可以宣告自己的 `ToString` ，但 `PrintMembers` 為繼承案例提供更好的選項。 若要提供您自己的合成方法版本，簽章必須符合合成方法。

`TempRecords`主控台輸出中的元素不實用。 它會顯示類型，但不會顯示任何其他專案。 您可以藉由提供合成方法的執行方式來變更此行為 `PrintMembers` 。 簽章取決於套用至宣告的修飾詞 `record` ：

- 如果記錄類型為 `sealed` ，則簽章為 `private bool PrintMembers(StringBuilder builder);`
- 如果記錄類型不是 `sealed` 衍生自 (也不會宣告 `object` 基底記錄) ，則簽章為 `protected virtual bool PrintMembers(StringBuilder builder);`
- 如果記錄類型不是 `sealed` 衍生自另一筆記錄，則簽章為 `protected override bool PrintMembers(StringBuilder builder);`

這些規則最容易透過瞭解的目的來理解 `PrintMembers` 。 `PrintMembers` 將記錄類型中每個屬性的相關資訊加入至字串。 合約需要基底記錄，以將其成員新增到顯示中，並假設衍生成員將會加入其成員。 每一筆記錄類型 `ToString` 都會會合成類似下列範例的覆寫 `HeatingDegreeDays` ：

```csharp
public override string ToString()
{
    StringBuilder stringBuilder = new StringBuilder();
    stringBuilder.Append("HeatingDegreeDays");
    stringBuilder.Append(" { ");
    if (PrintMembers(stringBuilder))
    {
        stringBuilder.Append(" ");
    }
    stringBuilder.Append("}");
    return stringBuilder.ToString();
}
```

您 `PrintMembers` 在記錄中宣告的方法 `DegreeDays` 不會列印集合的類型：

:::code language="csharp" source="snippets/record-types/DegreeDays.cs" ID="AddPrintMembers":::

簽章會宣告 `virtual protected` 符合編譯器版本的方法。 如果您遇到存取子的錯誤，別擔心，語言會強制執行正確的簽章。 如果您忘記任何合成方法的正確修飾詞，編譯器會發出警告或錯誤，以協助您取得正確的簽章。

## <a name="non-destructive-mutation"></a>非破壞性變化

位置記錄中的合成成員不會修改記錄的狀態。 目標是您可以更輕鬆地建立不可變的記錄。 再次查看和先前的宣告 `HeatingDegreeDays` `CoolingDegreeDays` 。 新增的成員會對記錄的值執行計算，但不會變動狀態。 位置記錄可讓您更輕鬆地建立不可變的參考型別。

建立不可變的參考型別表示您會想要使用非破壞性的變化。 您可以使用[ `with` 運算式](../../language-reference/operators/with-expression.md)，建立與現有記錄實例類似的新記錄實例。 這些運算式是具有可修改複製之其他指派的複製結構。 結果是新的記錄實例，其中每個屬性都已從現有記錄複製並選擇性地修改。 原始記錄不變。

讓我們將一些功能新增至示範運算式的程式 `with` 。 首先，讓我們使用相同的資料來建立新的記錄，以計算成長的程度。 *成長的程度* 通常會使用41F 做為基準，並測量高於基準的溫度。 若要使用相同的資料，您可以建立類似的新記錄 `coolingDegreeDays` ，但使用不同的基本溫度：

:::code language="csharp" source="snippets/record-types/Program.cs" ID="GrowingDegreeDays":::

您可以比較計算的單位數與以較高基準溫度產生的數位。 請記住，記錄是 *參考* 型別，而這些複本是淺層複製。 不會複製資料的陣列，但是這兩筆記錄都會參考相同的資料。 這是另一個案例的優點。 針對不斷成長的程度，追蹤前5天的總計會很有用。 您可以使用運算式來建立具有不同來源資料的新記錄 `with` 。 下列程式碼會建立這些 accumulations 的集合，然後顯示這些值：

:::code language="csharp" source="snippets/record-types/Program.cs" ID="RunningFiveDayTotal":::

您也可以使用 `with` 運算式來建立記錄的副本。 請勿在運算式的大括弧之間指定任何屬性 `with` 。 這表示建立複本，而且不要變更任何屬性：

```csharp
var growingDegreeDaysCopy = growingDegreeDays with { };
```

執行完成的應用程式以查看結果。

## <a name="summary"></a>摘要

本教學課程說明記錄的幾個層面。 記錄可針對基本用途是儲存資料的參考型別，提供簡潔的語法。 針對面向物件類別，基本用途是定義責任。 本教學課程著重于 *位置記錄*，您可以在其中使用精簡的語法來宣告記錄的僅限初始屬性。 編譯器會會合成記錄的數個成員，以複製和比較記錄。 您可以為記錄類型新增所需的任何其他成員。 您可以建立不可變的記錄類型，知道任何編譯器產生的成員都不會變動狀態。 針對位置記錄， `with` 運算式可讓您輕鬆地支援非破壞性的變化。

記錄會新增另一個定義類型的方式。 您可以使用 `class` 定義來建立物件導向階層，以專注于物件的責任和行為。 您可以建立 `struct` 資料結構的類型來儲存資料，而且小到足以有效率地複製。 當您想要以值為基礎的相等和比較、不想複製值，而且想要使用參考變數時，會建立記錄。

您可以藉由閱讀 [建議的記錄類型規格](~/_csharplang/proposals/csharp-9.0/records.md)來學習記錄的完整描述。
