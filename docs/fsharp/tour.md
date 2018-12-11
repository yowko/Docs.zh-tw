---
title: F# 的教學課程
description: 檢查一些 F# 程式設計語言，在此教學課程利用程式碼範例的主要功能。
ms.date: 11/06/2018
ms.openlocfilehash: 32bf892e97b29fcaf426791ef9ada15c9c35b5ae
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143736"
---
# <a name="tour-of-f"></a>F# 的教學課程 #

若要了解 F# 的最佳方式是讀取和寫入 F# 程式碼。 這篇文章會做為某些 F# 語言的重要功能的逐步教學課程，並提供您一些您可以在您的電腦執行的程式碼片段。 若要了解如何設定開發環境，請參閱[開始使用](tutorials/getting-started/index.md)。

F# 中有兩個主要概念： 函式和類型。  本教學課程會強調它們屬於這兩個概念的語言功能。

## <a name="executing-the-code-online"></a>執行線上程式碼

如果您沒有F#安裝在您的電腦上，您可以執行所有使用線上的範例[神鬼寓言 REPL](http://fable.io/repl/)。 神鬼寓言是方言F#直接在您的瀏覽器中執行。 若要檢視的範例，請遵循在 REPL 中，請參閱**範例 > 深入了解 > 教學課程F#** 神鬼寓言 REPL 的左側功能表列中

## <a name="functions-and-modules"></a>函式和模組

