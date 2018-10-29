---
title: 處理 LINQ
description: 本教學課程會教導您如何使用 LINQ 產生序列、撰寫用於 LINQ 查詢的方法，並區分立即和延遲評估。
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: dc5f6cc4fd38b32f54a576a3947187cbed4e70e8
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086748"
---
# <a name="working-with-linq"></a>處理 LINQ

## <a name="introduction"></a>簡介

本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。 您將了解：

*   如何使用 LINQ 產生序列
*   如何撰寫可輕鬆用於 LINQ 查詢的方法。
*   如何區分立即和延遲評估。

您將建置一個應用程式來學習這些技術，其中將示範任何魔術師都會的基礎技巧：[完美洗牌 (英文)](https://en.wikipedia.org/wiki/Faro_shuffle)。 簡單地說，完美洗牌是將牌組確實分成兩半，然後互相交錯每一張紙牌來重建原始牌堆的技術。

魔術師使用這項技術的原因，是因為在每次洗牌後，每張紙牌都會在已知的位置，其順序會遵循重複性的模式。 

對我們而言，這是以較輕鬆的方式來了解對資料序列的操作。 您將建置的應用程式會建構牌堆，然後執行一連串的洗牌，每次洗牌都會寫出序列。 您也會比較原始的順序與更新過的順序。

本教學課程有多個步驟。 在每個步驟之後，您可以執行應用程式並查看進度。 您也可以在 dotnet/samples GitHub 存放機制中查看[完整範例](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="prerequisites"></a>必要條件

您必須設定電腦以執行 .NET Core。 您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。 您可以在 Windows、Ubuntu Linux、OS X 或是 Docker 容器中執行此應用程式。 您將必須安裝慣用的程式碼編輯器。 以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。 不過，您可以使用您熟悉的任何工具。

## <a name="create-the-application"></a>建立應用程式

第一個步驟是建立新的應用程式。 請開啟命令提示字元，然後為您的應用程式建立新目錄。 使該目錄成為目前的目錄。 在命令提示字元處輸入命令 `dotnet new console`。 這會建立基本 "Hello World" 應用程式的起始檔案。

如果您從未使用過 C#，[此教學課程](console-teleprompter.md)會說明 C# 程式的結構。 您可以閱讀該教學課程，然後再回到這裡以深入了解 LINQ。 

## <a name="creating-the-data-set"></a>建立資料集

讓我們從建立一疊紙牌開始。 您將會使用具有兩個來源 (一個針對四個花色，另一個針對十三個值) 的 LINQ 查詢來進行。 您會將那些來源結合為 52 張紙牌的牌堆。 `foreach` 迴圈內的 `Console.WriteLine` 陳述式可顯示紙牌。

以下便是該查詢：

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

多個 `from` 子句會產生 `SelectMany`，這會將第一個序列與第二個序列中的每個元素相互結合，來建立單一序列。 其順序對我們來說很重要。 第一個來源序列 (花色) 中的第一個元素，會與第二個序列 (值) 中的每個元素結合。 這樣會產生第一個花色的十三張紙牌。 該程序會針對第一個序列 (花色) 中的每個元素重複執行。 最終結果是一疊先依花色，並接著依值排序的牌堆。

接下來，您需要建置 Suits() 和 Ranks() 方法。 我們從一組非常簡單的「迭代器方法」開始，該方法會產生為可列舉字串的序列：

```csharp
static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

這兩個方法都利用 `yield return` 語法，來在執行時產生序列。 編譯器會建置能實作 `IEnumerable<T>`，並會在要求它們時產生字串序列的物件。

若要讓此檔案進行編譯，您將必須把下列兩行新增到檔案開頭：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
```

現在，請執行您目前所建置的範例。 它會顯示牌堆中全部 52 張紙牌。 您會發現以偵錯工具執行此範例，對於觀察 `Suits()` 和 `Values()` 方法的執行方式非常有用。 您可以清楚地看見每個序列中的每個字串都只會在需要時產生。

![主控台視窗顯示寫出 52 張紙牌的應用程式](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>操作順序

接下來，我們將建置可執行洗牌的公用程式方法。 第一個步驟是將牌堆一分為二。 包含於 LINQ API 的`Take()` 和 `Skip()` 方法可以為我們提供該功能：

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

標準程式庫中不存在洗牌方法，所以您必須自行撰寫。 這個新方法會說明數個您會搭配 LINQ 型程式使用的技術，因此我們將逐步說明方法的每個部分。

方法的簽章會建立「擴充方法」：

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

擴充方法是特殊用途的「靜態方法」。 您可以方法的第一個引數上看到加入的 `this` 修飾詞。 這表示您會將方法當作第一個引數之型別的成員方法來呼叫。

您只能在 `static` 類別中宣告擴充方法，現在讓我們為這項功能建立稱為 `extensions` 的新靜態類別。 在繼續本教學課程的同時，您將會加入更多擴充方法，那些擴充方法都會放置在相同的類別中。

此方法宣告也遵循標準慣用語，其中輸入和輸出型別為 `IEnumerable<T>`。 該作法可使 LINQ 方法鏈結在一起，以執行更複雜的查詢。

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

您將會同時列舉兩個序列，對元素進行交錯，然後建立單一物件。  若要撰寫可搭配兩個序列使用的 LINQ 方法，您必須先了解 `IEnumerable` 的運作方式。

`IEnumerable` 介面具有單一方法：`GetEnumerator()`。 `GetEnumerator()` 傳回的物件具有可移動到下一個元素的方法，以及可擷取目前序列中元素的屬性。 您將會使用那兩個成員來列舉集合並傳回元素。 此交錯方法將會是迭代器方法，因此您將使用上述的 `yield return` 語法，而不是建置集合並傳回集合。 

以下是該方法的實作：

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

現在您已經撰寫了此方法，請回到 `Main` 方法，然後對牌堆洗牌一次：

```csharp
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a>比較

讓我們來看看需要洗牌多少次，才能將牌堆還原為原始的順序。 您必須撰寫判斷兩個序列是否相等的方法。 在您完成該方法後，您需要將洗牌的程式碼放入迴圈中，然後看看牌堆何時會回到原始順序。

撰寫判斷兩個序列是否相等的方法應該很單純。 它的架構與您先前撰寫的洗牌方法類似。 只是這次不使用 yield 傳回每個元素，而是比較各序列的相符元素。 當整個序列都已列舉後，如果每個元素都相符，則序列便為相同：

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

這裡示範第二個 LINQ 慣用語：終端方法。 它們會將序列 (在此範例中為兩個序列) 當作輸入，並傳回單一純量值。 當使用這些方法時，它們一律會是查詢的最終方法。 (也因此才名為終端方法)。 

當您使用它來判斷牌堆何時回到原始順序時，便可以看到其作用。 將洗牌程式碼放到迴圈中，並透過套用 `SequenceEquals()` 方法，來在序列回到原始順序時停止迴圈。 您可以看到它在任何查詢中都一律是最終方法，因為它會傳回單一值而非序列：

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

執行範例，然後查看牌堆於每次洗牌時的重新排列方式，直到它在反覆運算 8 次後回到其原始設定。

## <a name="optimizations"></a>最佳化

您目前建置的範例會執行「外部洗牌」，牌堆頂端和底部的紙牌，在每次執行時會保持不變。 讓我們來做個變化並執行「內部洗牌」，這會變更全部 52 張紙牌的位置。 對於內部洗牌而言，您要交錯牌堆，讓下半部的第一張紙牌變為牌堆的第一張紙牌。 這表示上半部的最後一張紙牌會變為底部的排。 這只需要一行變更。 更新洗牌的呼叫以變更牌堆上下半部的順序：

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

再次執行程式，您將會看到需要反覆運算 52 次，才能使牌堆重新排列回原始順序。 隨著程式持續執行，您也會開始注意到一些效能嚴重降低的情況。

這有幾個原因。 讓我們處理其中一個主要原因：無法有效使用「延遲評估」。

LINQ 查詢會以延遲的方式進行評估。 序列只會隨著要求元素產生。 通常，這是 LINQ 的主要優點。 不過，在使用如範例中的程式時，這會導致執行時間呈指數成長。

原始的牌堆是使用 LINQ 查詢產生。 每次洗牌都是透過對之前的牌堆執行三個 LINQ 查詢來產生。 這些都是以延遲方式執行。 這也表示每次要求序列時，它們都會再次執行。 當您達到第 52 次反覆運算時，您會非常多次地重複產生原始牌堆。 讓我們撰寫記錄以示範這個行為。 接著，您將會修正它。

以下是記錄方法，可以附加到任何查詢以標示查詢所執行的內容。

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

接下來，使用記錄訊息檢測每個查詢的定義：

```csharp
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
            .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
            .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

請注意，您不用在每次存取查詢時進行記錄。 您只需要在建立原始查詢時做出記錄。 程式仍然會花費很長的時間執行，但現在您可以看到原因。 如果您在執行開啟記錄的內部洗牌期間失去耐心，請切換回外部洗牌。 您仍然會看到延遲評估的效果。 在單次執行中，它會執行 2592 次查詢，其中包括所有值和花色的產生。

有一個簡單的方式可以更新此程式，以避免所有那些執行。 LINQ 方法 `ToArray()` 和 `ToList()` 可讓查詢執行，並分別將結果儲存於陣列或清單中。 您可以使用這些方法快取查詢的資料結果，而不需要再次執行來源查詢。  將對 `ToArray()` 的呼叫附加到產生牌堆的查詢，然後再次執行查詢：

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

再次執行，外部洗牌的查詢次數會降至 30 次。 搭配內部洗牌再次執行，您將會看到類似的改善。 (它現在只會執行 162 次查詢)。

請勿因此案例，而認為所有的查詢都應該立即執行。 這個範例的設計，用意在於凸顯因延遲執行而造成效能問題的使用案例。 那是因為每個新的牌堆排列，都是從前一個排列所建立。 使用延遲評估表示每個新的牌堆設定都是從原始牌堆建立，甚至會執行建置 `startingDeck` 的程式碼。 這會導致大量的額外工作。 

實際上，某些演算法會較適合使用立即評估，而其他演算法則較適合使用延遲評估。 (一般而言，資料來源為獨立程序 (例如資料庫引擎) 的狀況，比較適合延遲評估。 在那些情況下，延遲評估可讓更複雜的查詢，僅需針對資料庫程序執行單次反覆查詢)。LINQ 可使用延遲評估和立即評估。 請評量，然後挑選最佳選擇。

## <a name="preparing-for-new-features"></a>準備使用新功能

您針對此範例所撰寫的程式碼，是建立能完成工作之簡單原型的範例。 這是探索問題範圍的絕佳方法，而對許多功能來說，它可能是最好的永久解決方案。 您對紙牌利用了「匿名型別」，而每張紙牌都會以字串表示。

「匿名型別」具有許多生產力優點。 您不需要自行定義代表存放區的類別。 編譯器會為您產生類別。 編譯器產生的類別會利用簡單資料物件的許多最佳做法。 它是「不可變的」，這表示它在建構之後，其屬性皆不可變更。 匿名型別位於組件內部，因此不會被視為該組件公用 API 的一部分。 匿名型別也包含 `ToString()` 方法的覆寫，其中會傳回每個值的格式化字串。

匿名型別也有缺點。 它們不具有可存取的名稱，所以您無法使用它們做為傳回值或引數。 您會注意到上述所有使用這些匿名型別的方法都是泛型方法。 隨著應用程式加入更多功能，`ToString()` 的覆寫可能不是您所要的。 

範例針對花色和每張紙牌的順位也使用字串。 那相對較為模糊。 C# 型別系統可透過對那些值運用 `enum` 型別，來協助我們打造更棒的程式碼。

從花色開始。 這是使用 `enum` 的完美時機：

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

`Suits()` 方法也會變更型別和實作：

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

接下來，請對紙牌的順序執行相同變更：

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

而產生它們的方法為：

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

最後，我們會建立一個型別來代表紙牌，而不依賴匿名型別。 匿名型別很適合用於輕量的區域型別，但在此範例中，紙牌是其中一項主要概念。 它應該要是具象型別。

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

此型別使用「自動實作的唯讀屬性」，該屬性是在建構函式中設定，而且無法修改。 它也會利用[字串內插補點](../language-reference/tokens/interpolated.md)功能，來更輕鬆地對字串輸出進行格式化。

更新產生起始牌堆的查詢，以使用新的型別：

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

編譯並再次執行。 輸出會變的更簡潔，程式碼也會更清楚，而且更容易擴充。

## <a name="conclusion"></a>結論

這個範例為您示範了一些用於 LINQ 的方法，以及如何建立可輕鬆搭配啟用 LINQ 之程式碼來使用的方法。 它也示範延遲評估和立即評估的差異，以及兩者對效能可能會產生的效果。

您學到了一點魔術師的技巧。 魔術師之所以使用完美洗牌，是因為他們可以控制每張牌在牌堆中的動向。 在某些戲法中，魔術師讓觀眾把紙牌放在牌堆最上方，並在洗牌數次之後，仍然能知道該紙牌的位置。 其他的魔術則需要以特定方式設置牌堆。 魔術師會在表演戲法之前會先將牌堆設置好。 然後她會使用外部洗牌將牌堆洗 5 次。 在舞台上，她可以展示看起來像是隨機順序的牌堆，然後將紙牌洗 3 次，這個手法正好會將牌堆洗為她所想要的設置。
