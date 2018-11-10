---
title: 第一級函式
description: 深入了解第一級函式以及它們的重要函式程式設計的方式F#。
ms.date: 10/29/2018
ms.openlocfilehash: 1459049c9c1c77f4eefd2a83945335b33ca22ab9
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "50744629"
---
# <a name="first-class-functions"></a>第一級函式

功能性程式設計語言的一項定義特性是提高至頂級狀態的函式。 您應該能夠執行的函式，任何您可以與其他內建類型值，並能夠這樣做相當高的投入時間。

下面是一般的量值的第一等狀態：

- 您是否可以識別項繫結函式？ 也就是你可以提供這些名稱？

- 您可以儲存函式中的資料結構，例如清單中？

- 您可以做為引數，函式呼叫中傳遞函式？

- 您可以從函式呼叫傳回的函式？

最後兩個量值定義所謂*高階 operations*或*較高順序函式*。 較高順序函式會接受做為引數的函式，並傳回做為值的函式呼叫的函式。 這些作業都支援這類從函式程式設計，做為對應函式和函式的組合。

## <a name="give-the-value-a-name"></a>指定值的名稱

如果函式為第一級的值，您必須能夠加以命名，就如同您可以命名整數、 字串和其他內建類型。 這被指在功能性程式設計文獻中做為繫結至值的識別項。 F# 會使用[`let`繫結](../language-reference/functions/let-bindings.md)繫結到值的名稱： `let <identifier> = <value>`。 下列程式碼顯示兩個範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

