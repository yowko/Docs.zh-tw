---
title: 處理 LINQ
description: 本教學課程會教導您如何使用 LINQ 產生序列、撰寫用於 LINQ 查詢的方法，並區分立即和延遲評估。
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: e37c013add02f651875db7b908ae2b49711d996d
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609314"
---
# <a name="working-with-linq"></a>處理 LINQ

## <a name="introduction"></a>簡介

此教學課程會教導您 .NET Core 和 C# 語言中的功能。 您將了解：

- 如何使用 LINQ 產生序列。
- 如何撰寫可輕鬆用於 LINQ 查詢的方法。
- 如何區分立即和延遲評估。

您將建置一個應用程式來學習這些技術，其中將示範任何魔術師都會的基礎技巧：[完美洗牌 (英文)](https://en.wikipedia.org/wiki/Faro_shuffle)。 簡單地說，完美洗牌是將牌組確實分成兩半，然後互相交錯每一張紙牌來重建原始牌堆的技術。

魔術師使用這項技術的原因，是因為在每次洗牌後，每張紙牌都會在已知的位置，其順序會遵循重複性的模式。

基於您的目的，這是以較輕鬆的方式來了解對資料序列的操作。 您將建置的應用程式會建構牌堆，然後執行一連串的洗牌，每次洗牌都會寫出序列。 您也會比較原始的順序與更新過的順序。

本教學課程有多個步驟。 在每個步驟之後，您可以執行應用程式並查看進度。 您也可以在 dotnet/samples GitHub 存放機制中查看[完整範例](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="prerequisites"></a>必要條件

您必須設定電腦以執行 .NET Core。 您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。 您可以在 Windows、Ubuntu Linux、OS X 或是 Docker 容器中執行此應用程式。 您將必須安裝慣用的程式碼編輯器。 以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。 不過，您可以使用您熟悉的任何工具。

## <a name="create-the-application"></a>建立應用程式

第一個步驟是建立新的應用程式。 請開啟命令提示字元，然後為您的應用程式建立新目錄。 使該目錄成為目前的目錄。 在命令提示字元處輸入命令 `dotnet new console`。 這會建立基本 "Hello World" 應用程式的起始檔案。

如果您從未使用過 C#，[此教學課程](console-teleprompter.md)會說明 C# 程式的結構。 您可以閱讀該教學課程，然後再回到這裡以深入了解 LINQ。

## <a name="creating-the-data-set"></a>建立資料集

開始之前，請確定下列程式碼行位於 `dotnet new console` 所產生的`Program.cs` 檔案最上方：

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

如果這三行程式碼 (`using` 陳述式) 不在檔案最上方，我們的程式將不會編譯。

現在已具備您所需的所有參考，請考慮構成一副撲克牌的內容。 通常，一副撲克牌有四種花色，而每種花色有十三個值。 一般來說，您可以考慮立即建立 `Card` 類別，並以手動方式填入 `Card` 物件的集合。 使用 LINQ，您就能使用比平常方式更簡潔的方法來處理一副撲克牌的建立。 您不需建立 `Card` 類別，而是改為建立兩個序列，分別代表花色和順位。 您將建立一對非常簡單的[迭代器方法  ](../iterators.md#enumeration-sources-with-iterator-methods)，其將會產生順位和花色作為字串的 <xref:System.Collections.Generic.IEnumerable%601>：

```csharp
// Program.cs
// The Main() method

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

將這些方法放置於 `Program.cs` 檔案中的 `Main` 方法下方。 這兩個方法都利用 `yield return` 語法，來在執行時產生序列。 編譯器會建置能實作 <xref:System.Collections.Generic.IEnumerable%601>，並會在要求它們時產生字串序列的物件。

現在，使用這些迭代器方法來建立一副牌。 您將在 `Main` 方法中放置 LINQ 查詢。 以下就來看看此程序：

```csharp
// Program.cs
static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    // Display each card that we've generated and placed in startingDeck in the console
    foreach (var card in startingDeck)
    {
        Console.WriteLine(card);
    }
}
```

多個 `from` 子句會產生 <xref:System.Linq.Enumerable.SelectMany%2A>，這會將第一個序列與第二個序列中的每個元素相互結合，來建立單一序列。 其順序對我們來說很重要。 第一個來源序列 (花色) 中的第一個元素，會與第二個序列 (順位) 中的每個元素結合。 這樣會產生第一個花色的十三張紙牌。 該程序會針對第一個序列 (花色) 中的每個元素重複執行。 最終結果是一疊先依花色，並接著依值排序的牌堆。

請務必牢記在心，無論您選擇要在上述使用的查詢語法中撰寫 LINQ，還是改用方法語法，一律可從某種語法形式移至另一種語法形式。 上述以查詢語法撰寫的查詢可利用方法語法撰寫為：

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

編譯器會將以查詢語法撰寫的 LINQ 陳述式轉譯為相等的方法呼叫語法。 因此，不論您的語法選擇為何，這兩個查詢版本都會產生相同的結果。 選擇最適合您情況的語法：例如，如果您所在的小組中有部分成員對於使用方法語法有困難，請嘗試使用查詢語法。

現在，請執行您目前所建置的範例。 它會顯示牌堆中全部 52 張紙牌。 您會發現以偵錯工具執行此範例，對於觀察 `Suits()` 和 `Ranks()` 方法的執行方式非常有用。 您可以清楚地看見每個序列中的每個字串都只會在需要時產生。

![主控台視窗顯示寫出 52 張紙牌的應用程式。](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulating-the-order"></a>操作順序

接著，專注於您將如何在這副牌中洗牌。 所有好好洗牌步驟中的第一個步驟是將這副牌一分為二。 包含於 LINQ API 的<xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 方法可為您提供該功能。 將它們放在 `foreach` 迴圈下方：

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    // 52 cards in a deck, so 52 / 2 = 26
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
}
```

不過，標準程式庫中並未利用任何洗牌方法，所以您將必須自行撰寫。 您將建立的洗牌方法會舉例說明您將與 LINQ 型程式搭配使用的數種技術，以便在步驟中說明此程序的每個部分。

若要針對您與從 LINQ 查詢中取回的 <xref:System.Collections.Generic.IEnumerable%601> 進行互動的方式新增一些功能，您必須撰寫一些稱為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)的特殊種類方法。 簡單地說，擴充方法是具有特殊用途的「靜態方法」  ，其會將新功能新增到已經存在的類型，而不需修改您想要將功能新增到其中的原始類型。

藉由將新的「靜態」  類別檔案新增到名為 `Extensions.cs` 的程式，來為您的擴充方法提供一個新家，然後開始建置第一個擴充方法：

```csharp
// Extensions.cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>(this IEnumerable<T> first, IEnumerable<T> second)
        {
            // Your implementation will go here soon enough
        }
    }
}
```

查看一下方法簽章，特別是參數：

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

您可以方法的第一個引數上看到加入的 `this` 修飾詞。 這表示您會將方法當作第一個引數之型別的成員方法來呼叫。 此方法宣告也遵循標準慣用語，其中輸入和輸出型別為 `IEnumerable<T>`。 該作法可使 LINQ 方法鏈結在一起，以執行更複雜的查詢。

當然，因為您將這副牌分成數堆，所以必須將這幾堆聯結在一起。 在程式碼中，這表示您將同時列舉您透過 <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 取得的序列、 *`interleaving`* 元素，然後建立一個序列：您現在已完成對這副牌的洗牌。 若要撰寫可搭配兩個序列使用的 LINQ 方法，您必須先了解 <xref:System.Collections.Generic.IEnumerable%601> 的運作方式。

<xref:System.Collections.Generic.IEnumerable%601> 介面具有單一方法：<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>。 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 傳回的物件具有可移動到下一個元素的方法，以及可擷取目前序列中元素的屬性。 您將會使用那兩個成員來列舉集合並傳回元素。 此交錯方法將會是迭代器方法，因此您將使用上述的 `yield return` 語法，而不是建置集合並傳回集合。

以下是該方法的實作：

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

現在您已經撰寫了此方法，請回到 `Main` 方法，然後對牌堆洗牌一次：

```csharp
// Program.cs
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

需要洗牌多少次，才能將這副牌還原為其原始的順序？ 若要進行了解，您必須撰寫一個方法來判斷兩個序列是否相等。 在您完成該方法後，您需要將洗牌的程式碼放入迴圈中，然後看看牌堆何時會回到原始順序。

撰寫判斷兩個序列是否相等的方法應該很單純。 它的架構與您先前撰寫的洗牌方法類似。 只是這次不使用 `yield return` 每個元素，而是比較各序列的相符元素。 當整個序列都已列舉後，如果每個元素都相符，則序列便為相同：

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

這裡示範第二個 LINQ 慣用語：終端方法。 它們會將序列 (在此範例中為兩個序列) 當作輸入，並傳回單一純量值。 使用終端方法時，它們永遠都是適用於 LINQ 查詢之方法鏈結中的最終方法，因此有「終端」的名稱。

當您使用它來判斷牌堆何時回到原始順序時，便可以看到其作用。 將洗牌程式碼放到迴圈中，並透過套用 `SequenceEquals()` 方法，來在序列回到原始順序時停止迴圈。 您可以看到它在任何查詢中都一律是最終方法，因為它會傳回單一值而非序列：

```csharp
// Program.cs
static void Main(string[] args)
{
    // Query for building the deck

    // Shuffling using InterleaveSequenceWith<T>();

    var times = 0;
    // We can re-use the shuffle variable from earlier, or you can make a new one
    shuffle = startingDeck;
    do
    {
        shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

        foreach (var card in shuffle)
        {
            Console.WriteLine(card);
        }
        Console.WriteLine();
        times++;

    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

執行您到目前為止所取得的程式碼，並記下這副牌在每次洗牌之後的重新排列方式。 在 8 次洗牌 (反覆執行 do-while 迴圈) 之後，這副牌會回到您從開始 LINQ 查詢之後第一次建立它時它所處的原始設定。

## <a name="optimizations"></a>最佳化

您目前建置的範例會執行「外部洗牌」  ，牌堆頂端和底部的紙牌，在每次執行時會保持不變。 讓我們做個變化：我們將改用「內部洗牌」  ，這會變更全部 52 張牌的位置。 對於內部洗牌而言，您要交錯牌堆，讓下半部的第一張紙牌變為牌堆的第一張紙牌。 這表示上半部的最後一張紙牌會變為底部的排。 這是對單行程式碼的簡單變更。 藉由切換 <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 的位置來更新目前的洗牌查詢。 這將會變更這副牌上下半部的順序：

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

再次執行程式，您將會看到需要反覆運算 52 次，才能使牌堆重新排列回原始順序。 隨著程式持續執行，您也會開始注意到一些效能嚴重降低的情況。

這有幾個原因。 您可以處理導致這個效能降低的其中一個主要原因：無法有效使用[延遲評估  ](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。

簡單來說，延遲評估表示，在需要陳述式的值之前不會執行該陳述式的評估。 LINQ 查詢是以延遲方式評估的陳述式。 序列只會隨著要求元素產生。 通常，這是 LINQ 的主要優點。 不過，在使用如範例中的程式時，這會導致執行時間呈指數成長。

請記住，我們使用了 LINQ 查詢來產生這副原始的牌。 每次洗牌都是透過對之前的牌堆執行三個 LINQ 查詢來產生。 這些都是以延遲方式執行。 這也表示每次要求序列時，它們都會再次執行。 當您達到第 52 次反覆運算時，您會非常多次地重複產生原始牌堆。 讓我們撰寫記錄以示範這個行為。 接著，您將會修正它。

在您的 `Extensions.cs` 檔案中，輸入或複製下列方法。 這個擴充方法會在您的專案目錄內建立稱為 `debug.log` 的新檔案，並記錄目前正在對記錄檔執行哪一個查詢。 此擴充方法可附加到任何查詢，以標示查詢所執行的內容。

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

您會在 `File` 下看到紅色波浪線，表示它不存在。 它不會編譯，原因是編譯器不知道 `File` 是什麼。 若要解決這個問題，請務必將下列這一行程式碼新增至 `Extensions.cs` 的第一行下：

```csharp
using System.IO;
```

這應可解決此問題，讓紅色的錯誤消失。

接下來，使用記錄訊息檢測每個查詢的定義：

```csharp
// Program.cs
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
        // Out shuffle
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        // In shuffle
        shuffle = shuffle.Skip(26).LogQuery("Bottom Half")
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

您可以在此處改善程式碼的效能，以減少您所進行的執行次數。 您可進行的簡單修正是「快取」  建構這副牌的原始 LINQ 查詢結果。 目前，您會在每次 do-while 迴圈經歷反覆執行時一再地執行查詢、重新建構這副牌，而且每次都會對它進行重新洗牌。 若要快取這副牌，您可以利用 LINQ 方法 <xref:System.Linq.Enumerable.ToArray%2A> 和 <xref:System.Linq.Enumerable.ToList%2A>；當您將它們附加至查詢時，它們將執行您已告訴它們的相同動作，但現在它們會根據您選擇呼叫的方法，將結果儲存在陣列或清單中。 將 LINQ 方法 <xref:System.Linq.Enumerable.ToArray%2A> 附加至這兩個查詢，然後再次執行程式：

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

現在，已將外部洗牌減少至 30 個查詢。 搭配內部洗牌再次執行，您將會看到類似的改善：它現在會執行 162 個查詢。

請注意這個範例的**設計**，用意在於凸顯因延遲執行而造成效能問題的使用案例。 儘管查看延遲評估可能會影響程式碼效能的位置很重要，但了解並非所有查詢都應立即執行也很重要。 您在不使用 <xref:System.Linq.Enumerable.ToArray%2A> 的情況下所遇到的效能影響，是因為對於這副牌的每個排列都是從前一個排列建置的。 使用延遲評估表示每個新的牌堆設定都是從原始牌堆建立，甚至會執行建置 `startingDeck` 的程式碼。 這會導致大量的額外工作。

實際上，某些演算法適合使用立即評估來執行，而其他演算法則適合使用延遲評估來執行。 針對每日使用方式，當資料來源為獨立程序 (例如資料庫引擎) 時，通常比較適合選擇延遲評估。 針對資料庫，延遲評估讓更複雜的查詢僅針對資料庫程序執行單次來回行程，並返回您程式碼的剩餘部分。 無論您選擇利用延遲或立即評估，LINQ 都極具彈性，因此，請測量您的程序，並挑選可為您提供最佳效能的評估種類。

## <a name="conclusion"></a>結論

在此專案中，您已涵蓋：
- 使用 LINQ 查詢來將資料彙總到有意義的序列
- 撰寫擴充方法，將自己的自訂功能新增到 LINQ 查詢
- 在程式碼中尋找 LINQ 查詢可能遇到效能問題 (例如降低速度) 的區域
- 有關 LINQ 查詢的延遲和立即評估，以及它們可能對查詢效能產生的影響

除了 LINQ，您還了解到魔術師使用撲克牌的技巧。 魔術師之所以使用完美洗牌，是因為他們可以控制每張牌在牌堆中的動向。 既然您已經知道，就不要為其他人破壞了它！

如需有關 LINQ 的詳細資訊，請參閱：
- [Language-Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md)
  - [LINQ 簡介](../programming-guide/concepts/linq/index.md)
  - [基本 LINQ 查詢作業 (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
  - [使用 LINQ 轉換資料 (C#)](../programming-guide/concepts/linq/data-transformations-with-linq.md)
  - [LINQ 中的查詢語法及方法語法 (C#)](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
  - [支援 LINQ 的 C# 功能](../programming-guide/concepts/linq/features-that-support-linq.md)
