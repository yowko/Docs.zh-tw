---
title: "C# 的歷史"
description: "這個語言最初是什麼樣子？而這些年來又有哪些演進？"
keywords: "C#, .NET、.NET Core、最新動向、C# 歷史"
author: erikdietrich
ms.author: wiwagn
ms.date: 09/20/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 207c97c5dd7e04f815da61bff7f44393aea86222
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="the-history-of-c"></a>C# 的歷程記錄 #

這個語言最初是什麼樣子？ 而這些年來又有哪些演進？

## <a name="c-version-10"></a>C# 1.0 版

當您返回，並尋找時，C# 版本 1.0 許多看起來像是 Java。 做為[屬於 ECMA 其規定的設計目標](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)，它要在其中搜尋要為 「 簡單、 現代化、 一般用途物件導向語言。 」  同時，看似 Java 用它來達成這些早期的設計目標。

但如果您回顧 C# 1.0 現在，您會發現自己有點 dizzy。 由於缺乏的內建的非同步功能和部分靈活周圍我們需要，授與的泛型功能。 為事實上，它會將泛型缺乏完全。  和[LINQ](../linq/index.md)嗎？ 無法使用尚未。 如此會進入某些年。

C# 1.0 版查詢等量相較於現今的功能。 您會發現自己撰寫一些詳細資訊的程式碼。 但是，您必須啟動的地方。 C# 版本 1.0 是可行的替代方案 java Windows 平台上。

## <a name="c-version-20"></a>C# 2.0 版

現在項目開始有趣。 讓我們看看的 C# 2.0 中，於 2005，以及 Visual Studio 2005 發行一些主要功能：

