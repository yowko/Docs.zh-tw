---
title: C# 的歷史 - C# 指南
description: 最早的語言版本有哪些內容，而在之後有什麼演變？
keywords: C#, .NET, .NET Core, 新增功能, C# 歷史
author: erikdietrich
ms.author: wiwagn
ms.date: 09/20/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: d24d190eab5896121231543e6696b6a4861b5bb8
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="the-history-of-c"></a>C# 的歷史 #

最早的語言版本有哪些內容？ 而在那之後的幾年有什麼演變？

## <a name="c-version-10"></a>C# 1.0 版

當您回過頭看，C# 1.0 版很多看起來很像 Java。 在[其聲明的 ECMA 設計目標當中](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)，它試圖成為「簡單、現代化、一般用途的物件導向語言」。  同時，看似 Java 表示它達成了那些早期的設計目標。

但如果您現在回顧 C# 1.0，會覺得有點暈眩。 它缺乏了內建的非同步功能和部分圍繞著我們視為理所當然的泛型的熟練功能。 事實上，它完全缺乏了泛型。  那麼 [LINQ](../linq/index.md) 呢？ 尚無法使用。 那需要好幾年才會出現。

C# 1.0 版看起來與現今相比去除了一些功能。 您會發現自己撰寫一些詳細的程式碼。 但您仍然必須從某處開始。 C# 1.0 版是 Windows 平台上可行的 Java 替代方案。

## <a name="c-version-20"></a>C# 2.0 版

現在事情開始變得有趣。 讓我們看看 2005 年與 Visual Studio 2005 一起發行的 C# 2.0 中，一些主要功能：

- [泛型](../programming-guide/generics/index.md)
- [部分型別](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [匿名方法](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [可為 Null 的型別](../programming-guide/nullable-types/index.md)
- [迭代器](../programming-guide/concepts/iterators.md)
- [共變數和反變數](../programming-guide/concepts/covariance-contravariance/index.md)

雖然 C# 可能一開始是相當泛型的 物件導向 (OO) 語言，但 C# 2.0 版很急促地改變了。 穩定之後，它們追蹤一些嚴重的開發人員痛苦點。 而且是徹底地追蹤。

使用泛型時，您有型別和方法，可以操作任意型別，同時仍然保留型別安全。 比方說，有 <xref:System.Collections.Generic.List%601> 可讓您具有 `List<string>` 或 `List<int>`，並且對那些字串或整數逐一執行型別安全的作業。 這勝過針對每個作業建立 `ListInt` 繼承者或是從 `Object` 轉型。

C# 2.0 版帶來了迭代器。 簡潔地說，這可讓您使用 `foreach` 迴圈逐一查看 `List` (或其他可列舉型別) 中的項目。 將這當成語言的頭等部分能大幅增強語言的可讀性，並讓人們能理解程式碼。

但 C# 仍繼續追趕 Java。 Java 已經發行了包含泛型和迭代器的版本。 但是，很快就會變更，因為語言會持續朝不同方向發展。

## <a name="c-version-30"></a>C# 3.0 版

C# 3.0 版在 2007 年晚期和 Visual Studio 2008 一起出現，不過語言功能的完整陣容實際上是在 C# 3.5 版時齊備。 這個版本標記了 C# 發展的一項重大變更。 它將 C# 樹立為真正令人敬佩的程式設計語言。 讓我們看看此版本的一些主要功能：

- [自動實作屬性](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [匿名型別](../programming-guide/classes-and-structs/anonymous-types.md)
- [查詢運算式](../linq/query-expression-basics.md)
- [Lambda 運算式](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [運算式樹狀架構](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [擴充方法](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)

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
- [內嵌 Interop 型別](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

內嵌 interop 型別能減輕部署痛苦。 泛型 covariance 和 contravariance 可讓您有更強大的功能來使用泛型，但它們有點學術，可能最受架構和程式庫作者欣賞。 具名和選擇性參數可讓您消除許多方法多載，並提供方便性。 但這些功能沒有一項能完全改變典範。

主要功能是導入 `dynamic` 關鍵字。 `dynamic` 關鍵字為 C# 4.0 版導入在編譯時期型別設定時覆寫編譯器的功能。 藉由使用動態關鍵字，您可以建立類似於動態型別語言 (例如 JavaScript) 的建構。 您可以建立 `dynamic x = "a string"` 然後將它加六，留給執行階段找出接下來要採取的動作。

這樣可能會有錯誤，但也給您在語言內強大的功能。

## <a name="c-version-50"></a>C# 5.0 版

C# 5.0 版是該語言非常聚焦的一個版本。 幾乎該版本的所有心血都投入了另一項奠基的語言概念。  以下是主要的功能清單：

- [非同步成員](../async.md)
- [呼叫端資訊屬性](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

呼叫端資訊屬性可讓您輕鬆地擷取您正在執行的內容，而不必依賴大量的未定案反映程式碼。 它在診斷和記錄工作方面有許多用途。

但是 `async` 和 `await` 是此版本真正的明星。 當這些功能在 2012 年中推出時，C# 再次改變了遊戲，因為它將非同步深植在語言中，成為頭等參與者。 如果您曾經處理過長時間執行的作業，以及回撥網的實作，您可能會愛上這項語言功能。

## <a name="c-version-60"></a>C# 6.0 版

3.0 和 5.0 版本中，C# 在物件導向語言中新增了一些令人驚嘆的功能。 在 6.0 版中，它不再作為主控的殺手級功能，而是改為發表取悅語言使用者的許多功能。 這裡列出其中一些：

- [動態匯入](../language-reference/keywords/using-static.md)
- [例外狀況篩選條件](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [屬性初始設定式](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [運算式主體的成員](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Null 傳播程式](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [字串內插補點](../language-reference/tokens/interpolated.md)
- [nameof 運算子](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [字典初始設定式](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md)

這些功能每個本身都很有趣。 但是，如果您一起看它們，您會發現有趣的模式。 在此版本中，C# 排除語言樣本，以使程式碼更簡易、可讀性更高。 因此，對於喜好乾淨、簡單程式碼的人而言，這個語言版本大幅勝出。

雖然本身不是傳統的語言功能，他們在這個版本中做了另外一件事。 他們將 [Roslyn 編譯器發表為服務](https://github.com/dotnet/roslyn)。 C# 編譯器現在會以 C# 撰寫，您可以使用編譯器，作為程式設計工作的一部分。

## <a name="c-version-70"></a>C# 7.0 版

最新的主要版本是 C# 7.0 版。 此版本擁有 C# 6.0 中的某些進化和酷炫的東西，但是沒有編譯器作為服務。 下列為部分新功能：

- [Out 變數](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [Tuple 和解構](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [模式比對](./csharp-7.md#pattern-matching)
- [區域函式](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [展開的運算式主體成員](./csharp-7.md#more-expression-bodied-members)
- [Ref 區域變數和傳回](./csharp-7.md#ref-locals-and-returns)

所有這些功能會提供開發人員很棒的新功能，以及撰寫出比以往更簡潔的程式碼的機會。 重點強調是將變數宣告緊縮為使用 `out` 關鍵字，以及允許透過 tuple 傳回多個值。

但 C# 的運用範圍更廣了。 .NET Core 現在以任何作業系統為目標，並堅定地關注雲端和可攜性。  除了提出新功能之外，這當然也會佔據語言設計人員的想法和時間。

_文章_ [_最初發佈於 NDepend 部落格_](https://blog.ndepend.com/c-versions-look-language-history/)_，感謝 Erik Dietrich 和 Patrick Smacchia。_
