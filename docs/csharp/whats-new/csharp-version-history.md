---
title: C# 的歷史 - C# 指南
description: 最早的語言版本有哪些內容，而在之後有什麼演變？
author: erikdietrich
ms.date: 04/08/2020
ms.openlocfilehash: d9f50a7df7966f81366acb706d719cbdd40a45fa
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989190"
---
# <a name="the-history-of-c"></a>C\# 的歷史

此文章提供了 C# 語言每個主要版本的歷史。 C# 小組將持續創新並加入新功能。 您可以在ˋ GitHub 上的 [dotnet/roslyn 存放庫repository](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) 存放庫中找到詳細語言功能狀態 (包括針對未來版本考慮加入的功能)。

> [!IMPORTANT]
> C# 語言中的部分功能仰賴 C#規格定義為「標準程式庫」** 中的型別和方法。 .NET 平台在許多套件中會提供那些類型與方法。 例外狀況處理便是其中一個例子。 每個 `throw` 陳述式或運算式都會受到檢查，以確保擲回衍生自 <xref:System.Exception> 的物件。 每個 `catch` 也一樣會受到檢查，以確保攔截到衍生自 <xref:System.Exception> 的型別。 每個版本都可能會加入新的需求。 若要在較舊的環境中使用最新的語言功能，可能需要安裝特定的程式庫。 每個特定版本的頁面中會記載這些相依性。 若要知道此相依性的背景，可深入了解[語言和程式庫之間的關係](relationships-between-language-and-library.md)。

C# 建置工具將最新的主要語言版本視為預設語言版本。 主要版本之間可能存在單點發行版本，此節的其他文章對此進行了詳細介紹。 若要使用小數點版本中的最新功能，您需要[設定編譯器語言版本](../language-reference/configure-language-version.md)並選取該版本。 自 C# 7.0 以來已經有三個單點發行版本：