您可以命名輕鬆地為函式。 下列範例會定義名為函式`squareIt`繫結識別碼`squareIt`要[lambda 運算式](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`。 函式`squareIt`有一個參數， `n`，並傳回該參數的平方。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

F# 提供下列更簡潔的語法，來達到相同的結果，少打一些字。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

請依照下列大部分的範例會使用第一個樣式， `let <function-name> = <lambda-expression>`，以強調函式的宣告和其他類型之值的宣告之間的相似性。 不過，所有具名函式也可以撰寫使用簡潔的語法。 有些範例會以兩種方式。

## <a name="store-the-value-in-a-data-structure"></a>將值儲存在資料結構

第一級的值可以儲存在資料結構。 下列程式碼顯示於清單和 tuple 中儲存值的範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

若要確認函式名稱儲存在事實上確實會評估為函式，下列範例會使用`fst`並`snd`運算子來擷取 tuple 的第一個和第二個項目`funAndArgTuple`。 Tuple 中的第一個元素是`squareIt`，而第二個元素是`num`。 識別項`num`在上述範例中為整數 10 的有效引數繫結`squareIt`函式。 第二個運算式套用至 tuple 中第二個元素的 tuple 中的第一個項目： `squareIt num`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

同樣地，只是做為識別碼`num`而且可以是整數 10 交替使用，因此可以識別項`squareIt`lambda 運算式和`fun n -> n * n`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>將值傳遞做為引數

如果某個值有一種語言中的第一等狀態，您可以做為引數傳遞至函式。 比方說，常會傳遞做為引數的整數和字串。 下列程式碼顯示整數和 F# 中的引數傳遞的字串。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

如果函式的第一等狀態，您必須能夠將它們傳遞為引數中，相同的方式。 請記住，這是較高順序函式的第一個特性。

在下列範例中，函式`applyIt`有兩個參數，`op`和`arg`。 如果您傳送具有一個參數的函式中`op`和適當的引數的函式`arg`，此函數會傳回套用的結果`op`至`arg`。 在下列範例中，函式引數和整數引數會傳送相同的方式，使用其名稱。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

能夠將函式做為引數傳送至另一個函式是功能性程式設計語言的詳細資訊，例如對應或篩選作業中的通用抽象概念的基礎。 對應作業，比方說，是較高順序函式可擷取共用的逐步執行清單，執行某個動作，每個項目，然後傳回結果的清單的函式的計算。 您可能想要遞增的整數，清單中的每個項目或正方形每個項目，或變更為大寫的字串清單中的每個項目。 計算出錯部分是遞迴程序的逐步說明的清單，並建置一份要傳回的結果。 對應函式中擷取該部分。 您只需要撰寫特定的應用程式是您想要個別套用至每個清單項目函式 （新增、 number、 變更大小寫）。 函式會傳送做為引數以對應的函式，就如同`squareIt`傳送至`applyIt`在上述範例中。

F# 提供對應方法的大部分集合型別，包括[列出](../language-reference/lists.md)，[陣列](../language-reference/arrays.md)，並[序列](../language-reference/sequences.md)。 下列範例會使用清單。 語法是`List.map <the function> <the list>`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

如需詳細資訊，請參閱 <<c0> [ 列出](../language-reference/lists.md)。

## <a name="return-the-value-from-a-function-call"></a>從函式呼叫中傳回值

最後，如果函式語言中第一等狀態，您必須是能夠傳回做為值的函式呼叫，就像您傳回其他類型，例如整數和字串。

下列函式呼叫會傳回整數，並加以顯示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

下列函式呼叫傳回的字串。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

下列函式呼叫，宣告內嵌及傳回布林值。 顯示的值是`True`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

傳回做為值的函式呼叫的函式的功能是較高順序函式的第二個特性。 在下列範例中，`checkFor`定義為接受一個引數的函式`item`，並傳回新的函式，做為其值。 傳回的函式接受清單作為其引數， `lst`，並搜尋`item`在`lst`。 如果`item`已存在，則函數會傳回`true`。 如果`item`不存在，則函數會傳回`false`。 上一節中，下列程式碼會使用提供的清單函式[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)，以搜尋清單。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

下列程式碼會使用`checkFor`來建立新的函式採用一個引數，清單中，並搜尋 7 在清單中。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

下列範例使用在 F# 第一級函式的狀態，宣告函式， `compose`，傳回兩個函式引數的組合。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]

>[!NOTE]
即使較短的版本，請參閱下列區段中，「 Curried 函式。 」

下列程式碼會傳送兩個函式做為引數`compose`，這兩個的其中採用相同型別的單一引數。 傳回的值是新的函式所組成的兩個函式引數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]

>[!NOTE]
F# 提供兩個運算子`<<`和`>>`，撰寫函式。 例如，`let squareAndDouble2 = doubleIt << squareIt`相當於`let squareAndDouble = compose doubleIt squareIt`在上述範例中。

傳回做為值的函式呼叫的函式的下列範例會建立簡單的猜測遊戲。 若要建立的遊戲，呼叫`makeGame`值與想要其他人猜出傳入`target`。 函式的傳回值`makeGame`是採用一個引數 （猜測），並報告猜測是否正確的函式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

下列程式碼會呼叫`makeGame`，值傳送`7`如`target`。 識別項`playGame`繫結至傳回的 lambda 運算式。 因此，`playGame`是採用一個引數為值的函式`guess`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>局部調用函式

許多在上一節中的範例藉由運用隱含可以更精確撰寫*調用*F# 函式宣告中。 調用是轉換成一系列的內嵌函式，其中每一個具有單一參數的多個參數的函式的程序。 在 F# 中，有多個參數的函式原本就是局部調用。 比方說，`compose`上一節可以撰寫下列簡潔樣式，使用三個參數中所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

不過，結果會傳回一個參數，依序傳回的一個參數，另一個函式的函式中所示的一個參數的函式`compose4curried`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

您可以存取數種方式中的此函式。 每個下列範例會傳回，並顯示 18。 您可以取代`compose4`與`compose4curried`任何範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

若要確認函式仍可如以前一樣，再試一次原始的測試案例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]

>[!NOTE]
您可以限制對住 tuple 中的參數。 如需詳細資訊，請參閱 < 參數模式 」 中[參數和引數](../language-reference/parameters-and-arguments.md)。

下列範例會使用隱含調用撰寫的較短`makeGame`。 詳細方式`makeGame`建構並傳回`game`函式是較不明確的格式如下，但您可以確認使用原始的測試案例的結果都會相同。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

更多對的詳細資訊，請參閱 「 部分應用程式的引數 」，在[函式](../language-reference/functions/index.md)。

## <a name="identifier-and-function-definition-are-interchangeable"></a>是可互換的識別項和函式定義

變數的名稱`num`在上一個範例會評估為 10 的整數，而且毫無意外地，其中`num`是有效的 10 也是有效。 函式識別項和其值也是一樣： 隨處可用的函式名稱，它繫結的 lambda 運算式可以使用。

下列範例會定義`Boolean`函式，呼叫`isNegative`，然後交替使用 函式的名稱和函式的定義。 接下來的三個範例都會傳回並顯示`False`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

若要它進一步採取步驟，以取代值，`applyIt`繫結至如`applyIt`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>函式是 F# 第一級值\#

在先前章節中的範例將示範 F# 函式滿足的準則中 F# 第一級值：

- 您可以將識別項繫結至函式定義。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- 您可以在資料結構儲存函式。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- 您可以傳遞函式做為引數。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- 您可以傳回函式的函式呼叫的值。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

如需 F# 的詳細資訊，請參閱[F# 語言參考](../language-reference/index.md)。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列程式碼包含本主題中的所有範例。

### <a name="code"></a>程式碼

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>另請參閱

- [清單](../language-reference/lists.md)
- [元組](../language-reference/tuples.md)
- [函式](../language-reference/functions/index.md)
- [`let` 繫結](../language-reference/functions/let-bindings.md)
- [Lambda 運算式：`fun`關鍵字](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
