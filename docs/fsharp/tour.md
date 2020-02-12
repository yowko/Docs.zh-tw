---
title: F# 的教學課程
description: 在本教學課程中使用程式碼F#範例，檢查程式設計語言的一些重要功能。
ms.date: 02/09/2020
ms.openlocfilehash: ac2eef40e2dbc494e41a9760f0a70edb0f7ce399
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124568"
---
# <a name="tour-of-f"></a>F\# 的教學課程

瞭解的最佳方式F#是讀取和撰寫F#程式碼。 這篇文章將做為流覽F#語言的一些重要功能，並提供您可在電腦上執行的一些程式碼片段。 若要瞭解如何設定開發環境，請參閱[消費者入門](get-started/index.md)。

有兩個主要概念F#：函數和類型。  本教學課程將強調屬於這兩個概念的語言功能。

## <a name="executing-the-code-online"></a>線上執行程式碼

如果您的電腦F#上未安裝，您可以使用[WebAssembly 上的 Try F# ](https://tryfsharp.fsbolero.io/)來執行瀏覽器中的所有範例。 Fable 是直接在您F#的瀏覽器中執行的方言。 若要查看複寫中接下來的範例，請參閱**範例 > 瞭解F#**  Fable 複寫左側功能表列中的 > 導覽。

## <a name="functions-and-modules"></a>函數和模組

任何F#程式中最基本的部分都是組織成***模組***的***功能***。  函式[會對輸入執行工作](./language-reference/functions/index.md)以產生輸出，而且會在[模組](./language-reference/modules.md)底下加以組織，這是您在中F#分組專案的主要方式。  它們是使用[`let`](./language-reference/functions/let-bindings.md)系結所定義，這會提供函式名稱並定義其引數。