任何的 F# 程式的最基本的部分是***函式***分成***模組***。  [函式](language-reference/functions/index.md)來產生輸出的輸入上執行的工作和其下組織[模組](language-reference/modules.md)，這是主要的方式分組在 F# 中的項目。  它們使用來定義[`let`繫結](language-reference/functions/let-bindings.md)，其中指定函式的名稱，並定義其引數。

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` 繫結也是您如何結合其值為名稱，類似於其他語言中的變數。  `let` 繫結***不可變***根據預設，這表示，值或函式繫結的名稱之後, 便無法變更就地。  相較之下，在其他語言中，也就是變數***可變***，這表示其值可以變更在任何時間點的時間。  如果您需要的可變動的繫結時，您可以使用`let mutable ...`語法。

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>數字、 布林值和字串

為.NET 語言，F# 支援相同的基礎[基本型別](language-reference/primitive-types.md)存在於.NET。

以下是如何各種數值類型表示 F# 中：

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

以下是布林值，並執行基本的條件式邏輯如下所示：

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

以下是哪些 basic[字串](language-reference/strings.md)操作如下所示：

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Tuple

[Tuple](language-reference/tuples.md)是 F# 中是什麼大問題。  也就是未命名，但已排序，可以視為值本身的值的群組。  將它們視為與其他值彙總的值。  它們有許多用途，例如方便地從函式傳回多個值，或群組的一些特定便利的值。

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

自 F# 4.1，您也可以建立`struct`tuple。  這些也與交互操作完整 C# 7/Visual Basic 15 元組，這也是`struct`tuple:

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

請務必請注意，因為`struct`tuple 是實值型別，它們無法以隱含方式轉換成參考 tuple，反之亦然。  您必須明確轉換之間的參考和結構元組。

## <a name="pipelines-and-composition"></a>管線和組合

透過管道傳送這類運算子`|>`廣泛處理 F# 中的資料時。 這些運算子都可讓您以有彈性的方式建立的函式為 「 管線 」 函式。 下列範例逐步解說如何使用這些運算子，來建置簡單的功能性管線的利用：

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L282)]

先前所做的範例使用的許多功能的 F#，包括清單處理函式，第一級函式，並[部分的應用程式](language-reference/functions/index.md#partial-application-of-arguments)。 雖然每個這些概念的深入了解可以變得有點進階，應該很清楚如何輕鬆函式可用來建立管線時，處理資料。

## <a name="lists-arrays-and-sequences"></a>清單、 陣列和順序

清單、 陣列和順序是 F# 核心程式庫中的三種主要集合類型。

[列出](language-reference/lists.md)是相同型別的項目排序、 不可變的集合。  它們是單一連結清單中，這表示它們用於列舉型別，但不佳的選擇為隨機存取與串連很大時。  這相較於其他熱門的語言，通常不會使用單向連結清單來代表清單中的清單。

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[陣列](language-reference/arrays.md)是固定大小*可變動*相同型別的元素的集合。  它們支援的項目，快速隨機存取，且速度比 F# 清單因為它們只是連續記憶體區塊。

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[序列](language-reference/sequences.md)是一連串的項目，相同類型的所有邏輯。  這些是較普通的類型，比清單和陣列，在任何邏輯的一系列項目您 「 檢視 」。  它們也凸顯因為他們可***延遲***，這表示只有在需要時，您可以計算項目。

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>遞迴函式

處理集合或序列的項目通常是使用[遞迴](language-reference/functions/index.md#recursive-functions)F# 中。  雖然 F# 提供 for 迴圈和命令式程式設計的支援，但遞迴建議，因為很容易就能保證正確性。

> [!NOTE]
> 下列範例會使用透過模式比對`match`運算式。  本文章稍候會說明這個基本建構。

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F# 也有完整支援 Tail 呼叫最佳化，這是一種最佳化，使其只是最快的速度迴圈建構的遞迴呼叫。

## <a name="record-and-discriminated-union-types"></a>記錄和差別聯集類型

記錄和等位型別中 F# 程式碼，使用兩種基本資料類型，通常的最佳方式來表示 F# 程式中的資料。  雖然這可讓它們與類別類似其他語言中，其主要差異是它們具有結構相等語意。  也就是說，它們是 「 原生 」 比較，相等相當簡單： 只檢查其中一個是否等於其他。

[記錄](language-reference/records.md)會與選擇性成員 （例如方法） 的具名值的彙總。  如果您熟悉使用 C# 或 Java，然後這些應該感覺很像 Poco 或 Pojo-只與結構相等，並降低繁瑣細節。

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

自 F# 4.1，您也可以代表記錄當做`struct`s。  做法是使用`[<Struct>]`屬性：

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[差別聯集 (DUs)](language-reference/discriminated-unions.md)是可能在多個具名的表單或案例的值。  類型中儲存的資料可以是數個相異值的其中一個。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

您也可以使用為 DUs*單一案例差別聯集*，以協助進行基本類型的模型化的網域。  經常、 字串和其他基本型別用來代表項目，並因此會提供特定的意義。  不過，使用資料的基本表示法可能會導致錯誤地指派值不正確 ！  代表每一個不同的單一案例聯集的資訊類型，可以強制執行在此案例中的正確性。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

如上述範例所示，若要取得基礎值的單一案例差別聯集，您必須明確 unwrap。

此外，DUs 也支援遞迴定義，可讓您輕鬆地代表樹狀結構和原本就是遞迴的資料。  例如，以下是可以代表使用二進位搜尋樹狀結構的方式`exists`和`insert`函式。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

DUs 可讓您代表遞迴結構的樹狀目錄中的資料類型，因為此遞迴結構上操作很簡單，可確保正確性。  它也支援在模式比對，如下所示。

此外，您可以在這裡表示為 DUs`struct`與`[<Struct>]`屬性：

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

不過，有兩個要這麼做時，牢記在心的重要事項：

1. 結構 DU 不得以遞迴方式定義。
2. 結構 DU 必須有它的情況下的每個唯一的名稱。

遵循上述的失敗會導致編譯錯誤。

## <a name="pattern-matching"></a>模式比對

[模式比對](language-reference/pattern-matching.md)是 F# 語言功能，可讓 F# 類型上操作的正確性。  在上述範例中，您可能已經注意到一堆`match x with ...`語法。  此建構可讓編譯器，這可以了解資料類型，若要強制您處理所有可能的情況下，使用透過已知的資料類型為詳盡的模式比對時的 「 形狀 」。  這是非常強大的正確性，並可以巧妙地用來 「 上移 」 項目通常會為編譯時間是執行階段問題。

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L742)]

您也可以使用速記`function`建構用於模式比對，這非常有用，當您撰寫函式，請使用[部分的應用程式](language-reference/functions/index.md#partial-application-of-arguments):

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L744-L762)]

您可能已經發現的項目，就是使用`_`模式。  這就所謂[萬用字元模式](language-reference/pattern-matching.md#wildcard-pattern)，這是一種說: 「 我不用管事物 」。  雖然很方便，您可以不小心略過詳盡的模式比對，如果您不小心使用，不會再受益編譯時期強制`_`。  它最適合在您不在意特定資訊的分解的型別已列舉所有有意義的情況下的模式比對運算式時，當模式比對或最後一個子句。

[作用中的模式](language-reference/active-patterns.md)是另一個功能強大的建構函式來使用模式比對。  可讓您輸入的資料分割成自訂的表單，將它們分解在模式比對呼叫站台。  它們可以也進行參數化，因此資料分割定義為函式。  展開上一個範例是為了支援作用中的模式看起來像這樣：

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>選擇性的類型

差別聯集類型的其中一個特殊案例是選項類型，這很有用，它是 F# 核心程式庫的一部分。

[選項類型](language-reference/options.md)是型別代表兩個案例之一： 某個值，或在所有執行任何動作。  它可在任何案例中，值可能會或可能不會造成從特定作業。  這會強制您處理這兩種情況，因此編譯時間需要考量，而不是執行階段問題。  這些通常在 Api 中使用其中`null`用來表示"nothing"相反的而無需擔心`NullReferenceException`在許多情況下。

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>測量單位

F# 型別系統的一項獨特功能是能夠透過單位的量值的數值常值的提供內容。

[測量單位](language-reference/units-of-measure.md)可讓您建立一個單位，計量，例如數值類型的關聯，並有函式上執行的工作單位，而不是數值常值。  這可讓編譯器無法驗證傳入的數值常值的類型在某些環境下合理，因此減少執行階段錯誤相關聯的工作，該類型。

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L817-L842)]

F# 核心程式庫會定義許多的 SI 單位類型和單位轉換。  若要進一步了解，請參閱[Microsoft.FSharp.Data.UnitSystems.SI 命名空間](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d)。

## <a name="classes-and-interfaces"></a>類別和介面

F# 也有完整的支援，.NET 類別[介面](language-reference/interfaces.md)，[抽象類別](language-reference/abstract-classes.md)，[繼承](language-reference/inheritance.md)，依此類推。

[類別](language-reference/classes.md)是.NET 物件，表示型別且可以包含屬性、 方法和事件中的當做其[成員](language-reference/members/index.md)。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L845-L880)]

定義泛型類別也是非常簡單。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L883-L908)]

若要實作的介面，您可以使用`interface ... with`語法或[物件運算式](language-reference/object-expressions.md)。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>若要使用哪些類型

類別、 記錄、 差別聯集和 Tuple 的存在會產生重要的問題： 您應該使用？  大部分所有項目在生活中，例如答案需視您的情況。

Tuple 是適用於從函式傳回多個值，以及使用特定彙總的值做為值本身。

記錄會 「 步驟向上 」 的標籤和支援選擇性的成員具有名為的 Tuple。  它們是適合用來傳輸資料到您的程式的低儀式表示法。  他們有結構相等，因為它們是容易使用的比較。

差別聯的集有許多用途，但核心優勢能夠使用它們搭配模式比對來處理所有可能 「 圖形 」 可以有資料。  

類別是適合大量的原因，例如當您需要代表資訊也將繫結該功能的資訊。  根據經驗法則，當您有功能可在概念上會繫結至一些資料，使用類別和物件導向程式設計的原則是一大優點。  類別也會慣用的資料型別時使用 C# 和 Visual Basic 中，因為這些語言的幾乎所有的作業使用類別。

## <a name="next-steps"></a>後續步驟

既然您已了解的一些主要功能的語言，您應該準備好開始撰寫第一個 F# 程式 ！  請參閱[開始使用](tutorials/getting-started/index.md)以了解如何設定開發環境，並撰寫一些程式碼。

深入了下的一步可以是任何您喜歡，但我們建議您[中的功能性程式設計簡介F#](introduction-to-functional-programming/index.md)熟悉核心功能性程式設計概念。  這些會在建置強固的程式，在 F# 不可或缺。

此外，請參閱[F# 語言參考](language-reference/index.md)在 F# 中看到完整的概念性內容。
