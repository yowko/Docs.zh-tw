---
title: F# 的教學課程
description: '請在本教學課程中使用程式碼範例，檢查 F # 程式設計語言的一些主要功能。'
ms.date: 08/14/2020
ms.openlocfilehash: b115317e1f47ef7e18333cae4145b99e11645579
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558591"
---
# <a name="tour-of-f"></a>F 教學課程\#

瞭解 F # 的最佳方式是讀取和寫入 F # 程式碼。 本文將逐步解說 F # 語言的一些重要功能，並提供您一些可在電腦上執行的程式碼片段。 若要瞭解如何設定開發環境，請參閱 [消費者入門](get-started/index.md)。

F # 中有兩個主要概念：函數和類型。  本教學課程將著重在這兩個概念中的語言功能。

## <a name="executing-the-code-online"></a>線上執行程式碼

如果您的電腦上沒有安裝 F #，您可以在 [WebAssembly 上使用 Try F #](https://tryfsharp.fsbolero.io/)，在您的瀏覽器中執行所有範例。 Ncave 是 F # 的方言，可直接在您的瀏覽器中執行。 若要查看複寫中接下來的範例，請參閱 Ncave 複寫的左側功能表列中的 **範例，> 瞭解 F # > 導覽** 。

## <a name="functions-and-modules"></a>函數和模組

任何 F # 程式最基本的 ***部分都是*** 組織成 ***模組***的函式。  函式[會對輸入執行工作](./language-reference/functions/index.md)以產生輸出，並在[模組](./language-reference/modules.md)下組織，這些是您在 F # 中將專案分組的主要方式。  它們是使用系結定義[ `let` 的，它](./language-reference/functions/let-bindings.md)會為函式命名並定義其引數。

