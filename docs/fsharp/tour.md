---
title: 'F # 教學課程'
description: '檢查部份 F # 程式語言中的程式碼範例使用此教學課程的主要功能。'
author: cartermp
ms.author: phcart
ms.date: 02/28/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 6821c74827b928cdd0c5aff101be4f9103986e3e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="tour-of-f"></a>F # 教學課程 #

若要了解 F # 的最佳方式是讀取和寫入 F # 程式碼。  這篇文章會做為瀏覽某些索引鍵的 F # 語言功能，並提供您一些您可以在您的電腦執行的程式碼片段。  若要深入了解設定開發環境，請參閱[入門](tutorials/getting-started/index.md)。

F # 中有兩個主要概念： 函式和類型。  此教學課程會強調可分為下列兩個概念的語言功能。

## <a name="functions-and-modules"></a>函式和模組

任何 F # 程式的最基本的片段都***函式***組織成***模組***。  [函式](language-reference/functions/index.md)為產生輸出，輸入上執行的工作和組織在[模組](language-reference/modules.md)，這是主要的方式分組在 F # 中的項目。  定義使用[`let`繫結](language-reference/functions/let-bindings.md)，其中指定函式的名稱，並且定義其引數。

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` 繫結也是您如何結合其值為名稱，類似於其他語言中的變數。  `let` 繫結是***不可變***根據預設，也就是說，一旦值或函式繫結的名稱，它無法變更就地。  這是相較於其他語言，也就是變數***可變動***，這表示它們的值可以變更在任何時間點的時間。  如果您需要的可變動的繫結時，您可以使用`let mutable ...`語法。

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>數字、 布林值和字串

為.NET 語言，F # 支援相同的基礎[基本型別](language-reference/primitive-types.md).NET 中存在。

以下是如何各種數值類型表示 F # 中：

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

以下是布林值，並執行基本的條件式邏輯看起來像：

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

以下是何種 basic[字串](language-reference/strings.md)操作看起來像：

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Tuple

[Tuple](language-reference/tuples.md)是 F # 中是大問題。  它們是未命名的但已排序，可以視為值本身的值的群組。  將它們視為彙總從其他值的值。  它們有許多用途，例如輕鬆地從函式傳回多個值或群組的一些特定便利的值。

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

為準，F # 4.1，您也可以建立`struct`tuple。  這些也與交互操作完全也是 C# 7/Visual 基本 15 tuple `struct` tuple:

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

請務必注意因為`struct`tuple 是實值類型，它們無法隱含地轉換成參考 tuple，反之亦然。  您必須明確轉換之間的參考和結構的 tuple。

## <a name="pipelines-and-composition"></a>管線和撰寫

使用管線運算子 (`|>`， `<|`， `||>`， `<||`， `|||>`， `<|||`) 和運算子組合 (`>>`和`<<`) 會在處理 F # 中的資料時廣泛地使用。  這些運算子都可讓您以有彈性的方式建立 「 管線 」 的函式的函式。  下列範例逐步解說如何您無法利用這些運算子來建置簡單的功能性管線。

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L300)]

上述範例中所使用的 F # 中，包括清單處理函式，第一級函式，許多功能和[部分應用程式](language-reference/functions/index.md#partial-application-of-arguments)。  雖然深入了解這些概念的每個可以成為稍微進階，應該很清楚如何輕鬆地函式可用來建立管線時，處理資料。

## <a name="lists-arrays-and-sequences"></a>清單、 陣列和順序

清單、 陣列和順序是 F # 核心程式庫中的三種主要集合類型。

[列出](language-reference/lists.md)是相同型別的項目已排序、 不可變的集合。  它們是單向連結清單中，這表示它們一定會用於列舉型別，但不佳的適合隨機存取和串連很大時。  這相較於其他常用的語言，通常不會使用單向連結清單來表示清單中的清單。

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[陣列](language-reference/arrays.md)是固定大小*可變動*相同類型的元素的集合。  它們支援快速隨機存取項目，且會比 F # 列出因為它們是只連續記憶體區塊。

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[序列](language-reference/sequences.md)是邏輯的一連串的項目全為相同的類型。  這些是更廣泛的類型，比清單和陣列，在您 「 檢視 」 到任何邏輯系列的項目。  它們也突顯因為它們是***延遲***，這表示只在需要時，可以計算的項目。

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>遞迴函式

處理集合或序列的項目通常是與[遞迴](language-reference/functions/index.md#recursive-functions)F # 中。  雖然 F # 具有迴圈及命令式程式設計支援，但遞迴，因為很容易就能保證正確性。

>[!NOTE]
下列範例會使用模式比對透過`match`運算式。  這個基本建構涵蓋在本文稍後。

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F # 也具有完整支援 Tail 呼叫最佳化，這是一種最佳化遞迴呼叫，以使其速度會一樣快迴圈建構。

## <a name="record-and-discriminated-union-types"></a>記錄和差別聯集類型

記錄和等位型別在 F # 程式碼，使用兩種基本資料類型，通常代表資料在 F # 程式中的最佳方式。  雖然這使其與類別類似其他語言中，其主要差異是它們具有結構相等語意。  這表示它們是 「 原生 」 可比較而且十分簡單的等號比較-只檢查其中一個是否等於其他。

[記錄](language-reference/records.md)會與選擇性成員 （例如方法） 的具名值的彙總。  如果您熟悉 C# 或 Java，然後這些應該可以類似 POCOs 或 POJOs-只是具有結構相等和較低的儀式。

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

您也可以為準，F # 4.1，代表做為記錄`struct`s。  做法是使用`[<Struct>]`屬性：

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[差別等位 (DUs)](language-reference/discriminated-unions.md)可能是具名的表單或案例數的值。  類型中儲存的資料可以是數個相異值的其中一個。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

您也可以使用為 DUs*單一案例差別等位*，以協助進行網域模型基本類型。  經常、 字串和其他基本型別用來代表某樣東西，且都因此各有特定意義。  不過，使用資料的基本表示法可能會導致錯誤地指派值不正確 ！  代表每一種不同的單一案例聯集的資訊，可以強制在此案例中的正確性。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

如上述範例所示，若要取得基礎值中單一案例差別聯集，您必須明確 unwrap。

此外，DUs 也支援遞迴定義可讓您輕易地表示樹狀結構和原本就是遞迴的資料。  例如，以下是可以代表具有的二進位搜尋樹狀目錄的方式`exists`和`insert`函式。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

DUs 允許您將代表遞迴結構的樹狀結構中的資料類型，因為此遞迴結構上運作很直接，而且可保證正確性。  它也支援在模式比對，如下所示。

此外，您可以在這裡表示為 DUs`struct`與`[<Struct>]`屬性：

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

不過，有兩個重要的事情，若要這麼做時請記住以下幾點：

1. 法蘭西結構不能以遞迴方式定義。
2. 結構法蘭西必須有它的情況下的每個唯一的名稱。

遵循上述的失敗會導致編譯錯誤。

## <a name="pattern-matching"></a>模式比對

[模式比對](language-reference/pattern-matching.md)是 F # 語言功能，可讓 F # 類型上運作的正確性。  在上述範例中，您可能注意到相當多的`match x with ...`語法。  此建構可讓編譯器，可了解"shape"的資料類型，以強制要求您使用透過已知的資料類型為徹底的模式比對時，考量所有可能案例。  這是非常強大的正確性，並巧妙可用來 「 增益 」 通常會產生編譯成執行階段問題。

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L739)]

您也可以使用縮寫`function`建構用於模式比對，這非常有用，當您撰寫函式，這會導致使用[部分應用程式](language-reference/functions/index.md#partial-application-of-arguments):

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L741-L759)]

您可能已注意到的項目，就是使用`_`模式。  這稱為[萬用字元模式](language-reference/pattern-matching.md#wildcard-pattern)，這是一種說 「 我不在意的項目為何 」。  雖然方便，您可以不小心略過詳盡的模式比對，如果您不小心使用，不會再受益編譯時期強制`_`。  最好使用當您不在意分解類型的某些部分已經列舉所有有意義的情況下在模式比對運算式時，當模式比對或最後一個子句。

[現用模式](language-reference/active-patterns.md)是另一個功能強大的建構函式來使用搭配模式比對。  它們可讓您輸入的資料分割成自訂表單，將其分解在模式比對呼叫站台。  它們可以也是參數化，如此可讓資料分割定義為函式。  展開上一個範例是為了支援現用模式看起來像這樣：

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L761-L783)]

## <a name="optional-types"></a>選用的類型

差別聯集類型的其中一個特殊案例是選項類型，會很有用，它是 F # 核心程式庫的一部分。

[選項類型](language-reference/options.md)是型別代表兩個案例的其中一個： 一個值，或不完全。  它用在任何情況下，值可能會或可能不會造成從特定作業的位置。  這會強制您帳戶的這兩種情況，因此是編譯時期問題，而不是執行階段問題。  這些通常用於應用程式開發介面其中`null`用來代表"nothing"相反地，因此不需要擔心`NullReferenceException`在許多情況下。

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L791-L811)]

## <a name="units-of-measure"></a>測量單位

F # 型別系統的一項獨特功能是能夠提供透過測量單位的數值常值的內容。

[測量單位](language-reference/units-of-measure.md)可讓您將為單位，例如公尺來測量，數值類型產生關聯，並具有函式上執行的工作單位，而不是數值常值。  這可讓編譯器驗證傳入的數值常值的類型，在某些環境下的意義上，因此減少執行階段錯誤與該類型的工作相關聯。

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L818-L839)]

F # 核心程式庫定義許多 SI 單位類型和單位轉換。  若要進一步了解，請參閱[Microsoft.FSharp.Data.UnitSystems.SI 命名空間](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d)。

## <a name="classes-and-interfaces"></a>類別和介面

F # 也有.NET 類別的完整支援[介面](language-reference/interfaces.md)，[抽象類別](language-reference/abstract-classes.md)，[繼承](language-reference/inheritance.md)，依此類推。

[類別](language-reference/classes.md)是代表.NET 物件的型別且可以包含屬性、 方法和事件中的當做其[成員](language-reference/members/index.md)。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L848-L877)]

定義泛型類別也是非常簡單。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L884-L905)]

若要實作介面，您可以使用`interface ... with`語法或[物件運算式](language-reference/object-expressions.md)。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L912-L931)]

## <a name="which-types-to-use"></a>若要使用哪些類型

類別、 記錄、 差別等位和 Tuple 的存在會導致重要的問題： 您應該使用它？  大部分的所有項目在生活中，例如答案需視您的情況。

Tuple 非常適合用來從函式，傳回多個值，並用作值本身的特定彙總的值。

記錄會 「 逐步向上 」 從具有名為標籤和支援選擇性成員的 Tuple。  它們很適合用於資料傳輸中執行您的程式的低儀式表示法。  具有結構相等，因為它們是容易使用的比較。

差別等位有許多用途，但核心優點是能夠利用它們搭配模式比對所有可能 「 圖形 」 可以有資料的帳戶。  

類別最適合用於大量的原因，例如當您需要代表資訊也連接該功能的資訊。  根據經驗法則，當您擁有的功能可在概念上繫結至部分資料，使用類別和 Object-Oriented 程式設計的原則是一大優點。  類別也是慣用的資料類型與 C# 和 Visual Basic 中，搭配使用時為這些語言幾乎所有項目使用的類別。

## <a name="next-steps"></a>後續步驟

既然您已看過的一些主要功能的語言，您應該準備好開始撰寫第一個 F # 程式 ！  簽出[入門](tutorials/getting-started/index.md)以了解如何設定您的開發環境，並撰寫一些程式碼。

接下來的步驟來學習更多可以是任何您喜歡，但我們建議您[函式做為第一級值](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)-->取得熟悉核心功能的程式設計概念。  這些會在建置穩固的應用程式在 F # 中不可或缺。

此外，請參閱[F # 語言參考](language-reference/index.md)若要查看在 F # 的概念性內容的完整集合。
