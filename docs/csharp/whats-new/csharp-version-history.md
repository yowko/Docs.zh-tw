---
title: C# 的歷史 - C# 指南
description: 最早的語言版本有哪些內容，而在之後有什麼演變？
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: c750bf8e1ae6dd94c11dc887921c5c365cc04b10
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981929"
---
# <a name="the-history-of-c"></a>C\# 的歷史

此文章提供了 C# 語言每個主要版本的歷史。 C# 小組將持續創新並加入新功能。 您可以在ˋ GitHub 上的 [dotnet/roslyn 存放庫repository](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) 存放庫中找到詳細語言功能狀態 (包括針對未來版本考慮加入的功能)。

> [!IMPORTANT]
> C# 語言中的部分功能仰賴 C#規格定義為「標準程式庫」中的型別和方法。 .NET 平台在許多套件中會提供那些類型與方法。 例外狀況處理便是其中一個例子。 每個 `throw` 陳述式或運算式都會受到檢查，以確保擲回衍生自 <xref:System.Exception> 的物件。 每個 `catch` 也一樣會受到檢查，以確保攔截到衍生自 <xref:System.Exception> 的型別。 每個版本都可能會加入新的需求。 若要在較舊的環境中使用最新的語言功能，可能需要安裝特定的程式庫。 每個特定版本的頁面中會記載這些相依性。 若要知道此相依性的背景，可深入了解[語言和程式庫之間的關係](relationships-between-language-and-library.md)。

C# 建置工具將最新的主要語言版本視為預設語言版本。 主要版本之間可能存在單點發行版本，此節的其他文章對此進行了詳細介紹。 若要使用小數點版本中的最新功能，您需要[設定編譯器語言版本](../language-reference/configure-language-version.md)並選取該版本。 自 C# 7.0 以來已經有三個單點發行版本：

