---
title: 'C # 9.0 的新功能-c # 指南'
description: '深入瞭解 c # 9.0 中可用的新功能。'
ms.date: 09/04/2020
ms.openlocfilehash: a863e544c0fcc8682994f49a464acccafc5ce92f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495821"
---
# <a name="whats-new-in-c-90"></a>C # 9.0 的新功能

C # 9.0 將下列功能和增強功能新增至 c # 語言：

- 記錄
- 僅供初始化的 Setter
- 最上層陳述式
- 模式比對增強功能
- 原生大小的整數
- 函式指標
- 隱藏發出 localsinit 旗標
- 目標型別新運算式
- 靜態匿名函數
- 目標型別條件運算式
- Covariant 傳回類型
- Lambda 捨棄參數
- 區域函式上的屬性
- 模組初始設定式
- 部分方法的新功能

**.Net 5**支援 c # 9.0。 如需詳細資訊，請參閱 [c # 語言版本控制](../language-reference/configure-language-version.md)。

## <a name="record-types"></a>記錄類型

C # 9.0 引進了 ***記錄類型***，這是一種參考型別，可提供合成方法來提供相等的值語義。 依預設，記錄是不可變的。

記錄類型可讓您輕鬆地在 .NET 中建立不可變的參考型別。 在過去，.NET 型別大多分類為參考型別 (包括類別和匿名型別) 和實值型別 (包括結構和元組) 。 雖然建議使用可變的實數值型別，但可變動的實值型別通常不會造成錯誤。 實值型別變數會保存值，以便在將實數值型別傳遞給方法時，對原始資料的複本進行變更。

不可變的參考型別也有許多優點。 這些優點在具有共用資料的並行程式中更加明顯。 可惜的是，c # 強制您撰寫相當多的額外程式碼來建立不可變的參考型別。 記錄提供使用值語義相等的不可變參考型別的類型宣告。 相等和雜湊碼的合成方法會將兩筆記錄視為相等，如果其屬性相等。 請考慮下列定義：

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="RecordDefinition":::

記錄定義 `Person` 會建立包含兩個 readonly 屬性的型別： `FirstName` 和 `LastName` 。 `Person`類型是參考型別。 如果您看過 IL，它就是一種類別。 這是不可變的，因為在建立之後，就無法修改任何屬性。 當您定義記錄類型時，編譯器會為您會合成數個其他方法：

- 以值為基礎之相等比較的方法
- 覆寫 <xref:System.Object.GetHashCode>
- 複製和複製成員
- `PrintMembers` 和 <xref:System.Object.ToString>
- `Deconstruct` 方法

記錄支援繼承。 您可以宣告衍生自的新記錄 `Person` ，如下所示：

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="InheritedRecord":::

您也可以密封記錄以防止進一步的衍生：

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="SealedRecord":::

編譯器會會合成上述方法的不同版本。 如果記錄類型是密封的，且直接基類為 object，則方法簽章相依于。 記錄應該具有下列功能：

- 相等是以值為基礎，並且包含類型相符的檢查。 例如， `Student` `Person` 即使兩筆記錄共用相同的名稱，a 也不能相等。
- 記錄會為您產生一致的字串表示。
- 記錄支援複製結構。 正確的複製結構必須包含繼承階層，以及開發人員新增的屬性。
- 您可以修改記錄以進行複製。 這些複製和修改作業支援非破壞性的變化。
- 所有記錄都支援解構。

除了熟悉的多載 `Equals` 、 `operator ==` 和以外 `operator !=` ，編譯器也會會合成新的 `EqualityContract` 屬性。 屬性 `Type` 會傳回符合記錄類型的物件。 如果基底類型為 `object` ，則屬性為 `virtual` 。 如果基底類型是另一種記錄類型，則此屬性為 `override` 。 如果記錄類型為 `sealed` ，則屬性為 `sealed` 。 合成會 `GetHashCode` 使用 `GetHashCode` 基底類型中宣告的所有屬性和欄位，以及記錄類型。 這些合成方法會在整個繼承階層架構中強制執行以值為基礎的相等。 這表示 `Student` 永遠不會將永遠視為 `Person` 相同名稱的。 這兩筆記錄的類型必須相符，以及在記錄類型中共用的所有屬性都相等。