[!code-fsharp[BasicFunctions](~/samples/snippets/fsharp/tour.fs#L101-L133)]

`let` 系結也是您將值系結至名稱的方式，類似于其他語言的變數。  `let` 系結預設為 ***不可變*** ，這表示一旦值或函數系結至名稱之後，就無法就地變更。  這與其他語言中的變數不同， ***這是可變動的，這***表示它們的值可以在任何時間點變更。  如果您需要可變的系結，您可以使用 `let mutable ...` 語法。

[!code-fsharp[Immutability](~/samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>數位、布林值和字串

作為 .NET 語言，F # 支援存在於 .NET 中的相同基礎基本 [類型](language-reference/basic-types.md) 。

以下是如何以 F # 表示不同的數位類型：

[!code-fsharp[Numbers](~/samples/snippets/fsharp/tour.fs#L49-L68)]

以下是布林值和執行基本條件式邏輯的樣子：

[!code-fsharp[Bools](~/samples/snippets/fsharp/tour.fs#L142-L152)]

以下是基本 [字串](./language-reference/strings.md) 操作的樣子：

[!code-fsharp[Strings](~/samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Tuple

[元組](./language-reference/tuples.md) 在 F # 中是很大的交易。  它們是未命名但排序值的群組，可視為值本身。  將它們視為從其他值匯總的值。  它們有許多用途，例如方便從函式傳回多個值，或將值分組以進行某些特定的便利性。

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L186-L203)]

您也可以建立 `struct` 元組。  這些也會與 c # 7/Visual Basic 15 個元組（也就是元組）完全交互操作 `struct` ：

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L205-L218)]

請務必注意，因為 `struct` 元組是實值型別，所以無法隱含地轉換成參考元組，反之亦然。  您必須在參考和結構元組之間明確地轉換。

## <a name="pipelines-and-composition"></a>管線和組合

`|>`在 F # 中處理資料時，會廣泛使用管道運算子（例如）。 這些運算子是功能，可讓您以彈性的方式建立函式的「管線」。 下列範例會逐步解說如何利用這些運算子來建立簡單的功能管線：

[!code-fsharp[Pipelines](~/samples/snippets/fsharp/tour.fs#L227-L282)]

先前的範例使用 F # 的許多功能，包括清單處理函式、第一級函式和 [部分應用程式](./language-reference/functions/index.md#partial-application-of-arguments)。 雖然對每個概念的深入瞭解都可能更簡單，但是在建立管線時，可以清楚地使用函式來處理資料。

## <a name="lists-arrays-and-sequences"></a>清單、陣列和序列

清單、陣列和序列是 F # 核心程式庫中的三個主要集合類型。

[清單](./language-reference/lists.md) 是相同類型之專案的已排序、不可變的集合。  它們是單一連結的清單，這表示它們是用來進行列舉，但如果很大，則會有不佳的隨機存取和串連選項。  這與其他熱門語言中的清單相較之下，通常不會使用單一連結的清單來表示清單。

[!code-fsharp[Lists](~/samples/snippets/fsharp/tour.fs#L309-L359)]

[陣列](./language-reference/arrays.md) 是具有相同類型之專案的固定 *大小、可* 變動集合。  它們支援快速隨機存取專案，而且比 F # 清單更快，因為它們只是連續的記憶體區塊。

[!code-fsharp[Arrays](~/samples/snippets/fsharp/tour.fs#L368-L407)]

[序列](./language-reference/sequences.md) 是元素的邏輯系列，全都是相同的類型。  這些是比清單和陣列更一般的型別，可將您的「view」成任何邏輯系列元素。  它們也有可能是 ***延遲***的，這表示只有在需要時，才可以計算元素。

[!code-fsharp[Sequences](~/samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>遞迴函式

處理集合或元素的順序通常是以 F # 中的 [遞迴](./language-reference/functions/index.md#recursive-functions) 來完成。  雖然 F # 支援迴圈和命令式程式設計，但最好是遞迴，因為這樣可以更輕鬆地確保正確性。

> [!NOTE]
> 下列範例會利用運算式的模式比對 `match` 。  本文稍後將說明此基礎結構。

[!code-fsharp[RecursiveFunctions](~/samples/snippets/fsharp/tour.fs#L461-L500)]

F # 也有 Tail 呼叫優化的完整支援，這是將遞迴呼叫優化，使其與迴圈結構一樣快的方式。

## <a name="record-and-discriminated-union-types"></a>記錄和區分聯集類型

記錄和等位類型是 F # 程式碼中使用的兩個基本資料類型，通常是在 F # 程式中表示資料的最佳方式。  雖然這會讓它們類似于其他語言的類別，但其中一個主要差異在於它們具有結構化相等的語法。  這表示它們是「原生」可比較且相等的相等，只要檢查其中一個是否等於另一個。

[記錄](./language-reference/records.md) 是已命名值的匯總，具有選擇性成員 (例如) 方法。  如果您熟悉 c # 或 JAVA，則這些應該類似于 Poco 或 Pojo，只是結構相等且較不會發生。

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L507-L559)]

您也可以將記錄表示為結構。 這是使用屬性來完成的 `[<Struct>]` ：

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L561-L568)]

差異聯集[ (du) ](./language-reference/discriminated-unions.md)是可能是數個名稱的表單或案例的值。  儲存在類型中的資料可以是數個相異值的其中一個。

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L575-L631)]

您也可以使用 Du 作為 *單一案例*的差異聯集，以協助您在基本類型上進行領域模型化。  通常會使用時間、字串和其他基本型別來代表某個東西，因此會提供特定意義。  不過，僅使用資料的基本標記法可能會導致錯誤地指派不正確的值！  將每一種類型的資訊表示為不同的單一案例聯集，可以在此案例中強制執行正確性。

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L633-L654)]

如上一個範例所示，若要取得單一案例差異聯集的基礎值，您必須明確地將它解除包裝。

此外，Du 也支援遞迴定義，可讓您輕鬆地表示樹狀結構和原本遞迴的資料。  例如，以下是您可以使用和函式來表示二進位搜尋樹狀結構的方式 `exists` `insert` 。

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L656-L683)]

由於 Du 可讓您以資料類型代表樹狀結構的遞迴結構，因此在此遞迴結構上運作相當簡單，而且保證正確性。  在模式比對中也支援，如下所示。

此外，您可以 `struct` 使用屬性將 du 表示為 s `[<Struct>]` ：

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L685-L696)]

不過，在這種情況下，有兩個重要事項要牢記在心：

1. 無法遞迴定義結構 DU。
2. 結構 DU 的每個案例都必須有唯一的名稱。

無法遵循上述動作將會導致編譯錯誤。

## <a name="pattern-matching"></a>模式比對

[模式](./language-reference/pattern-matching.md) 比對是 f # 語言功能，可讓您在 f # 類型上操作的正確性。  在上述範例中，您可能已注意到很多 `match x with ...` 語法。  此結構可讓編譯器瞭解資料類型的「圖形」，以強制您在使用資料類型時，透過所謂的完整模式比對來考慮所有可能的情況。  這在正確性方面相當強大，而且可以用來「增益」，這通常是執行時間在編譯時間方面的顧慮。

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L705-L742)]

您可能已經注意到，這是使用 `_` 模式。  這就是所謂的 [萬用字元模式](./language-reference/pattern-matching.md#wildcard-pattern)，也就是說「我不在意什麼東西」的方法。  雖然很方便，但您可以不小心略過詳盡的模式比對，如果您不小心使用，則無法再從編譯時期大規模地規範獲益 `_` 。  當您在模式比對時不在意某些分解型別的片段，或是當您在模式比對運算式中列舉所有有意義的案例時，最好使用它。

在下列範例中， `_` 當剖析作業失敗時，會使用案例。

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L744-L762)]

[現用模式](./language-reference/active-patterns.md) 是另一種功能強大的結構，可搭配模式比對使用。  它們可讓您將輸入資料分割成自訂表單，並在模式比對呼叫位置分解它們。  它們也可以參數化，因此可讓您將資料分割定義為函數。  擴充先前的範例以支援現用模式看起來像這樣：

[!code-fsharp[ActivePatterns](~/samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>選用類型

差異聯集類型的一個特殊案例是選項類型，因此它是 F # 核心程式庫的一部分。

[選項類型](./language-reference/options.md) 是代表兩種情況之一的類型：值，或完全沒有。  在任何情況下，其值可能會或可能不會由特定作業產生。  然後，這會強制您考慮這兩種情況，使其成為編譯時期的考慮，而不是執行時間的考慮。  這些通常用於用來代表「nothing」的 Api `null` ，因此 `NullReferenceException` 在許多情況下都不需要擔心。

[!code-fsharp[Options](~/samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>測量單位

F # 類型系統的一項獨特功能，就是能夠透過測量單位提供數值常值的內容。

[測量單位](./language-reference/units-of-measure.md) 可讓您將數數值型別與某個單位（例如計量）建立關聯，並讓函式對單位（而非數值常值）執行工作。  如此一來，編譯器就可以驗證在特定內容下傳遞的數值常數值型別是否合理，從而消除與該工作類型相關聯的執行階段錯誤。

[!code-fsharp[UnitsOfMeasure](~/samples/snippets/fsharp/tour.fs#L817-L842)]

F # 核心程式庫會定義許多 SI 單位類型和單位轉換。  若要深入瞭解，請參閱 [fsharp.core. UnitSystems. Unitsymbols.s 命名空間](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitsymbols.html)。

## <a name="classes-and-interfaces"></a>類別和介面

F # 也有 .NET 類別、 [介面](./language-reference/interfaces.md)、 [抽象類別](./language-reference/abstract-classes.md)、 [繼承](./language-reference/inheritance.md)等的完整支援。

[類別](./language-reference/classes.md) 是代表 .net 物件的類型，其 [成員](./language-reference/members/index.md)可以有屬性、方法和事件。

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L845-L880)]

定義泛型類別也非常簡單。

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L883-L908)]

若要執行介面，您可以使用 `interface ... with` 語法或 [物件運算式](./language-reference/object-expressions.md)。

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>要使用的類型

類別、記錄、差別聯集和元組的存在會導致重要問題：您應該使用哪一項？  就像大部分的生活一樣，答案都取決於您的情況。

元組很適合用來傳回函式的多個值，並使用特定值的隨選匯總作為值本身。

記錄是來自元組的「逐步執行」，具有命名標籤和選擇性成員的支援。  它們很適合用於透過您的程式傳輸中資料的低人員表示。  因為它們的結構相等，所以很容易與比較使用。

差別聯集有許多用途，但核心優點是能夠搭配模式比對使用，以考慮資料可擁有的所有可能「圖形」。  

類別很適合許多原因，例如當您需要表示資訊，同時也將該資訊系結至功能時。  根據經驗法則，當您有在概念上系結至某些資料的功能時，使用類別和麵向物件程式設計的原則是一項很大的好處。  與 c # 和 Visual Basic 交互操作時，類別也是慣用的資料類型，因為這些語言幾乎都是使用類別。

## <a name="next-steps"></a>後續步驟

現在您已看過語言的一些主要功能，接下來您應該準備好撰寫您的第一個 F # 程式！  查看 [消費者入門](get-started/index.md) ，瞭解如何設定您的開發環境並撰寫一些程式碼。

後續學習的步驟可以是您喜歡的任何內容，但我們建議使用 [F # 中的功能程式設計](./introduction-to-functional-programming/index.md) ，以熟悉核心功能程式設計概念。  在 F # 中建立強大的程式時，這些都是不可或缺的。

此外，請參閱 [f # 語言參考](./language-reference/index.md) ，以查看 f # 的完整概念內容集合。