[!code-fsharp[BasicFunctions](~/samples/snippets/fsharp/tour.fs#L101-L133)]

`let` 系結也是您將值系結至名稱的方式，類似于其他語言中的變數。  `let` 系結預設為***不可變***，這表示一旦值或函式系結至名稱，就無法就地變更。  這與其他語言中的變數相反，***這是可變動的，這***表示它們的值可以在任何時間點變更。  如果您需要可變的系結，您可以使用 `let mutable ...` 語法。

[!code-fsharp[Immutability](~/samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>數位、布林值和字串

當做 .NET 語言， F#支援存在於 .net 中[的相同基礎基本型](language-reference/basic-types.md)別。

以下是各種數位類型的表示方式F#：

[!code-fsharp[Numbers](~/samples/snippets/fsharp/tour.fs#L49-L68)]

以下是布林值和執行基本條件式邏輯的樣子：

[!code-fsharp[Bools](~/samples/snippets/fsharp/tour.fs#L142-L152)]

以下是基本[字串](./language-reference/strings.md)操作的樣子：

[!code-fsharp[Strings](~/samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Tuple

[元組](./language-reference/tuples.md)是很大的F#交易。  它們是未命名但已排序值的群組，可視為值本身。  請將它們想成是從其他值匯總而來的值。  它們有許多用途，例如方便地從函式傳回多個值，或將值分組以進行特定的便利性。

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L186-L203)]

您也可以建立 `struct` 元組。  這些也會與 c # 7/Visual Basic 15 元組完全互通，這也是 `struct` 元組：

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L205-L218)]

請務必注意，因為 `struct` 元組是實值型別，所以無法隱含地轉換成參考元組，反之亦然。  您必須在參考和結構元組之間明確轉換。

## <a name="pipelines-and-composition"></a>管線和組合

在中F#處理資料時，會廣泛使用管線運算子（例如 `|>`）。 這些運算子是函數，可讓您以彈性的方式建立函式的「管線」。 下列範例會逐步解說如何利用這些運算子來建立簡單的功能管線：

[!code-fsharp[Pipelines](~/samples/snippets/fsharp/tour.fs#L227-L282)]

先前的範例使用了的許多功能F#，包括清單處理函式、第一級函式和[部分應用程式](./language-reference/functions/index.md#partial-application-of-arguments)。 雖然深入瞭解每個概念可能會變得很重要，但請清楚瞭解在建立管線時，函數可以如何用來處理資料。

## <a name="lists-arrays-and-sequences"></a>清單、陣列和順序

清單、陣列和序列是F#核心程式庫中的三個主要集合類型。

[清單](./language-reference/lists.md)是相同類型之元素的已排序、不可變集合。  它們是單一連結的清單，這表示它們是用來進行列舉，但如果很大，則不適合用于隨機存取和串連。  相較于其他熱門語言的清單，通常不會使用單一連結的清單來表示清單。

[!code-fsharp[Lists](~/samples/snippets/fsharp/tour.fs#L309-L359)]

[陣列](./language-reference/arrays.md)是一種固定大小 *、可*變動的元素集合，屬於相同類型的專案。  它們支援快速隨機存取專案，而且速度比F#清單快，因為它們只是連續的記憶體區塊。

[!code-fsharp[Arrays](~/samples/snippets/fsharp/tour.fs#L368-L407)]

[序列](./language-reference/sequences.md)是專案的邏輯系列，全都是相同的類型。  這些是比清單和陣列更一般的類型，可以將您的「視圖」放入任何邏輯專案序列中。  它們也會脫穎而出，因為它們可能是***延遲***的，也就是說，只有在需要時才會計算元素。

[!code-fsharp[Sequences](~/samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>遞迴函式

在中F#，處理集合或元素的序列通常是透過[遞迴](./language-reference/functions/index.md#recursive-functions)來完成。  雖然F#具有迴圈和命令式程式設計的支援，但建議您這麼做，因為更容易保證正確性。

> [!NOTE]
> 下列範例會透過 `match` 運算式來使用模式比對。  本文稍後將討論此基本結構。

[!code-fsharp[RecursiveFunctions](~/samples/snippets/fsharp/tour.fs#L461-L500)]

F#也具有 Tail 呼叫優化的完整支援，這種方式可將遞迴呼叫優化，使其如同迴圈結構一樣快速。

## <a name="record-and-discriminated-union-types"></a>記錄和區分聯集類型

記錄和聯集類型是在F# F#程式碼中使用的兩種基本資料類型，通常是在程式中表示資料的最佳方式。  雖然這會使它們類似于其他語言中的類別，但其中一個主要差異在於它們有結構相等的語義。  這表示它們是「原生」的可比較和相等，只需檢查其中一個是否等於另一個。

[記錄](./language-reference/records.md)是已命名值的匯總，具有選擇性成員（例如方法）。  如果您熟悉C#或 JAVA，則這些內容應該類似于 Poco 或 pojo，只是結構化的相等和較少的儀式。

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L507-L559)]

您也可以將記錄表示為結構。 這會透過 `[<Struct>]` 屬性來完成：

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L561-L568)]

[區分等位（DUs）](./language-reference/discriminated-unions.md)是可能是一些命名表單或案例的值。  儲存在類型中的資料可以是數個相異值的其中一個。

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L575-L631)]

您也可以使用 DUs 作為*單一案例的區分等位*，以協助透過基本型別進行領域模型化。  通常會使用字串和其他基本型別來代表某個專案，因此會提供特定意義。  不過，只使用資料的基本標記法可能會造成錯誤地指派不正確的值！  將每一種類型的資訊表示為不同的單一案例聯集，可以在此案例中強制執行正確性。

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L633-L654)]

如上述範例所示，若要取得單一案例的區分等位中的基礎值，您必須明確地將它解除包裝。

此外，DUs 也支援遞迴定義，可讓您輕鬆地表示樹狀結構和原本就遞迴的資料。  例如，以下說明如何使用 `exists` 和 `insert` 函數來表示二進位搜尋樹狀目錄。

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L656-L683)]

由於 DUs 可讓您以資料類型表示樹狀結構的遞迴結構，因此在此遞迴結構上操作十分簡單，並保證正確性。  模式比對也支援，如下所示。

此外，您可以使用 `[<Struct>]` 屬性，將 DUs 表示為 `struct`s：

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L685-L696)]

不過，在這麼做時，有兩個重要的事項要牢記在心：

1. 結構 DU 無法以遞迴方式定義。
2. 結構 DU 的每一個案例都必須有唯一的名稱。

如果無法遵循上述動作，將會導致編譯錯誤。

## <a name="pattern-matching"></a>模式比對

[模式](./language-reference/pattern-matching.md)比對是F#一種語言功能，可讓您F#在類型上運作。  在上述範例中，您可能已注意到相當多的 `match x with ...` 語法。  此結構可讓編譯器（可以瞭解資料類型的「圖形」）在使用資料類型時，透過所謂的完整模式比對來強制您考慮所有可能的情況。  這在正確性方面非常強大，而且可以應變用來「增益」通常會在編譯時期發生的執行時間問題。

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L705-L742)]

您可能已經注意到，使用 `_` 模式。  這就是所謂的[萬用字元模式](./language-reference/pattern-matching.md#wildcard-pattern)，這是一個指出「我不在意什麼東西」的方法。  雖然方便，但如果您不小心使用 `_`，您可以不小心略過完整的模式比對，而不再受益于編譯時期實行原則。  在模式比對時，如果您不在意分解類型的特定片段，或當您在模式比對運算式中列舉了所有有意義的案例時，最好使用此方式。

在下列範例中，當剖析作業失敗時，會使用 `_` 案例。

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L744-L762)]

[現用模式](./language-reference/active-patterns.md)是另一個搭配模式比對使用的強大結構。  它們可讓您將輸入資料分割成自訂表單，並在模式比對呼叫位置分解它們。  它們也可以參數化，因此可讓將資料分割定義為函數。  展開先前的範例以支援現用模式看起來像這樣：

[!code-fsharp[ActivePatterns](~/samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>選擇性類型

區分等位類型的一種特殊案例是選項類型，這對它是F#核心程式庫的一部分很有用。

[選項類型](./language-reference/options.md)是代表兩個案例之一的類型：值，或完全沒有。  在任何情況下，如果值不一定是由特定作業所產生，就會使用它。  這會強制您將這兩種情況都列入考慮，使其成為編譯時期的考慮，而不是執行時間的顧慮。  這些通常用於 `null` 用來代表「無」的 Api，因此在許多情況下都不需要擔心 `NullReferenceException`。

[!code-fsharp[Options](~/samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>測量單位

型別系統的F#一項獨特功能，就是能夠透過測量單位提供數值常值的內容。

[測量單位](./language-reference/units-of-measure.md)可讓您建立數數值型別與單位（例如計量）的關聯，並讓函式在單位上執行工作，而不是數值常值。  這可讓編譯器確認傳入的數值常數值型別在特定內容之下有意義，因而排除與該類型工作相關聯的執行階段錯誤。

[!code-fsharp[UnitsOfMeasure](~/samples/snippets/fsharp/tour.fs#L817-L842)]

F#核心程式庫會定義許多 SI 單位類型和單位轉換。  若要深入瞭解，請參閱[Microsoft.FSharp.Data.UnitSystems.SI 命名空間](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d)。

## <a name="classes-and-interfaces"></a>類別和介面

F#也具有 .NET 類別、[介面](./language-reference/interfaces.md)、[抽象類別](./language-reference/abstract-classes.md)、[繼承](./language-reference/inheritance.md)等的完整支援。

[類別](./language-reference/classes.md)是代表 .net 物件的類型，可以有屬性、方法和事件做為其[成員](./language-reference/members/index.md)。

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L845-L880)]

定義泛型類別也非常簡單。

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L883-L908)]

若要執行介面，您可以使用 `interface ... with` 語法或[物件運算式](./language-reference/object-expressions.md)。

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>要使用的類型

類別、記錄、區分等位和元組的存在會導致一個重要的問題：您應該使用哪一項？  就像生活中的大部分專案一樣，答案取決於您的情況。

元組非常適合用來從函式傳回多個值，並使用值的臨機操作匯總作為值本身。

記錄是來自元組的「逐步執行」，具有選擇性成員的命名標籤和支援。  它們非常適合用來透過您的程式進行傳輸中的資料的低人。  因為它們的結構相等，所以比較容易使用。

區分聯集有許多用途，但核心優點是能夠將它們與模式比對搭配使用，以考慮資料可擁有的所有可能「圖形」。  

類別非常適用于許多因素，例如當您需要表示資訊，以及將該資訊系結至功能時。  根據經驗法則，當您具有概念上與某些資料系結的功能時，使用類別和麵向物件程式設計的原則是一個很大的好處。  當與C#和 Visual Basic 交互操作時，類別也是慣用的資料類型，因為這些語言幾乎都是使用類別。

## <a name="next-steps"></a>後續步驟

既然您已瞭解此語言的一些主要功能，您應該已準備好撰寫您的第一個F#程式！  查看[消費者入門](get-started/index.md)以瞭解如何設定您的開發環境，並撰寫一些程式碼。

進一步瞭解的後續步驟可以是您喜歡的任何方式，但我們建議您[在中F#進行功能程式設計的簡介](./introduction-to-functional-programming/index.md)，以熟悉核心功能程式設計概念。  在中F#建立健全的程式時，這些都是不可或缺的。

此外，請參閱[ F#語言參考](./language-reference/index.md)，以在上F#查看完整的概念內容集合。