記錄也有合成的函式，以及用來建立複本的「複製」方法。 合成的函式有一種記錄類型的引數。 它會針對記錄的所有屬性產生具有相同值的新記錄。 如果記錄是密封的，則這個函式是私用的，否則會受到保護。 合成的 "clone" 方法支援記錄階層的複製結構。 「Clone」一詞是以引號括住，因為實際名稱是編譯器產生的。 您無法 `Clone` 在記錄類型中建立名為的方法。 合成的 "clone" 方法會傳回使用虛擬分派複製的記錄類型。 編譯器會根據上的存取修飾詞，為 "clone" 方法新增不同的修飾詞 `record` ：

- 如果記錄類型為，則「 `abstract` 複製」方法也是 `abstract` 。 如果基底類型不 `object` 是，則方法也是 `override` 。
- 針對不是 `abstract` 基底類型為下列情況的記錄類型 `object` ：
  - 如果記錄是，則不會 `sealed` 將其他修飾詞新增至「複製」方法 (這表示不會 `virtual`) 。
  - 如果記錄不是 `sealed` ，則「複製」方法是 `virtual` 。
- 針對 `abstract` 不是基底類型不是的記錄類型 `object` ：
  - 如果記錄為，則「 `sealed` 複製」方法也是 `sealed` 。
  - 如果記錄不是 `sealed` ，則「複製」方法是 `override` 。

所有這些規則的結果都是一致地跨任何記錄類型階層來實行相等的結果。 如果兩筆記錄的屬性相等且其類型相同，就會彼此相等，如下列範例所示：

:::code language="csharp" source="snippets/whats-new-csharp9/RecordsExamples.cs" ID="RecordsEquality":::

編譯器會會合成兩種支援列印輸出的方法：覆 <xref:System.Object.ToString> 寫、和 `PrintMembers` 。 `PrintMembers`會接受 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 做為其引數。 它會針對記錄類型中的所有屬性，附加以逗號分隔的屬性名稱和值清單。 `PrintMembers` 針對衍生自其他記錄的任何記錄，呼叫基底實作為。 覆 <xref:System.Object.ToString> 寫會傳回所產生的字串 `PrintMembers` ，並以和括住 `{` `}` 。 例如，的方法會傳回， <xref:System.Object.ToString> `Student` `string` 如下列程式碼所示：

```csharp
"Student { LastName = Wagner, FirstName = Bill, Level = 11 }"
```

到目前為止所顯示的範例會使用傳統語法來宣告屬性。 有更精確的形式稱為「 ***位置記錄***」。  以下是稍早定義為位置記錄的三種記錄類型：

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="PositionalRecords":::

這些宣告會建立與舊版 (的相同功能，但有幾個額外的功能) 在下一節中討論。 這些宣告的結尾都是分號而不是方括弧，因為這些記錄不會加入額外的方法。 您可以新增內文，也可以包含任何其他方法：

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="RecordsWithMethods":::

編譯器會產生 `Deconstruct` 位置記錄的方法。 `Deconstruct`方法的參數與記錄類型中所有公用屬性的名稱相符。 `Deconstruct`方法可以用來將記錄解構到其元件屬性中：

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="DeconstructRecord":::

最後，記錄支援 ***與-運算式***。 ***With-expression***會指示編譯器建立記錄的複本 *，但已修改指定的屬性*：

:::code language="csharp" source="snippets/whats-new-csharp9/PositionalRecords.cs" ID="Wither":::

上述程式程式碼會建立新的 `Person` 記錄 `LastName` ，其中屬性是的複本 `person` ，而 `FirstName` 是 "Paul"。 您可以使用運算式來設定任何數目的屬性。  任何合成成員（「複製」方法除外）都可以由您撰寫。 如果記錄類型的方法符合任何合成方法的簽章，則編譯器不會合成該方法。 先前的 `Dog` 記錄範例包含手動編碼的 <xref:System.String.ToString> 方法做為範例。

