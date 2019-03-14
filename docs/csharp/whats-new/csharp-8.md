---
title: C# 8.0 的新功能 - C# 指南
description: 大致了解 C# 8.0 中可用的新功能。 此文章為適用於預覽 2 的最新資訊。
ms.date: 02/12/2019
ms.openlocfilehash: 3a19cc7ffae706769cf1b1a19fdaff7c7cdc07fc
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674441"
---
# <a name="whats-new-in-c-80"></a>C# 8.0 的新功能

有許多 C# 語言的增強功能，您已經可透過預覽 2 來試用。 在預覽 2 中新增的功能為：

- [模式比對增強功能](#more-patterns-in-more-places)：
  * [Switch 運算式](#switch-expressions)
  * [屬性模式](#property-patterns)
  * [Tuple 模式](#tuple-patterns)
  * [位置模式](#positional-patterns)
- [Using 宣告](#using-declarations)
- [靜態區域函式](#static-local-functions)
- [可處置的 ref struct](#disposable-ref-structs)

下列語言功能首次出現於 C# 8.0 預覽 1 中：

- [可為 Null 的參考類型](#nullable-reference-types)
- [非同步資料流](#asynchronous-streams)
- [索引和範圍](#indices-and-ranges)

> [!NOTE]
> 此文章內容為 C# 8.0 預覽 2 的最新更新。

此文章的其餘部分會簡短說明這些功能。 提供教學課程及概觀的連結，其中包含深入詳盡的文章。

## <a name="more-patterns-in-more-places"></a>在更多位置使用更多的模式

**模式比對**讓您能夠使用提供相關但不同種類資料間圖形相依功能的工具。 C# 7.0 透過使用 [`is`](../language-reference/keywords/is.md) 運算式及 [`switch`](../language-reference/keywords/switch.md) 陳述式，推出了類型模式及常數模式的語法。 這些功能代表達成支援程式設計範例 (資料及功能分開) 的暫訂步驟。 隨著業界趨勢轉向微服務及其他雲端式架構，也產生其他語言工具的需求。

C# 8.0 可展開此詞彙，讓您能夠在程式碼中的更多位置，使用更多的模式運算式。 當您的資料與功能分開時，請考慮使用這些功能。 當您的演算法取決於物件執行階段類型外的事實時，請考慮使用模式比對。 這些技術提供表達設計的另一種方式。

除了在新位置的新模式之外，C# 8.0 還新增了**遞迴模式**。 任何模式運算式的結果皆是運算式。 遞迴模式僅為套用到其他模式運算式輸出的模式運算式。

### <a name="switch-expressions"></a>switch 運算式

通常，[`switch`](../language-reference/keywords/switch.md) 陳述式會在其各個 `case` 區塊中產生值。 **Switch 運算式**讓您能夠使用更精簡的運算式語法。 重複的 `case` 及 `break` 關鍵字和大括號都減少了。  例如，請考慮以下列出彩虹色彩的列舉：

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Blue,
    Indigo,
    Violet
}
```

您可使用以下包含 switch 運算式的方法，將 `Rainbow` 值轉換為其 RGB 值：

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
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
public static RGBColor fromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
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

**屬性模式**使您得以比對所檢查物件的屬性。 試想必須根據購買者地址計算營業稅的電子商務網站。 `Address` 類別的核心功能並非負責進行該計算。 此計算會隨著時間變更，而且可能比地址格式的變更更加頻繁。 營業稅額取決於地址的 `State` 屬性。 下列方法會使用屬性模式，從地址及價格計算營業稅：

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

某些演算法需仰賴數個輸入。 **Tuple 模式**可讓您根據以 [tuple](../tuples.md) 形式表示的多個值進行切換。  下列範例示範「剪刀、石頭、布」遊戲的 switch 運算式：

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

下列方法會使用**位置模式**擷取 `x` 及 `y` 的值。 接著，其使用 `when` 子句判斷點的象限：

```csharp
static string Quadrant(Point p) => p switch
{
    (0, 0) => "origin",
    (var x, var y) when x > 0 && y > 0 => "Quadrant 1",
    (var x, var y) when x < 0 && y > 0 => "Quadrant 2",
    (var x, var y) when x < 0 && y < 0 => "Quadrant 3",
    (var x, var y) when x > 0 && y < 0 => "Quadrant 4",
    (var x, var y) => "on a border",
    _ => "unknown"
};
```

當 `x` 或 `y` (非兩者) 為 0 時，上述 switch 中的捨棄模式就會符合。 switch 運算式必須產生值或者擲回例外狀況。 若沒有任何案例符合，則 switch 運算式會擲回例外狀況。 若您未在 switch 運算式中涵蓋所有可能的案例，則編譯器會對您產生警告。

## <a name="using-declarations"></a>using 宣告

**using 宣告**為以 `using` 關鍵字開頭的變數宣告。 其會告知編譯器，應在括住的範圍結尾處置所宣告的變數。 例如，試想下列寫入文字檔的程式碼：

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

在上述範例中，到達方法的右大括號時，就會處置檔案。 這是宣告 `file` 之範圍的結尾。 上述程式碼與下列使用傳統 [using 陳述式](../language-reference/keywords/using-statement.md)的程式碼相等：


```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

在上述範例中，到達與 `using` 陳述式相關的結尾右大括號時，就會處置檔案。

在這兩個案例中，編譯器皆會產生對 `Dispose()` 的呼叫。 若無法處置 using 陳述式中的運算式，則編譯器會產生錯誤。

## <a name="static-local-functions"></a>靜態區域函式

您現可將 `static` 修飾詞新增至區域函式，以確保區域函式不會從括住的範圍擷取 (參考) 任何變數。 這樣會產生 `CS8421`「靜態區域函式不可包含對 <variable> 的參考。」。 

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

使用 `ref` 修飾詞宣告的 `struct` 不會實作任何介面，故無法實作 <xref:System.IDisposable>。 因此，若要讓 `ref struct` 可處置，其必須具有可存取的 `void Dispose()` 方法。 這也適用於 `readonly ref struct` 宣告。

## <a name="nullable-reference-types"></a>可為 Null 的參考型別

在可為 Null 的註解內容中，參考型別的任何變數皆視為**不可為 Null 的參考型別**。 若您要表示變數可能為 Null，則必須使用 `?` 來附加類型名稱，以將變數宣告為**可為 Null 的參考型別**。

對於不可為 Null 的參考型別，編譯器會使用流程分析來確保將區域變數在宣告時，初始化為非 Null 的值。 必須在建構期間將欄位初始化。 若變數不是由對任何可用建構函式的呼叫，或是初始設定式所設定，則編譯器會產生警告。 此外，也不能對不可為 Null 的參考型別指派可為 Null 的值。

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

您可在我們有關[建立及取用非同步資料流](../tutorials/generate-consume-asynchronous-stream.md)的教學課程中，親自試用非同步資料流。

## <a name="indices-and-ranges"></a>索引和範圍

範圍及索引可提供用來指定陣列中子範圍的簡潔語法，<xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601>。

您可**從結尾**指定索引。 您可使用 `^` 運算子指定**從結尾**。 您已熟悉 `array[2]` 表示「從開頭起算 2 個」元素。 現在，`array[^2]` 表示「從結尾起算 2 個」元素。 索引 `^0` 表示「結尾」，或最後一個元素後接續的索引。

您可使用**範圍運算子**指定**範圍**：`..`。 例如，`0..^0` 會指定陣列的整個範圍：從開頭起算由 0 開始，從結尾起算則不包含 0。 運算元各可以使用「從開頭」或「從結尾」。 此外，也可省略各運算元。 預設是開始索引為 `0`，結尾索引為 `^0`。

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
};
```

各元素的索引會強調「從開頭」及「從結尾」的概念，而且該範圍專屬於範圍的結尾。 整個陣列的「開頭」是第一個元素。 整個陣列的「結尾」則「結束在」最後一個元素。

您可使用 `^1` 索引擷取最後一個字組：

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

下列程式碼會建立具有 "quick"、"brown" 和 "fox" 字組的子範圍。 其會包含 `words[1]` 到 `words[3]`。 元素 `words[4]` 則不在範圍內。

```csharp
var quickBrownFox = words[1..4];
```

下列程式碼會建立具有 "lazy" 和 "dog" 的子範圍。 其包含 `words[^2]` 及 `words[^1]`。 不包含結束索引 `words[^0]`：

```csharp
var lazyDog = words[^2..^0];
```

下列範例會建立不限定開始、結束或兩者的範圍：

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

您也可將範圍宣告為變數：

```csharp
Range phrase = 1..4;
```

接著範圍可用於 `[` 及 `]` 字元中：

```csharp
var text = words[phrase];
```