- [C# 7.3](csharp-7-3.md):
  - 從 [Visual Studio 2017 版本 15.7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 和 [.NET Core 2.1 SDK](../../core/whats-new/dotnet-core-2-1.md) 開始，可以使用 C# 7.3。
- [C# 7.2](csharp-7-2.md):
  - C# 7.2 可從[Visual Studio 2017 版本 15.5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)和[.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md)開始。
- [C# 7.1](csharp-7-1.md):
  - 從 [Visual Studio 2017 version 15.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 和 [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md) 開始，可以使用 C# 7.1。

## <a name="c-version-10"></a>C# 1.0 版

當您回過頭來查看時,C# 版本 1.0 與 Visual Studio .NET 2002 一起發佈,看起來非常像 JAva。 在[其聲明的 ECMA 設計目標當中](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)，它試圖成為「簡單、現代化、一般用途的物件導向語言」。  同時，看似 Java 表示它達成了那些早期的設計目標。

但如果您現在回顧 C# 1.0，會覺得有點暈眩。 它缺乏內建的非同步功能和部分圍繞著您視為理所當然的泛型熟練功能。 事實上，它完全缺乏了泛型。  那麼 [LINQ](../linq/index.md) 呢？ 尚無法使用。 那些新增項目需要好幾年才會出現。

C# 1.0 版看起來與現今相比去除了一些功能。 您會發現自己撰寫一些詳細的程式碼。 但您仍然必須從某處開始。 C# 1.0 版是 Windows 平台上可行的 Java 替代方案。

C# 1.0 的主要功能包含：

- [類別](../programming-guide/classes-and-structs/classes.md)
- [結構](../language-reference/builtin-types/struct.md)
- [介面](../programming-guide/interfaces/index.md)
- [事件](../events-overview.md)
- [屬性](../properties.md)
- [委派](../delegates-overview.md)
- [運算式](../programming-guide/statements-expressions-operators/expressions.md)
- [陳述式](../programming-guide/statements-expressions-operators/statements.md)
- [屬性](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C# 1.2 版

C# 版本 1.2 隨 Visual Studio .NET 2003 一起提供。 本版內含對語言的小幅功能改善。 最值得注意的是，自本版開始，當 <xref:System.Collections.IEnumerator> 實作 <xref:System.IDisposable> 時，在 `foreach` 迴圈產生的程式碼會在 <xref:System.Collections.IEnumerator> 呼叫 <xref:System.IDisposable.Dispose%2A>。

## <a name="c-version-20"></a>C# 2.0 版

現在事情開始變得有趣。 讓我們看看 2005 年與 Visual Studio 2005 一起發行的 C# 2.0 中，一些主要功能：

- [泛型](../programming-guide/generics/index.md)
- [部分類型](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [匿名方法](../language-reference/operators/delegate-operator.md)
- [可為 Null 的實值型別](../language-reference/builtin-types/nullable-value-types.md)
- [迭代器](../programming-guide/concepts/iterators.md)
- [共變數和反變數](../programming-guide/concepts/covariance-contravariance/index.md)

其他 C# 2.0 功能將功能新增至現有功能：

- Getter/setter 不同協助工具
- 方法群組轉換 (委派)
- 靜態類別
- 委派推斷

雖然 C# 一開始可能是泛型的物件導向 (OO) 語言，但 C# 2.0 版很急促地改變了。 穩定之後，它們追蹤一些嚴重的開發人員痛苦點。 而且是徹底地追隨。

使用泛型時，型別和方法可以操作任意型別，同時仍然保留型別安全。 例如，<xref:System.Collections.Generic.List%601> 可讓您具有 `List<string>` 或 `List<int>`，並且對那些字串或整數逐一執行型別安全的作業。 使用泛型最好不要建立衍生自 `ArrayList` 的 `ListInt`，或針對每個作業從 `Object` 轉型。

C# 2.0 版帶來了迭代器。 簡單的說，迭代器讓您使用 `foreach` 迴圈檢查 `List` (或其他可列舉型別) 中的所有項目。 將迭代器當成語言的頭等部分能大幅增強語言的可讀性，並讓人們能理解程式碼。

但 C# 仍繼續追趕 Java。 Java 已經發行了包含泛型和迭代器的版本。 但是，很快就會變更，因為語言會持續朝不同方向發展。

## <a name="c-version-30"></a>C# 3.0 版

C# 3.0 版在 2007 年晚期和 Visual Studio 2008 一起出現，不過語言功能的完整陣容實際上是在 .NET Framework 3.5 版時齊備。 這個版本標記了 C# 發展的一項重大變更。 它將 C# 樹立為真正令人敬佩的程式設計語言。 讓我們看看此版本的一些主要功能：

- [自動設定的屬性](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [匿名類型](../programming-guide/classes-and-structs/anonymous-types.md)
- [查詢運算式](../linq/query-expression-basics.md)
- [Lambda 運算式](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [運算式樹狀架構](../expression-trees.md)
- [擴充方法](../programming-guide/classes-and-structs/extension-methods.md)
- [隱含鍵入的局部變數](../language-reference/keywords/var.md)
- [部分方法](../language-reference/keywords/partial-method.md)
- [物件與集合初始化器](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

回顧以往，許多功能似乎無法避免和分離。 它們全都因為策略的緣故而放在一起。 一般認為 C# 版本的殺手級功能是查詢運算式，也稱為 Language-Integrated Query (LINQ)。

更細看的話，則會探討出運算式樹狀架構、Lambda 運算式及匿名型別才是建構 LINQ 的基礎。 但無論如何，C# 3.0 呈現了革命性的概念。 C# 3.0 已經開始打下基礎，將 C# 變成混合式的物件導向 / 功能性語言。

具體來說，您現在可以撰寫 SQL 樣式的宣告式查詢，尤其是對集合執行作業。 您不必撰寫 `for` 迴圈來計算整數清單的平均值，您現在只要用 `list.Average()` 就能做到。 查詢運算式和擴充方法的組合，結果看似整數清單變得聰明許多。

人們真正抓住並整合概念需要時間，但他們逐漸做到了。 而多年之後的現在，程式碼已經精簡、簡單且功能強大許多。

## <a name="c-version-40"></a>C# 4.0 版

C# 版本 4.0 與 Visual Studio 2010 一起發佈,將很難達到版本 3.0 的突破性狀態。 3.0 版開始，C# 讓語言穩固地擺脫 Java 的影子，並建立聲望。 語言很快地變優雅。

下一版確實導入了一些有趣的新功能：

- [動態繫結](../language-reference/builtin-types/reference-types.md)
- [具名/選擇性引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [泛型 covariant 和 contravariant](../../standard/generics/covariance-and-contravariance.md)
- [嵌入式互通型態](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

內嵌 interop 型別能減輕部署痛苦。 泛型 covariance 和 contravariance 可讓您有更強大的功能來使用泛型，但它們有點學術，可能最受架構和程式庫作者欣賞。 具名和選擇性參數可讓您消除許多方法多載，並提供方便性。 但這些功能沒有一項能完全改變典範。

主要功能是導入 `dynamic` 關鍵字。 `dynamic` 關鍵字為 C# 4.0 版導入在編譯時期型別設定時覆寫編譯器的功能。 藉由使用動態關鍵字，您可以建立類似於動態型別語言 (例如 JavaScript) 的建構。 您可以建立 `dynamic x = "a string"` 然後將它加六，留給執行階段找出接下來要採取的動作。

動態繫結可能會有錯誤，但也給予您語言內的強大功能。

## <a name="c-version-50"></a>C# 5.0 版

C# 版本 5.0 與 Visual Studio 2012 一起發佈,是該語言的重點版本。 幾乎該版本的所有心血都投入了另一個奠基的語言概念：非同步程式設計的 `async` 和 `await` 模型。  以下是主要的功能清單：

- [非同步成員](../async.md)
- [呼叫端資訊屬性](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>另請參閱

- [程式碼專案：C# 5.0 中的呼叫端資訊屬性](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

呼叫端資訊屬性可讓您輕鬆地擷取您正在執行的內容，而不必依賴大量的未定案反映程式碼。 它在診斷和記錄工作方面有許多用途。

但是 `async` 和 `await` 是此版本真正的明星。 當這些功能在 2012 年中推出時，C# 再次改變了遊戲，因為它將非同步深植在語言中，成為頭等參與者。 如果您曾經處理過長時間執行的作業，以及回撥網的實作，您可能會愛上這項語言功能。

## <a name="c-version-60"></a>C# 6.0 版

在 3.0 和 5.0 版本中，C# 在物件導向語言中新增了一些重大的新功能。 隨著版本 6.0 與 Visual Studio 2015 發佈, 它將放棄做一個主要殺手功能, 而是釋放許多較小的功能,使 C# 程式設計更有成效. 以下說明其中一部分：

- [動態匯入](./csharp-6.md#using-static)
- [例外篩選器](./csharp-6.md#exception-filters)
- [Auto 屬性初始設定式](./csharp-6.md#auto-property-initializers)
- [運算式主體的成員](./csharp-6.md#expression-bodied-function-members)
- [Null 傳播程式](./csharp-6.md#null-conditional-operators)
- [字串插補](./csharp-6.md#string-interpolation)
- [nameof 運算子](./csharp-6.md#the-nameof-expression)
- [索引初始設定式](csharp-6.md#extension-add-methods-in-collection-initializers)

其他新功能包括：

- catch/finally 區塊中的 Await
- 僅限 getter 屬性的預設值

這些功能每個本身都很有趣。 但是，如果您一起看它們，您會發現有趣的模式。 在此版本中，C# 排除語言樣本，以使程式碼更簡易、可讀性更高。 因此，對於喜好乾淨、簡單程式碼的人而言，這個語言版本大幅勝出。

雖然本身不是傳統的語言功能，他們在這個版本中做了另外一件事。 他們將 [Roslyn 編譯器發表為服務](https://github.com/dotnet/roslyn)。 C# 編譯器現在會以 C# 撰寫，您可以使用編譯器，作為程式設計工作的一部分。

## <a name="c-version-70"></a>C# 7.0 版

C# 版本 7.0 與 Visual Studio 2017 一起發佈。 此版本擁有 C# 6.0 中的某些進化和酷炫的東西，但是沒有編譯器作為服務。 下列為部分新功能：

- [Out 變數](./csharp-7.md#out-variables)
- [Tuple 和解構](./csharp-7.md#tuples)
- [模式符合](./csharp-7.md#pattern-matching)
- [區域函式](./csharp-7.md#local-functions)
- [展開的運算式主體成員](./csharp-7.md#more-expression-bodied-members)
- [Ref 區域變數和傳回](./csharp-7.md#ref-locals-and-returns)

其他功能包括：

- [捨棄](./csharp-7.md#discards)
- [二進位常值和數字分隔符號](./csharp-7.md#numeric-literal-syntax-improvements)
- [throw 運算式](./csharp-7.md#throw-expressions)

所有這些功能會提供開發人員很棒的新功能，以及撰寫出比以往更簡潔的程式碼的機會。 重點強調是將變數宣告緊縮為使用 `out` 關鍵字，以及允許透過 tuple 傳回多個值。

但 C# 的運用範圍更廣了。 .NET Core 現在以任何作業系統為目標，並堅定地關注雲端和可攜性。  除了提出新功能之外，這些新功能當然也會佔據語言設計人員的想法和時間。

## <a name="c-version-71"></a>C# 版本 7.1

C# 開始使用 C# 7.1*發表點版本*。 此版本添加了[語言版本選擇](../language-reference/configure-language-version.md)配置元素、三個新語言功能和新的編譯器行為。

此版本的新款語言功能包括：

- [`async``Main`方法](./csharp-7-1.md#async-main)
  - 應用程式的進入點允許使用`async`修飾詞。
- [`default`文字運算式](./csharp-7-1.md#default-literal-expressions)
  - 目標類型可以推斷時，可以在預設值運算式中使用預設常值運算式。
- [Tuple 型別推導](./csharp-7-1.md#inferred-tuple-element-names)
  - 在許多情況下，Tuple 項目的名稱均可從 Tuple 初始化推斷來加以推斷。
- [泛型型別參數的模式比對](./csharp-7-1.md#pattern-matching-on-generic-type-parameters)
  - 您可以對型別為泛型型別參數的變數使用模式比對運算式。

最後，編譯器有兩個選項 `-refout` 和 `-refonly`，它們控制了[參考組件產生](./csharp-7-1.md#reference-assembly-generation)。

## <a name="c-version-72"></a>C# 版本 7.2

C# 7.2 添加了幾個小語言功能:

- [撰寫安全、有效率之程式碼的技巧](./csharp-7-2.md#safe-efficient-code-enhancements)
  - 此為語法改進功能組合，其可讓使用參考語意進行實質型別作業變得可能。
- [非後置具名引數](./csharp-7-2.md#non-trailing-named-arguments)
  - 具名引數之後可以接著位置引數。
- [數值常值中的前置底線](./csharp-7-2.md#leading-underscores-in-numeric-literals)
  - 數值常值的任何列印數字之前，現都可加上前置底線。
- [`private protected`存取修改器](./csharp-7-2.md#private-protected-access-modifier)
  - 您可利用 `private protected` 存取修飾詞，存取相同組件中的衍生類別。
- [條件`ref`運算式](./csharp-7-2.md#conditional-ref-expressions)
  - 條件運算式 (`?:`) 的結果現在可以是參考。

## <a name="c-version-73"></a>C# 版本 7.3

C# 7.3 版有兩個主要的佈景主題。 其中一個佈景主題提供了使安全的程式碼具有與不安全的程式碼一樣高效能的功能。 第二個佈景主題提供現有功能的累加增強功能。 此外，此版本中加入了新的編譯器選項。

下列新功能針對安全的程式碼支援較佳效能的佈景主題：

- [您可以在不釘選的情況下存取固定的欄位。](csharp-7-3.md#indexing-fixed-fields-does-not-require-pinning)
- [您可以重新分配`ref`局部變數。](csharp-7-3.md#ref-local-variables-may-be-reassigned)
- [您可以在陣列上`stackalloc`使用初始化程式。](csharp-7-3.md#stackalloc-arrays-support-initializers)
- [可以將語句與`fixed`支援模式的任何類型的語句一起使用。](csharp-7-3.md#more-types-support-the-fixed-statement)
- [您可以使用其他的泛型限制式。](csharp-7-3.md#enhanced-generic-constraints)

已在現有功能中提供下列增強功能：

- [您可以測試`==`和`!=`中列型態。](csharp-7-3.md#tuples-support--and-)
- [您可以在更多位置使用運算式變數。](csharp-7-3.md#extend-expression-variables-in-initializers)
- [您可以將屬性附加至自動實作屬性的支援欄位。](csharp-7-3.md#attach-attributes-to-the-backing-fields-for-auto-implemented-properties)
- [當參數不同時的方法解析`in`得到了改進。](csharp-7-3.md#in-method-overload-resolution-tiebreaker)
- [多載解析現在會有較少模稜兩可的情況。](csharp-7-3.md#improved-overload-candidates)

新的編譯器選項：

- [`-publicsign`啟用程式集的開源軟體 (OSS) 簽名。](csharp-7-3.md#public-or-open-source-signing)
- [`-pathmap`為源目錄提供映射。](csharp-7-3.md#pathmap)

## <a name="c-version-80"></a>C# 版本 8.0

C# 8.0 是第一個專門針對 .NET Core 的主要 C# 版本。 某些功能依賴於新的 CLR 功能,其他功能則依賴於僅在 .NET Core 中添加的庫類型。 C# 8.0 向 C# 語言新增了以下功能和增強功能:

- [唯讀成員](./csharp-8.md#readonly-members)
- [預設介面方法](./csharp-8.md#default-interface-methods)
- [模式比對增強功能](./csharp-8.md#more-patterns-in-more-places)：
  - [Switch 運算式](./csharp-8.md#switch-expressions)
  - [屬性模式](./csharp-8.md#property-patterns)
  - [Tuple 模式](./csharp-8.md#tuple-patterns)
  - [位置模式](./csharp-8.md#positional-patterns)
- [Using 宣告](./csharp-8.md#using-declarations)
- [靜態區域函式](./csharp-8.md#static-local-functions)
- [可處置的 ref struct](./csharp-8.md#disposable-ref-structs)
- [可為 Null 的參考型別](../language-reference/builtin-types/nullable-reference-types.md)
- [非同步資料流](./csharp-8.md#asynchronous-streams)
- [索引和範圍](./csharp-8.md#indices-and-ranges)
- [空合併配置](./csharp-8.md#null-coalescing-assignment)
- [非託管建構類型](./csharp-8.md#unmanaged-constructed-types)
- [巢狀式的 Stackalloc](./csharp-8.md#stackalloc-in-nested-expressions)
- [增強插值逐字串](./csharp-8.md#enhancement-of-interpolated-verbatim-strings)

默認介面成員需要在CLR中增強。 這些功能在 .NET Core 3.0 的 CLR 中添加。 範圍和索引以及非同步需要在 .NET Core 3.0 庫中使用新類型。 當對庫進行批號說明以提供有關參數和返回值的 null 狀態的語義資訊時,空引用類型雖然在編譯器中實現,但使用時非常有用。 這些註釋正在 .NET 核心庫中添加。

_文章_ [_最初發佈於 NDepend 部落格_](https://blog.ndepend.com/c-versions-look-language-history/)_，感謝 Erik Dietrich 和 Patrick Smacchia。_