- [泛型](../programming-guide/generics/index.md)
- [部分型別](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [匿名方法](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [可為 Null 的型別](../programming-guide/nullable-types/index.md)
- [迭代器](../programming-guide/concepts/iterators.md)
- [共變數和反變數](../programming-guide/concepts/covariance-contravariance/index.md)

雖然 C# 可能啟動做為泛型相當 Object-Oriented (OO) 語言，C# 2.0 版中變更該急。 一旦它們在其下的其英呎，它們發生之後有些嚴重的開發人員痛苦點。 而且它們發生之後它們以大的方式。

使用泛型時，您可以有型別和可操作的任意型別，同時仍然保留型別安全的方法。 因此，比方說，有<xref:System.Collections.Generic.List%601>可讓您有`List<string>`或`List<int>`並且時您逐一執行這些字串或整數的類型安全作業。 這是比建立更好`ListInt`繼承者注意事項或從轉型`Object`針對每個作業。

C# 2.0 版回到迭代器。 若要讓它簡潔，這可讓您逐一查看中的項目`List`（或其他可列舉的類型） 與`foreach`迴圈。 需要這樣做為第一級語言的一部分大幅增強可讀性語言和原因相關的程式碼的人的能力。

然後，C# 繼續播放追補 java 的位元。 Java 具有已發行版本包含泛型和迭代器。 但是，很快就會變更為持續發展相距的語言。

## <a name="c-version-30"></a>C# 3.0 版

C# 3.0 版隨附在晚期 2007 中，以及 Visual Studio 2008 中，雖然語言功能的完整的船實際上會使用 C# 3.5 版。 這個版本會標示成長的 C# 的重大變更。 建立 C# 做為真正極為困難的程式設計語言。 在此版本中，讓我們看看一些主要功能：

- [自動實作屬性](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [匿名型別](../programming-guide/classes-and-structs/anonymous-types.md)
- [查詢運算式](../linq/query-expression-basics.md)
- [Lambda 運算式](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [運算式樹狀架構](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [擴充方法](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)

回顧以往，許多功能似乎無法避免和擺。 可以全部放在一起策略。 它通常會想的 C# 版本的令人激賞的功能則是查詢運算式中，也稱為 Language-Integrated Query (LINQ)。

更 nuanced 的檢視會檢查做為建構的 LINQ 運算式 tress、 lambda 運算式和匿名型別。 但是，在任一情況下，C# 3.0 呈現革命性的概念。 C# 3.0 已經開始配置基礎，將 C# 變成物件導向的混合式 / 功能性語言。

具體來說，您現在可以撰寫 SQL 樣式的宣告式查詢的集合，以及其他項目上執行作業。 反而比撰寫`for`迴圈來計算平均值的整數清單，也可以立即執行，只需為`list.Average()`。 查詢運算式和擴充方法的組合，變成結果看起來好像整數的清單已收到一大堆更聰明。

花費時間的人真的抓住及整合概念，但是逐漸並未成功。 而且，年之後，程式碼更精簡、 簡單，以及功能。

## <a name="c-version-40"></a>C# 4.0 版

C# 4.0 版會有困難的時間住 groundbreaking 3.0 版的狀態。 3.0 版開始，C# 具有語言穩固地編寫從移陰影 Java，並進入優點。 語言快速成為優雅。

下一版沒有導入了一些有趣的新功能：

- [動態繫結](../language-reference/keywords/dynamic.md)
- [名為/選擇性引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [泛型 covariant 和 contravariant](../../standard/generics/covariance-and-contravariance.md)
- [內嵌 interop 類型](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

內嵌 interop 類型減輕部署痛苦。 泛型共變數和反變數可讓您更強大的功能使用泛型，但位元學術和可能最令人激賞的架構和程式庫作者。 具名和選擇性參數可讓您消除許多方法多載，並提供方便。 但無這項功能完全典範改變。

主要功能已引入`dynamic`關鍵字。 `dynamic`關鍵字引入 C# 4.0 版覆寫於編譯時期輸入編譯器的功能。 藉由使用動態關鍵字，您可以建立建構類似於動態具型別語言，例如 JavaScript。 您可以建立`dynamic x = "a string"`並將六個，留給執行階段找出接下來要採取的動作。

這可讓您可能的錯誤，但在語言中很棒的電源。

## <a name="c-version-50"></a>C# 5.0 版

C# 5.0 版是語言的非常具有焦點版本。 幾乎所有該版本的投入時間會引進另一個 groundbreaking 語言概念。  以下是主要的功能清單：

- [非同步成員](../async.md)
- [呼叫端資訊屬性](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

呼叫端資訊屬性可讓您輕鬆地擷取您正在執行需要大量的未定案反映程式碼就可以做到的內容的相關資訊。 它有許多用途，在 診斷和記錄工作。

但是`async`和`await`是此版本的。 當這些功能 2012年中，C# 變更遊戲再次非同步將為第一級的參與者為語言。 如果您曾經處理過長時間執行作業和 web 的回撥的實作，可能會愛這項語言功能。

## <a name="c-version-60"></a>C# 6.0 版

3.0 和 5.0 的版本中，C# 必須加入一些令人驚嘆的功能在物件導向語言中。 版本 6.0，會移開進行主控項的令人激賞功能且改用釋放許多功能，很高興語言的使用者。 以下是一些它們：

- [靜態匯入](../language-reference/keywords/using-static.md)
- [例外狀況篩選條件](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [屬性初始設定式](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [運算式主體的成員](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Null （propagator block)](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [字串插值](../language-reference/keywords/interpolated-strings.md)
- [nameof 運算子](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [字典的初始設定式](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md)

這些功能很有趣好似它本身。 但是，如果完全看看它們，您會發現有趣的模式。 在此版本中，C# 排除使程式碼，更簡易、 可讀性更高的語言重複使用。 讓這個語言版本風扇的乾淨、 簡單的程式碼，為龐大 win。

雖然它不是在本身的傳統的語言功能，它們就會支援這個版本中，以及其他一件事。 釋放它們[Roslyn 編譯器以服務](https://github.com/dotnet/roslyn)。 C# 編譯器現在會寫入 C# 中，您可以使用編譯器，做為您的程式設計工作的一部分。

## <a name="c-version-70"></a>C# 7.0 版

最新的主要版本為 C# 7.0 版。 此版本中部 C# 6.0 中，但是沒有編譯器有某些進化，也很酷個人資料，做為服務。 以下是一些新功能：

- [Out 變數](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [Tuple 和解構](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [模式比對](./csharp-7.md#pattern-matching)
- [區域函式](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [展開的運算式主體的成員](./csharp-7.md#more-expression-bodied-members)
- [Ref 本機與傳回](./csharp-7.md#ref-locals-and-returns)

所有這些功能提供開發人員與寫入比以往更簡潔的程式碼有機會項很棒的新功能。 反白顯示會緊縮至搭配使用的變數宣告`out`關鍵字，以及讓透過 tuple 的多個傳回值。

但 C# 會被放曾經更廣泛的使用。 .NET core 現在為目標的任何作業系統，且其眼睛穩固地可攜性和雲端上。  這當然會佔據語言設計人員的想法和時間，除了在接下來的新功能。

_發行項_ [_最初發行 NDepend 部落格上_](https://blog.ndepend.com/c-versions-look-language-history/)_、 Erik Dietrich 和 Patrick Smacchia 項。_