## <a name="init-only-setters"></a>僅供初始化的 Setter

***Init only setter*** 提供一致的語法來初始化物件的成員。 屬性初始化運算式可讓它清除哪個值正在設定哪個屬性。 缺點是這些屬性必須是可設定的。 從 c # 9.0 開始，您可以建立存取子， `init` 而不是 `set` 屬性和索引子的存取子。 呼叫端可以使用屬性初始化運算式語法來設定建立運算式中的這些值，但在結構完成之後，這些屬性是唯讀的。 僅限 Init 的 setter 提供視窗來變更狀態。 當建築階段結束時，該視窗就會關閉。 在所有初始化後（包括屬性初始化運算式和 with-expression），都能有效地結束結構階段。

上述的位置記錄範例示範如何使用初始化 setter，以使用 with 運算式來設定屬性。 您可以在任何您撰寫的型別中宣告 init only setter。 例如，下列結構會定義氣象觀察結構：

:::code language="csharp" source="snippets/whats-new-csharp9/WeatherObservation.cs" ID="DeclareWeatherObservation":::

呼叫端可以使用屬性初始化運算式語法來設定值，同時仍然保留永久性：

:::code language="csharp" source="snippets/whats-new-csharp9/WeatherObservation.cs" ID="UseWeatherObservation":::

但是，在初始化之後變更觀察是一項錯誤，方法是在初始化之外指派給僅限初始化的屬性：

```csharp
// Error! CS8852.
now.TempetureInCelsius = 18;
```

僅初始化 setter 有助於從衍生類別設定基類屬性。 它們也可以透過基類中的協助程式來設定衍生屬性。 位置記錄會使用僅初始化 setter 來宣告屬性。 這些 setter 會在 with 運算式中使用。 您可以針對任何或定義，宣告 init only 的 setter `class` `struct` 。

## <a name="top-level-statements"></a>最上層陳述式

***最上層的語句*** 會從許多應用程式中移除不必要的繁瑣。 請考慮標準 "Hello World！" 程式：

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

只有一行程式碼會執行任何作業。 使用最上層的語句，您可以使用 `using` 語句和執行工作的單行來取代所有重複使用的語句：

:::code language="csharp" source="snippets/whats-new-csharp9/Program.cs" ID="TopLevelStatements":::

如果您需要單行程式，您可以移除指示詞， `using` 並使用完整類型名稱：

```csharp
System.Console.WriteLine("Hello World!");
```

您的應用程式中只有一個檔案可以使用最上層的語句。 如果編譯器在多個原始程式檔中尋找最上層的語句，則會產生錯誤。 如果您將最上層語句與宣告的程式進入點方法（通常是方法）結合，也會發生錯誤 `Main` 。 您可以認為一個檔案包含的語句通常會在 `Main` 類別的方法中 `Program` 。  

這項功能最常見的用途之一就是建立教學教材。 初學者 c # 開發人員可以撰寫標準 "Hello World！" 在一或兩行程式碼中。 不需要額外的額外儀式。 不過，經驗豐富的開發人員也會發現這項功能有許多用途。 最上層的語句可啟用類似腳本的實驗體驗，類似于 Jupyter 筆記本所提供的功能。 最上層的語句非常適合小型主控台程式和公用程式。 Azure 函式是最適合最上層語句的使用案例。

最重要的是，最重要的語句不會限制應用程式的範圍或複雜度。 這些語句可以存取或使用任何 .NET 類別。 它們也不會限制您使用命令列引數或傳回值。 最上層語句可以存取名為 args 的字串陣列。 如果最上層的語句傳回整數值，該值就會變成合成方法的整數傳回碼 `Main` 。 最上層語句可能包含非同步運算式。 在此情況下，合成的進入點會傳回 `Task` 或 `Task<int>` 。

## <a name="pattern-matching-enhancements"></a>模式比對增強功能

C # 9 包含新的模式比對改良功能：

