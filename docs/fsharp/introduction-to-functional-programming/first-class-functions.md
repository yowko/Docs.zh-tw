---
title: 一級函式
description: 瞭解第一類函式, 以及這些函式在中的函F#式程式設計中的重要功能。
ms.date: 10/29/2018
ms.openlocfilehash: 4681d32abd59cc4aade6f4cb2d062e7888bcfbbc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629721"
---
# <a name="first-class-functions"></a>一級函式

函式程式設計語言的定義特性是將函式提升至第一層的狀態。 您應該能夠使用函式來處理其他內建類型的值, 而且能夠以相當程度的工作來執行此作業。

第一類狀態的一般量值包括下列各項:

- 可以將函式系結至識別碼嗎？ 也就是說, 您可以為它們提供名稱嗎？

- 您是否可以將函數儲存在資料結構中, 例如清單中？

- 您是否可以在函式呼叫中傳遞函式做為引數？

- 您可以從函式呼叫傳回函數嗎？

最後兩個量值會定義所謂的*高階作業*或*更高*順序的函式。 較高順序的函式會接受函式做為引數, 並傳回函式做為函式呼叫的值。 這些作業支援這類函式程式設計的 mainstays, 做為對應函式和函式的組合。

## <a name="give-the-value-a-name"></a>為值命名

如果函式是第一個類別的值, 您必須能夠將它命名為, 就像您可以為整數、字串和其他內建類型命名一樣。 這在功能性程式設計文獻中稱為「將識別碼系結至值」。 F#`let <identifier> = <value>` [使用`let` ](../language-reference/functions/let-bindings.md)系結將名稱系結至值:。 下列程式碼顯示兩個範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

