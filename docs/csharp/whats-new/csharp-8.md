---
title: C# 8.0 - C# 指南中的新增功能
description: 大致了解 C# 8.0 中可用的新功能。
ms.date: 04/07/2020
ms.openlocfilehash: fcba0526fbcbe46a02cef167822c219f9db2eb63
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738158"
---
# <a name="whats-new-in-c-80"></a>C# 8.0 的新功能

C# 8.0 向 C# 語言新增了以下功能和增強功能:

- [唯讀成員](#readonly-members)
- [預設介面方法](#default-interface-methods)
- [模式比對增強功能](#more-patterns-in-more-places)：
  - [Switch 運算式](#switch-expressions)
  - [屬性模式](#property-patterns)
  - [Tuple 模式](#tuple-patterns)
  - [位置模式](#positional-patterns)
- [Using 宣告](#using-declarations)
- [靜態區域函式](#static-local-functions)
- [可處置的 ref struct](#disposable-ref-structs)
- [可為 Null 的參考型別](#nullable-reference-types)
- [非同步資料流](#asynchronous-streams)
- [非同步一次性](#asynchronous-disposable)
- [索引和範圍](#indices-and-ranges)
- [空合併配置](#null-coalescing-assignment)
- [非託管建構類型](#unmanaged-constructed-types)
- [巢狀式的 Stackalloc](#stackalloc-in-nested-expressions)
- [增強插值逐字串](#enhancement-of-interpolated-verbatim-strings)

C# 8.0 在 **.NET Core 3.x**和 **.NET 標準 2.1**上受支援。 有關詳細資訊,請參閱[C# 語言版本控制](../language-reference/configure-language-version.md)。

本文的其餘部分會簡短說明這些功能。 提供教學課程及概觀的連結，其中包含深入詳盡的文章。 您可以使用 `dotnet try` 全域工具，在您的環境中探索這些功能：

1. 安裝 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全域工具。
1. 複製 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存放庫。
1. 將目前的目錄設為 *try-samples* 存放庫的 *csharp8* 子目錄。
1. 執行 `dotnet try`。

## <a name="readonly-members"></a>唯讀成員

您可以將`readonly`修改器應用於結構的成員。 它指示成員不修改狀態。 它比套用 `readonly` 修飾詞到 `struct` 宣告更為精細。  假設您有下列可變動結構：

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

與大多數結構一樣,`ToString()`該方法不會修改狀態。 您可以透過新增 `readonly` 修飾詞到 `ToString()` 的宣告來指出此情況：

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

前面的變更將產生編譯器警告,因為`ToString``Distance`存取屬性,該屬性未標`readonly`記為 :

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

當它需要建立防禦性複本時，編譯器會警告您。  屬性`Distance`不會更改狀態,因此可以通過`readonly`將 修改器添加到聲明來修復此警告:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

請注意,`readonly`在唯讀屬性上需要修改器。 編譯器不假定`get`訪問器不修改狀態,但您必須顯示式聲明`readonly`。 自動實現的屬性是一個例外;編譯器將所有自動實現的`readonly`getter 視為 ,因此此`readonly`處無需將 修飾`X``Y`符添加到 和 屬性。

編譯器強制實施`readonly`成員不修改狀態的規則。 除非刪除變更器,`readonly`否則以下方法不會編譯:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

此功能可讓您指定您的設計意圖，以便編譯器可以強制套用，並根據該意圖進行最佳化。

有關詳細資訊,請參閱[結構類型](../language-reference/builtin-types/struct.md)文章的[`readonly`實例成員](../language-reference/builtin-types/struct.md#readonly-instance-members)部分。

## <a name="default-interface-methods"></a>預設介面方法

您現在可以新增成員到介面並提供那些成員的實作。 此語言功能可讓 API 作者在較新的版本中新增方法到介面中，而不會因為該介面的現有實作造成原始程式碼或二進位檔案相容性受影響。 現有實作會「繼承」** 預設實作。 此功能也會讓 C# 與以 Android 或 Swift 為目標的 API 相互操作，這些 API 支援類似的功能。 默認介面方法還啟用類似於"traits"語言功能的方案。

默認介面方法會影響許多方案和語言元素。 我們的第一個教學課程涵蓋[使用預設實作更新介面](../tutorials/default-interface-methods-versions.md)。 其他教學課程與參考更新即將在正式發行時推出。

## <a name="more-patterns-in-more-places"></a>在更多位置使用更多的模式

**模式比對**讓您能夠使用提供相關但不同種類資料間圖形相依功能的工具。 C# 7.0[`is`](../language-reference/keywords/is.md)使用 運算式和 語句引入了類型[`switch`](../language-reference/keywords/switch.md)模式和常量 模式的語法。 這些功能代表達成支援程式設計範例 (資料及功能分開) 的暫訂步驟。 隨著業界趨勢轉向微服務及其他雲端式架構，也產生其他語言工具的需求。

C# 8.0 可展開此詞彙，讓您能夠在程式碼中的更多位置，使用更多的模式運算式。 當您的資料與功能分開時，請考慮使用這些功能。 當您的演算法取決於物件執行階段類型外的事實時，請考慮使用模式比對。 這些技術提供表達設計的另一種方式。

除了在新位置的新模式之外，C# 8.0 還新增了**遞迴模式**。 任何模式運算式的結果皆是運算式。 遞迴模式僅為套用到其他模式運算式輸出的模式運算式。

### <a name="switch-expressions"></a>switch 運算式

通常,語句[`switch`](../language-reference/keywords/switch.md)在其`case`每個塊中生成值。 **Switch 運算式**讓您能夠使用更精簡的運算式語法。 重複的 `case` 及 `break` 關鍵字和大括號都減少了。  例如，請考慮以下列出彩虹色彩的列舉：

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

如果您的應用程式定義了由 `R`、`G` 和 `B` 元件所建構的 `RGBColor` 型別，則可以使用包含 switch 運算式的下列方法，將 `Rainbow` 值轉換為其 RGB 值：

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

幾項語法改進如下：

- 變數挪到了 `switch` 關鍵字前。 不同的順序讓您可輕鬆區分出 switch 運算式及 switch 陳述式。
- `case` 及 `:` 元素取代為 `=>`。 這更加精簡而且符合直覺。
- `default` 案例取代為 `_` 捨棄。
- 主體為運算式，而非陳述式。

對比該語法與使用傳統 `switch` 陳述式的對等程式碼：

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a>屬性模式

**屬性模式**使您得以比對所檢查物件的屬性。 試想必須根據購買者地址計算營業稅的電子商務網站。 這種計算不是`Address`類的核心責任。 這項計算會隨著時間變更，而且可能比地址格式的變更更加頻繁。 營業稅額取決於地址的 `State` 屬性。 下列方法會使用屬性模式，從地址及價格計算營業稅：

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

模式比對會建立簡潔的語法以表示此演算法。

### <a name="tuple-patterns"></a>Tuple 模式

某些演算法需仰賴數個輸入。 **Tuple 模式**可讓您根據以 [tuple](../tuples.md) 形式表示的多個值進行切換。  下列範例示範「剪刀、石頭、布」** 遊戲的 switch 運算式：

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

訊息會指出優勝者。 捨棄案例代表平手的三個組合，或其他文字輸入。

### <a name="positional-patterns"></a>位置模式

某些類型會包含 `Deconstruct` 方法，其能將自己的屬性解構成離散變數。 可存取 `Deconstruct` 方法時，您可以使用**位置模式**來檢查物件的屬性，然後將那些屬性用於某個模式。  請考慮下列 `Point` 類別，其包含 `Deconstruct` 方法來針對 `X` 和 `Y` 建立離散變數：

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

此外，請考慮下列代表象限各種不同位置的列舉：

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

下列方法會使用**位置模式**擷取 `x` 及 `y` 的值。 接著，它使用 `when` 子句判斷點的 `Quadrant`：

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

當 `x` 或 `y` 為 0 (非兩者) 時，上述 switch 中的捨棄模式就會符合。 switch 運算式必須產生值或者擲回例外狀況。 若沒有任何案例符合，則 switch 運算式會擲回例外狀況。 如果未涵蓋交換機表達式中的所有可能情況,編譯器將為您生成警告。

您可以在此[模式比對進階教學課程](../tutorials/pattern-matching.md)中探索模式比對技巧。

## <a name="using-declarations"></a>using 宣告

**using 宣告**為以 `using` 關鍵字開頭的變數宣告。 其會告知編譯器，應在括住的範圍結尾處置所宣告的變數。 例如，試想下列寫入文字檔的程式碼：

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    // Notice how we declare skippedLines after the using statement.
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

在上述範例中，到達方法的右大括號時，就會處置檔案。 這是宣告 `file` 之範圍的結尾。 上述程式碼相當於使用傳統 [using 陳述式](../language-reference/keywords/using-statement.md)的下列程式碼：

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    // We must declare the variable outside of the using block
    // so that it is in scope to be returned.
    int skippedLines = 0;
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
    } // file is disposed here
    return skippedLines;
}
```

在上述範例中，到達與 `using` 陳述式相關的結尾右大括號時，就會處置檔案。

在這兩個案例中，編譯器皆會產生對 `Dispose()` 的呼叫。 如果語句中的表示式不是一次性的,`using`編譯器將生成錯誤。

## <a name="static-local-functions"></a>靜態區域函式

您現可將 `static` 修飾詞新增至區域函式，以確保區域函式不會從括住的範圍擷取 (參考) 任何變數。 這樣會產生 `CS8421`「靜態區域函式不可包含對 \<變數> 的參考」。

請考慮下列程式碼： 區域函式 `LocalFunction` 會存取在所括住範圍 (方法 `M`) 中宣告的變數 `y`。 因此，無法使用 `static` 修飾詞宣告 `LocalFunction`：

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

下列程式碼包含靜態區域函式。 因為其不會存取所括住範圍中的任何變數，所以可以為靜態：

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>可處置的 ref struct

使用`struct``ref`修飾符聲明的無法實現任何介面,因此無法<xref:System.IDisposable>實現 。 因此，若要讓 `ref struct` 可處置，其必須具有可存取的 `void Dispose()` 方法。 此功能也適用於`readonly ref struct`聲明。

## <a name="nullable-reference-types"></a>可為 Null 的參考型別

在可為 Null 的註解內容中，參考型別的任何變數皆視為**不可為 Null 的參考型別**。 若您要表示變數可能為 Null，則必須使用 `?` 來附加類型名稱，以將變數宣告為**可為 Null 的參考型別**。

對於不可為 Null 的參考型別，編譯器會使用流程分析來確保將區域變數在宣告時，初始化為非 Null 的值。 必須在建構期間將欄位初始化。 如果變數不是通過調用任何可用的構造函數或初始化器設置,編譯器將生成警告。 此外，也不能對不可為 Null 的參考型別指派可為 Null 的值。

系統不會檢查可為 Null 的參考型別，來確保其不會指派或初始化為 Null。 不過，編譯器會在將變數存取或指派至不可為 Null 的參考型別之前，使用流程分析來確保已對可為 Null 參考型別的所有變數檢查可 Null 性。

您可在[可為 Null 的參考型別](../nullable-references.md)概觀中深入了解功能。 在此[可為 Null 的參考型別教學課程](../tutorials/nullable-reference-types.md)中，親自在新的應用程式內試用。 在[移轉應用程式以使用可為 Null 的參考型別教學課程](../tutorials/upgrade-to-nullable-references.md)中，了解移轉現有程式碼基底的步驟，進而利用可為 Null 的參考型別。

## <a name="asynchronous-streams"></a>非同步資料流

自 C# 8.0 起，您可非同步地建立及取用資料流。 傳回非同步資料流的方法具有三個屬性：

1. 使用 `async` 修飾詞來宣告。
1. 其會傳回 <xref:System.Collections.Generic.IAsyncEnumerable%601>。
1. 方法會包含 `yield return` 陳述式以傳回非同步資料流中的後續元素。

當您列舉資料流的元素時，必須在 `foreach` 關鍵字前新增 `await` 關鍵字，才可取用非同步資料流。 需要方法才可新增 `await` 關鍵字，而且該方法列舉要使用 `async` 修飾詞宣告的非同步資料流，並傳回 `async` 方法允許的類型。 通常這代表傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。 也可以是 <xref:System.Threading.Tasks.ValueTask> 或 <xref:System.Threading.Tasks.ValueTask%601>。 方法可同時取用及產生非同步資料流，這代表其會傳回 <xref:System.Collections.Generic.IAsyncEnumerable%601>。 下列程式碼會產生 0 到 19 的序列，產生每個號碼需等待 100 毫秒的間隔：

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

您應使用 `await foreach` 陳述式列舉序列：

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

您可在我們有關[建立及取用非同步資料流](../tutorials/generate-consume-asynchronous-stream.md)的教學課程中，親自試用非同步資料流。 默認情況元素在捕獲的上下文中處理。 如果要禁用上下文捕獲,請使用<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType>擴展方法。 有關同步上下文和捕獲當前上下文的詳細資訊,請參閱有關[使用基於任務的非同步模式](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的文章。

## <a name="asynchronous-disposable"></a>非同步一次性

從 C# 8.0 開始,該語言支援<xref:System.IAsyncDisposable?displayProperty=nameWithType>實現介面的 非同步一次性類型。 `using`表示式的操作數可以實現<xref:System.IDisposable><xref:System.IAsyncDisposable>或 。 在`IAsyncDisposable`中,編譯器將代碼生成`await`到<xref:System.Threading.Tasks.Task><xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType>從返回的代碼。 有關詳細資訊,請參閱[`using`語句](../language-reference/keywords/using-statement.md)。

## <a name="indices-and-ranges"></a>索引和範圍

索引和範圍提供了簡潔的語法,用於按順序訪問單個元素或範圍。

此語言支援相依於兩種新類型和兩個新運算符號:

- <xref:System.Index?displayProperty=nameWithType> 代表序列的索引。
- 來自結束運算符`^`的索引 ,它指定索引相對於序列的末尾。
- <xref:System.Range?displayProperty=nameWithType> 代表序列的子範圍。
- 範圍運算子`..`, 指定範圍的開始與結束作為其操作數。

讓我們從索引的規則開始。 假設有一個陣列 `sequence`。 `0` 索引與 `sequence[0]` 相同。 `^0` 索引與 `sequence[sequence.Length]` 相同。 請注意，`sequence[^0]` 會擲回例外狀況，就樣 `sequence[sequence.Length]` 會這樣做一樣。 針對任何數字 `n`，索引 `^n` 與 `sequence.Length - n` 相同。

指定範圍「開頭」** 與「結尾」** 的範圍。 範圍的開頭是包羅萬象的,但範圍的結束是獨佔的,這意味著*起始項*包含在範圍內,但範圍中不包括*結束*。 範圍 `[0..^0]` 代整個範圍，就像 `[0..sequence.Length]` 代表整個範圍一樣。

讓我們來看以下幾個範例。 試想下列使用其索引從開頭或從結尾標註的陣列：

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

您可使用 `^1` 索引擷取最後一個字組：

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

下列程式碼會建立具有 "quick"、"brown" 和 "fox" 字組的子範圍。 其會包含 `words[1]` 到 `words[3]`。 項目 `words[4]` 不在範圍內。

```csharp
var quickBrownFox = words[1..4];
```

下列程式碼會建立具有 "lazy" 和 "dog" 的子範圍。 其包含 `words[^2]` 及 `words[^1]`。 不包括最終索引`words[^0]`:

```csharp
var lazyDog = words[^2..^0];
```

下列範例會建立不限定開始、結束或兩者的範圍：

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

您也可將範圍宣告為變數：

```csharp
Range phrase = 1..4;
```

接著範圍可用於 `[` 及 `]` 字元中：

```csharp
var text = words[phrase];
```

不僅陣組支援索引和範圍。 您可以使用索引與範圍與[字串](../language-reference/builtin-types/reference-types.md#the-string-type),<xref:System.Span%601>或<xref:System.ReadOnlySpan%601>。 有關詳細資訊,請參閱[索引和範圍的類型支援](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges)。

您可以在[索引及範圍](../tutorials/ranges-indexes.md)上的教學課程中探索更多關於索引及範圍的資訊。

## <a name="null-coalescing-assignment"></a>空合併配置

C# 8.0 引入了空聚集合賦值運算`??=`子 。 僅當左側操作數`??=`計算`null`到 時,才能使用運算符將其右側操作數的值分配給其左側操作數。

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

有關詳細資訊,請參閱[?和??• 運算符](../language-reference/operators/null-coalescing-operator.md)文章。

## <a name="unmanaged-constructed-types"></a>非託管建構類型

在 C# 7.3 與更早版本中,建構類型(至少包含一個類型參數的類型)不能為[非託管類型](../language-reference/builtin-types/unmanaged-types.md)。 從 C# 8.0 開始,如果建構的值類型僅包含非託管類型的欄位,則該值類型將處於非託管類型。

例如,給定泛型`Coords<T>`型態的以下定義:

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

類型`Coords<int>`是 C# 8.0 及更高版本中的非託管類型。 與任何非託管型態一樣,您可以建立指向此類型的變數的指標,或在[堆疊上為此類實體分配記憶體區](../language-reference/operators/stackalloc.md)塊 :

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

有關詳細資訊,請參閱[非託管類型](../language-reference/builtin-types/unmanaged-types.md)。

## <a name="stackalloc-in-nested-expressions"></a>巢狀式的 Stackalloc

從 C# 8.0 開始,如果[stackalloc](../language-reference/operators/stackalloc.md)運算式的結果為<xref:System.Span%601?displayProperty=nameWithType><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>`stackalloc`或 類型,則可以在其他 運算式中使用運算式:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>增強插值逐字串

插值逐`$``@`字字串中的[interpolated](../language-reference/tokens/interpolated.md)和 標記的順序可以是任意:`$@"..."``@$"..."`兩 者都是有效插值逐字字串。 在早期的 C#`$`版本中 ,權杖必須`@`出現在權杖之前。