- ***類型模式*** 符合變數是類型
- ***括弧模式*** 會強制執行或強調模式組合的優先順序
- ***組成 `and` 模式*** 需要這兩個模式相符
- ***Disjunctive `or` 模式*** 需要有兩種模式相符
- ***否定 `not` 模式*** 要求模式不相符
- ***關聯式模式*** 要求輸入小於、大於、小於或等於或大於或等於指定的常數。

這些模式會擴充模式的語法。 請考慮下列範例：

:::code language="csharp" source="snippets/whats-new-csharp9/PatternUtilities.cs" ID="IsLetterPattern":::

或者，使用選擇性的括弧讓它清楚的 `and` 優先順序高於 `or` ：

:::code language="csharp" source="snippets/whats-new-csharp9/PatternUtilities.cs" ID="IsLetterOrSeparatorPattern":::

其中一個最常見的用法是 null 檢查的新語法：

```csharp
if (e is not null)
{
    // ...
}
```

這些模式中的任何一種都可以在允許模式的任何內容中使用： `is` 模式運算式、 `switch` 運算式、嵌套模式，以及 `switch` 語句 `case` 標籤的模式。

## <a name="performance-and-interop"></a>效能和互通性

有三項新功能可改善需要高效能的原生 interop 和低層級程式庫的支援：原生大小的整數、函式指標，以及省略 `localsinit` 旗標。

原生大小的整數 `nint` 和 `nuint` 是整數類型。 它們是以基礎類型和來 <xref:System.IntPtr?displayProperty=nameWithType> 表示 <xref:System.UIntPtr?displayProperty=nameWithType> 。 編譯器會以原生 int 的形式呈現這些類型的其他轉換和作業。 原生大小的整數沒有或的常數 `MaxValue` `MinValue` ，但 `nuint.MinValue` 具有 `MinValue` 的是 `0` 。 其他值無法表示為常數，因為它相依于目的電腦上的整數原生大小。 您可以 `nint` 在 [.] 範圍中使用的常數值 `int.MinValue` 。 `int.MaxValue`]. 您可以 `nuint` 在 [.] 範圍中使用的常數值 `uint.MinValue` 。 `uint.MaxValue`]. 編譯器會使用和類型來執行所有一元和二元運算子的常數折迭 <xref:System.Int32?displayProperty=nameWithType> <xref:System.UInt32?displayProperty=nameWithType> 。 如果結果不符合32位，則作業會在執行時間執行，且不會被視為常數。 原生大小的整數可提高使用整數數學的案例中的效能，而且需要盡可能最快的效能。

函式指標提供簡單的語法來存取 IL 操作碼 `ldftn` 和 `calli` 。 您可以使用新的語法來宣告函式指標 `delegate*` 。 `delegate*`類型是指標類型。 `delegate*` `calli` 相對於在方法上使用的委派，叫用型別會使用 `callvirt` `Invoke()` 。 在語法上，叫用相同。 函數指標調用會使用 `managed` 呼叫慣例。 您可以在 `unmanaged` 語法之後加入關鍵字， `delegate*` 以宣告您想要 `unmanaged` 呼叫慣例。 您可以使用宣告上的屬性來指定其他呼叫慣例 `delegate*` 。

最後，您可以加入， <xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute?displayProperty=nameWithType> 以指示編譯器不要發出 `localsinit` 旗標。 此旗標會指示 CLR 將所有區域變數初始化為零。 `localsinit`自1.0 起，旗標已是 c # 的預設行為。 不過，在某些情況下，額外的零初始化可能會有顯著的效能影響。 尤其是在使用時 `stackalloc` 。 在這些情況下，您可以新增 <xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute> 。 您可以將它加入至單一方法或屬性，或加入至 `class` 、 `struct` 、 `interface` 或甚至是模組。 這個屬性不會影響 `abstract` 方法，它會影響針對實作為產生的程式碼。

在某些情況下，這些功能可以改善效能。 在採用之前和之後，請務必謹慎使用它們。 牽涉到原生大小整數的程式碼必須在具有不同整數大小的多個目標平臺上進行測試。 其他功能則需要 unsafe 程式碼。