您可以用簡單的方式命名函式。 下列範例會藉由將識別碼`squareIt` `squareIt`系結至[lambda 運算式](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`, 來定義名為的函式。 `n`函式`squareIt`有一個參數, 它會傳回該參數的平方。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

F#提供下列更簡潔的語法, 以較少的輸入達到相同的結果。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

接下來的範例會使用第一個樣式, `let <function-name> = <lambda-expression>`以強調函式宣告與其他類型值的宣告之間的相似處。 不過, 所有命名的函式也可以使用簡潔的語法來撰寫。 其中一些範例是以這兩種方式撰寫。

## <a name="store-the-value-in-a-data-structure"></a>將值儲存在資料結構中

第一個類別的值可以儲存在資料結構中。 下列程式碼顯示將值儲存在清單和元組中的範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

為了確認儲存在元組中的函式名稱確實會評估為函式, 下列範例會使用`fst`和`snd`運算子來解壓縮元組`funAndArgTuple`中的第一個和第二個元素。 元組中的第一個專案`squareIt`是, 而第二`num`個元素是。 識別碼`num`在先前的範例中系結至整數 10, 此`squareIt`為函數的有效引數。 第二個運算式會將元組中的第一個專案套用至元組中`squareIt num`的第二個元素:。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

同樣地, 如同 identifier `num`和 integer 10 可以交替使用, 因此可以是 identifier `squareIt`和 lambda 運算式`fun n -> n * n`。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>傳遞值做為引數

如果某個值在語言中具有第一個類別的狀態, 您可以將它當做引數傳遞給函式。 例如, 通常會將整數和字串當做引數傳遞。 下列程式碼顯示在中當做引數傳遞的F#整數和字串。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

如果函式具有第一類的狀態, 您必須能夠以相同方式將它們當做引數傳遞。 請記住, 這是高階函數的第一個特性。

在下列範例中, `applyIt`函式有兩個參數: `op`和`arg`。 如果您在`op`有一個參數的函式中傳送, 並將該函數的適當引數傳給`arg`, 則函數會傳回`op`套用`arg`至的結果。 在下列範例中, 函式引數和整數引數會使用其名稱以相同的方式傳送。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

將函式當做引數傳送至另一個函式的功能, 這是功能性程式設計語言 (例如對應或篩選作業) 中常見的抽象概念。 例如, 對應作業是較高順序的函式, 它會捕捉逐步執行清單的函式所共用的計算、對每個元素執行一些動作, 然後傳回結果清單。 您可能想要遞增整數清單中的每個專案, 或每個元素的平方, 或將字串清單中的每個專案變更為大寫。 計算容易出錯的部分是逐步執行清單, 並建立要傳回之結果清單的遞迴程式。 該元件會在對應函式中捕捉。 您只需要針對特定應用程式撰寫的函式, 就是您想要個別套用至每個清單專案的函式 (新增、求等、變更案例)。 該函式會當做引數傳送至對應函數, 就像`squareIt`先前範例`applyIt`中所傳送的一樣。

F#提供大部分集合類型的對應方法, 包括[清單](../language-reference/lists.md)、[陣列](../language-reference/arrays.md)和[序列](../language-reference/sequences.md)。 下列範例使用清單。 語法為`List.map <the function> <the list>`。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

如需詳細資訊, 請參閱[清單](../language-reference/lists.md)。

## <a name="return-the-value-from-a-function-call"></a>從函式呼叫傳回值

最後, 如果函式具有語言的第一級狀態, 您就必須能夠傳回它做為函式呼叫的值, 就像您傳回其他類型 (例如整數和字串) 一樣。

下列函式呼叫會傳回整數並加以顯示。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

下列函式呼叫會傳回字串。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

下列函式呼叫 (宣告為 inline) 會傳回布林值。 顯示的值是`True`。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

將函式當做函式呼叫的值傳回的功能, 是高階函數的第二個特性。 在下列範例中, `checkFor`會定義為接受一個引數的函式, `item`並傳回新的函式做為其值。 傳回的函式會採用清單做為其`lst`引數, 並`item`在`lst`中搜尋。 如果`item`存在, 則`true`函式會傳回。 如果`item`不存在, 則`false`函式會傳回。 如上一節所示, 下列程式碼會使用提供的清單函式[list. exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)來搜尋清單。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

下列程式碼會`checkFor`使用來建立新的函式, 該函式會接受一個引數、一個清單, 並在清單中搜尋7個。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

下列範例使用中F#函式的第一個類別狀態來宣告函式, `compose`此函式會傳回兩個函數引數的組合。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> 如需更短的版本, 請參閱下一節「擴充功能」。

下列程式碼會將兩個函式`compose`當做引數傳送至, 這兩個函數都會接受相同類型的單一引數。 傳回值是新的函式, 它是兩個函數引數的組合。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> F#提供兩個運算子`<<` , `>>`也就是撰寫函式的。 例如, `let squareAndDouble = compose doubleIt squareIt`在`let squareAndDouble2 = doubleIt << squareIt`先前的範例中, 相當於。

下列範例會傳回函數做為函式呼叫的值, 以建立簡單的猜測遊戲。 若要建立遊戲, 請`makeGame`使用您想要讓其他人猜測的`target`值來呼叫。 函式的傳回值`makeGame`是接受一個引數 (猜測) 的函式, 並且會報告猜測是否正確。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

下列程式碼會`makeGame`呼叫, 並傳送`7`的`target`值。 識別碼`playGame`會系結至傳回的 lambda 運算式。 因此, `playGame`是一個函式, 它會將的`guess`值當做其一個引數。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>擴充函數

上一節中的許多範例都可以藉由利用函式宣告中F#的隱含*currying* , 更簡潔地撰寫。 Currying 是將具有一個以上參數的函式轉換成一系列內嵌函式的程式, 其中每個都有單一參數。 在F#中, 具有多個參數的函式原本就是擴充的。 例如, `compose`您可以使用三個參數, 以下列簡潔的樣式撰寫上一節中所示的。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

不過, 結果是一個參數的函式, 它會傳回一個參數的函式, 然後傳回另一個參數的函式, 如中`compose4curried`所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

您可以透過數種方式來存取此函式。 下列每個範例都會傳回並顯示18。 您可以在`compose4`任何`compose4curried`範例中, 將取代為。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

若要確認函式仍然如先前運作, 請再次嘗試原始的測試案例。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> 您可以藉由將元組中的參數括住來限制 currying。 如需詳細資訊, 請參閱[參數和引數](../language-reference/parameters-and-arguments.md)中的「參數模式」。

下列範例會使用隱含 currying 來撰寫較短的`makeGame`版本。 使用此格式時`makeGame` , 結構和傳回`game`函式的詳細資料並不明確, 但是您可以使用原始的測試案例來驗證結果是相同的。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

如需 currying 的詳細資訊, 請參閱[函數](../language-reference/functions/index.md)中的「部分引數應用程式」。

## <a name="identifier-and-function-definition-are-interchangeable"></a>識別碼和函式定義可互換

先前範例中`num`的變數名稱會評估為整數 10, 而且在其中有效的情況`num`下並不會驚訝, 10 也是有效的。 函式識別碼和其值也是如此: 可以使用函式名稱的任何位置, 都可以使用它所系結的 lambda 運算式。

下列範例會定義名`Boolean` `isNegative`為的函式, 然後使用函式的名稱和函式的定義交換。 接下來的三個範例都會傳回`False`並顯示。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

若要進一步進行, 請將系結至的`applyIt` `applyIt`值替換為。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>函數是 F 中的第一個類別值\#

前幾節中的範例會示範中F#的函式, 符合中F#第一個類別值的準則:

- 您可以將識別碼系結至函式定義。
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- 您可以將函數儲存在資料結構中。
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- 您可以傳遞函式做為引數。
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- 您可以傳回函數做為函式呼叫的值。
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

如需的詳細F#資訊, 請參閱[ F#語言參考](../language-reference/index.md)。

## <a name="example"></a>範例

### <a name="description"></a>說明

下列程式碼包含本主題中的所有範例。

### <a name="code"></a>程式碼

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>另請參閱

- [清單](../language-reference/lists.md)
- [元組](../language-reference/tuples.md)
- [函式](../language-reference/functions/index.md)
- [`let`關係](../language-reference/functions/let-bindings.md)
- [Lambda 運算式:`fun` 關鍵字](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