* [C# 7.3](csharp-7-3.md)：
  - [Visual Studio 2017 15.7 版](https://visualstudio.microsoft.com/vs/whatsnew/)和 [.NET Core 2.1 SDK 2.1.300 RC1](../../core/whats-new/index.md) 目前提供 C# 7.3。
* [C# 7.2](csharp-7-2.md):
  - [Visual Studio 2017 15.5 版](https://visualstudio.microsoft.com/vs/whatsnew/)和 [.NET Core 2.0 SDK](../../core/whats-new/index.md) 目前提供 C# 7.2。
* [C# 7.1](csharp-7-1.md)：
  - [Visual Studio 2017 15.3 版](https://visualstudio.microsoft.com/vs/whatsnew/)和 [.NET Core 2.0 SDK](../../core/whats-new/index.md) 已新增這些功能。

## <a name="c-version-10"></a>C# 1.0 版

當您回過頭看，C# 1.0 版很多看起來很像 Java。 在[其聲明的 ECMA 設計目標當中](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)，它試圖成為「簡單、現代化、一般用途的物件導向語言」。  同時，看似 Java 表示它達成了那些早期的設計目標。

但如果您現在回顧 C# 1.0，會覺得有點暈眩。 它缺乏內建的非同步功能和部分圍繞著您視為理所當然的泛型熟練功能。 事實上，它完全缺乏了泛型。  那麼 [LINQ](../linq/index.md) 呢？ 尚無法使用。 那些新增項目需要好幾年才會出現。

C# 1.0 版看起來與現今相比去除了一些功能。 您會發現自己撰寫一些詳細的程式碼。 但您仍然必須從某處開始。 C# 1.0 版是 Windows 平台上可行的 Java 替代方案。

C# 1.0 的主要功能包含：

- [類別](../programming-guide/classes-and-structs/classes.md)
- [結構](../programming-guide/classes-and-structs/structs.md)
- [介面](../programming-guide/interfaces/index.md)
- [事件](../events-overview.md)
- [屬性](../properties.md)
- [委派](../delegates-overview.md)
- [運算式](../programming-guide/statements-expressions-operators/expressions.md)
- [陳述式](../programming-guide/statements-expressions-operators/statements.md)
- [屬性](../programming-guide/concepts/attributes/index.md)
- [常值](../language-reference/keywords/literal-keywords.md)

## <a name="c-version-12"></a>C# 1.2 版

Visual Studio 2003 隨附的 C# 1.2 版。 本版內含對語言的小幅功能改善。 最值得注意的是，自本版開始，當 <xref:System.Collections.IEnumerator> 實作 <xref:System.IDisposable> 時，在 `foreach` 迴圈產生的程式碼會在 <xref:System.Collections.IEnumerator> 呼叫 <xref:System.IDisposable.Dispose%2A>。

## <a name="c-version-20"></a>C# 2.0 版

現在事情開始變得有趣。 讓我們看看 2005 年與 Visual Studio 2005 一起發行的 C# 2.0 中，一些主要功能：

- [泛型](../programming-guide/generics/index.md)
- [部分型別](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [匿名方法](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [可為 Null 的型別](../programming-guide/nullable-types/index.md)
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

C# 3.0 版在 2007 年晚期和 Visual Studio 2008 一起出現，不過語言功能的完整陣容實際上是在 .NET Framework 3.5 版時齊備。 這個版本標記了 C# 發展的一個重大變更。 它將 C# 樹立為真正令人敬佩的程式設計語言。 讓我們看看此版本的一些主要功能：

- [自動實作屬性](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [匿名型別](../programming-guide/classes-and-structs/anonymous-types.md)
- [查詢運算式](../linq/query-expression-basics.md)
- [Lambda 運算式](../lambda-expressions.md)
- [運算式樹狀架構](../expression-trees.md)
- [擴充方法](../programming-guide/classes-and-structs/extension-methods.md)
- [隱含型別區域變數](../language-reference/keywords/var.md)
- [部分方法](../language-reference/keywords/partial-method.md)
- [物件和集合初始設定式](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

回顧以往，許多功能似乎無法避免和分離。 它們全都因為策略的緣故而放在一起。 一般認為 C# 版本的殺手級功能是查詢運算式，也稱為 Language-Integrated Query (LINQ)。

更細看的話，則會探討出運算式樹狀架構、Lambda 運算式及匿名型別才是建構 LINQ 的基礎。 但無論如何，C# 3.0 呈現了革命性的概念。 C# 3.0 已經開始打下基礎，將 C# 變成混合式的物件導向 / 功能性語言。

具體來說，您現在可以撰寫 SQL 樣式的宣告式查詢，尤其是對集合執行作業。 您不必撰寫 `for` 迴圈來計算整數清單的平均值，您現在只要用 `list.Average()` 就能做到。 查詢運算式和擴充方法的組合，結果看似整數清單變得聰明許多。

人們真正抓住並整合概念需要時間，但他們逐漸做到了。 而多年之後的現在，程式碼已經精簡、簡單且功能強大許多。

## <a name="c-version-40"></a>C# 4.0 版

C# 4.0 版要堅守 3.0 版的奠基狀態會很困難。 3.0 版開始，C# 讓語言穩固地擺脫 Java 的影子，並建立聲望。 語言很快地變優雅。

下一版確實導入了一些有趣的新功能：

- [動態繫結](../language-reference/keywords/dynamic.md)
- [具名/選擇性引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [泛型 covariant 和 contravariant](../../standard/generics/covariance-and-contravariance.md)
- [內嵌 Interop 型別](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

內嵌 interop 型別能減輕部署痛苦。 泛型 covariance 和 contravariance 可讓您有更強大的功能來使用泛型，但它們有點學術，可能最受架構和程式庫作者欣賞。 具名和選擇性參數可讓您消除許多方法多載，並提供方便性。 但這些功能沒有一個能完全改變典範。

主要功能是導入 `dynamic` 關鍵字。 `dynamic` 關鍵字為 C# 4.0 版導入在編譯時期型別設定時覆寫編譯器的功能。 藉由使用動態關鍵字，您可以建立類似於動態型別語言 (例如 JavaScript) 的建構。 您可以建立 `dynamic x = "a string"` 然後將它加六，留給執行階段找出接下來要採取的動作。

動態繫結可能會有錯誤，但也給予您語言內的強大功能。

## <a name="c-version-50"></a>C# 5.0 版

C# 5.0 版是該語言的一個聚焦版本。 幾乎該版本的所有心血都投入了另一個奠基的語言概念：非同步程式設計的 `async` 和 `await` 模型。  以下是主要的功能清單：

- [非同步成員](../async.md)
- [呼叫端資訊屬性](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>請參閱

* [Code Project：C# 5.0 的呼叫端資訊屬性](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

呼叫端資訊屬性可讓您輕鬆地擷取您正在執行的內容，而不必依賴大量的未定案反映程式碼。 它在診斷和記錄工作方面有許多用途。

但是 `async` 和 `await` 是此版本真正的明星。 當這些功能在 2012 年中推出時，C# 再次改變了遊戲，因為它將非同步深植在語言中，成為頭等參與者。 如果您曾經處理過長時間執行的作業，以及回撥網的實作，您可能會愛上這項語言功能。

## <a name="c-version-60"></a>C# 6.0 版

在 3.0 和 5.0 版本中，C# 在物件導向語言中新增了一些重大的新功能。 在 6.0 版中，它不再作為主控的殺手級功能，而是改為發表讓 C# 程式設計更具生產力的許多較小功能。 這裡列出其中一些：

- [動態匯入](./csharp-6.md#using-static)
- [例外狀況篩選條件](./csharp-6.md#exception-filters)
- [Auto 屬性初始設定式](./csharp-6.md#auto-property-initializers)
- [運算式主體的成員](./csharp-6.md#expression-bodied-function-members)
- [Null 傳播程式](./csharp-6.md#null-conditional-operators)
- [字串內插補點](./csharp-6.md#string-interpolation)
- [nameof 運算子](./csharp-6.md#the-nameof-expression)
- [索引初始設定式](csharp-6.md#extension-add-methods-in-collection-initializers)

其他新功能包括：

- catch/finally 區塊中的 Await
- 僅限 getter 屬性的預設值

這些功能每個本身都很有趣。 但是，如果您一起看它們，您會發現有趣的模式。 在此版本中，C# 排除語言樣本，以使程式碼更簡易、可讀性更高。 因此，對於喜好乾淨、簡單程式碼的人而言，這個語言版本大幅勝出。

雖然本身不是傳統的語言功能，他們在這個版本中做了另外一件事。 他們將 [Roslyn 編譯器發表為服務](https://github.com/dotnet/roslyn)。 C# 編譯器現在會以 C# 撰寫，您可以使用編譯器，作為程式設計工作的一部分。

## <a name="c-version-70"></a>C# 7.0 版

最新的主要版本是 C# 7.0 版。 此版本擁有 C# 6.0 中的某些進化和酷炫的東西，但是沒有編譯器作為服務。 下列為部分新功能：

- [Out 變數](./csharp-7.md#out-variables)
- [Tuple 和解構](./csharp-7.md#tuples)
- [模式比對](./csharp-7.md#pattern-matching)
- [區域函式](./csharp-7.md#local-functions)
- [展開的運算式主體成員](./csharp-7.md#more-expression-bodied-members)
- [Ref 區域變數和傳回](./csharp-7.md#ref-locals-and-returns)

其他功能包括：

- [捨棄](./csharp-7.md#discards)
- [二進位常值和數字分隔符號](./csharp-7.md#numeric-literal-syntax-improvements)
- [throw 運算式](./csharp-7.md#throw-expressions)

所有這些功能會提供開發人員很棒的新功能，以及撰寫出比以往更簡潔的程式碼的機會。 重點強調是將變數宣告緊縮為使用 `out` 關鍵字，以及允許透過 tuple 傳回多個值。

但 C# 的運用範圍更廣了。 .NET Core 現在以任何作業系統為目標，並堅定地關注雲端和可攜性。  除了提出新功能之外，這些新功能當然也會佔據語言設計人員的想法和時間。

_文章_ [_最初發佈於 NDepend 部落格_](https://blog.ndepend.com/c-versions-look-language-history/)_，感謝 Erik Dietrich 和 Patrick Smacchia。_