## <a name="fit-and-finish-features"></a>符合和完成功能

許多其他功能可協助您更有效率地撰寫程式碼。 在 c # 9.0 中，當已建立的物件類型為已知時，您可以在新的運算式中省略該型別。 最常見的用法是在欄位宣告中：

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="WeatherStationField":::

當您需要建立新的物件以做為參數傳遞至方法時，也可以使用目標型別 new。 請考慮 `ForecastFor()` 具有下列簽章的方法：

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="ForecastSignature":::

您可以呼叫它，如下所示：

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="TargetTypeNewArgument":::

這項功能的另一個不錯用途是將它與 init only 屬性結合，以初始化新的物件。 上的括弧 `new` 是選擇性的：

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="InitWeatherStation":::

您可以使用運算式傳回預設的函式所建立的實例 `return new();` 。

類似的功能可改善條件運算式的目標型別解析。 進行這項變更時，這兩個運算式不需要從一個運算式隱含轉換成另一個運算式，但兩者都可能隱含轉換成一般類型。 您可能不會注意到這種變更。 您將會注意到，某些條件運算式先前需要轉換或根本無法編譯。

從 c # 9.0 開始，您可以將 `static` 修飾詞加入至 lambda 運算式或匿名方法。 靜態 lambda 運算式類似于 `static` 區域函數：靜態 lambda 或匿名函式無法捕捉區域變數或實例狀態。 `static`修飾詞可避免意外地捕捉其他變數。

協變數傳回型別提供覆寫函式之傳回類型的彈性。 覆寫的虛擬函式可以傳回衍生自基類方法中宣告之傳回型別的型別。 這有助於記錄，以及支援虛擬複製品或 factory 方法的其他類型。

接下來，您可以使用捨棄作為 lambda 運算式的參數。 這種便利性可讓您避免將引數命名，而編譯器可能會避免使用它。 您可以使用 `_` 做為任何引數。

最後，您現在可以將屬性套用至區域函數。 例如，您可以將可為 null 的屬性批註套用至區域函數。

## <a name="support-for-code-generators"></a>程式碼產生器的支援

有兩個最終功能支援 c # 程式碼產生器。 C # 程式碼產生器是您可以撰寫的元件，類似于 roslyn 分析器或程式碼修正。 差別在於程式碼產生器會分析程式碼，並在編譯過程中撰寫新的原始程式碼檔。 一般的程式碼產生器會搜尋程式碼中的屬性或其他慣例。

程式碼產生器會使用 Roslyn 分析 Api 來讀取屬性或其他程式碼元素。 在該資訊中，它會將新的程式碼加入至編譯中。 來源產生器只能新增程式碼;不允許它們修改編譯中的任何現有程式碼。

針對程式碼產生器新增的兩項功能是 ***部分方法語法***的延伸模組，以及 ***模組初始化運算式***。 首先是部分方法的變更。 在 c # 9.0 之前，部分方法是 `private` 但無法指定存取修飾詞、傳回 `void` ，而且不能有 `out` 參數。 這些限制表示如果未提供任何方法執行，則編譯器會移除對部分方法的所有呼叫。 C # 9.0 會移除這些限制，但需要部分方法宣告才能執行。 程式碼產生器可以提供該執行。 為了避免引進重大變更，編譯器會考慮任何部分方法，而不使用存取修飾詞來遵循舊規則。 如果部分方法包含 `private` 存取修飾詞，則新的規則會管理該部分方法。

程式碼產生器的第二項新功能是 ***模組初始化運算式***。 模組初始化運算式是已 <xref:System.Runtime.CompilerServices.ModuleInitializerAttribute> 附加屬性的方法。 載入元件時，執行時間會呼叫這些方法。 模組初始化運算式方法：

- 必須是靜態
- 必須是無參數
- 必須傳回 void
- 不得為泛型方法
- 不得包含在泛型類別中
- 必須可從包含的模組存取

最後一個專案符號點實際上表示方法及其包含的類別必須為內部或公用。 方法不能是區域函數。
