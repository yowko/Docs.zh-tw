---
title: 當做優先使用值的函式 (F#)
description: '了解如何提高函式，才能在 F # 程式語言中的第一級狀態。'
ms.date: 05/16/2016
ms.openlocfilehash: cccff5fcf9de150da26422f80cae032ddf21014c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566661"
---
# <a name="functions-as-first-class-values"></a>當做優先使用值的函式

功能性程式設計語言的定義特性在於函式第一級的狀態來提高的權限。 您應該能夠處理函式，無論您可以與其他內建類型值，並能夠這樣做比較投入時間的程度。

一般量值的第一級的狀態包括下列各項：

- 您是否可以識別項繫結函式？ 也就是可以您讓它們名稱嗎？

- 您可以儲存函式中的資料結構，例如清單中？

- 您可以做為引數函式呼叫中傳遞函式？

- 您可以從函式呼叫傳回函式？

最後兩個量值定義所謂*高階 operations*或*較高順序函式*。 較高順序函式會接受做為引數的函式，並傳回做為值的函式呼叫的函式。 這些作業支援功能性程式設計，做為對應函式和函式的複合這類細節。


## <a name="give-the-value-a-name"></a>指定值的名稱

如果函式的第一級的值，您必須能夠加以命名，就如同您可以將整數、 字串和其他內建型別名稱。 這被指做為識別項繫結值的功能性程式設計文獻中。 F # 使用[`let`繫結](../language-reference/functions/let-bindings.md)繫結至值的名稱： `let <identifier> = <value>`。 下列程式碼顯示兩個範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

您可以命名輕易地函式。 下列範例會定義名為函式`squareIt`繫結的識別項`squareIt`至[lambda 運算式](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`。 函式`squareIt`具有一個參數， `n`，它會傳回該參數的平方和。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

F # 提供下列更簡潔的語法，來達到相同的結果與輸入較少。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

請依照下列大部分的範例會使用第一個樣式， `let <function-name> = <lambda-expression>`，以強調函式的宣告和其他類型的值的宣告之間的相似性。 不過，所有具名函式也可以寫入使用簡潔的語法。 部分範例是以兩種方式撰寫。


## <a name="store-the-value-in-a-data-structure"></a>將值儲存在資料結構

第一級的值可以儲存在資料結構。 下列程式碼會顯示於清單和 tuple 中儲存值的範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

若要確認，儲存在 tuple 中的函式名稱事實上確實會評估函式，下列範例會使用`fst`和`snd`運算子的第一個和第二個項目擷取 tuple `funAndArgTuple`。 Tuple 中的第一個元素是`squareIt`而第二個項目是`num`。 識別項`num`整數 10，有效的引數，如前一個範例中會繫結`squareIt`函式。 第二個運算式套用至 tuple 中第二個元素的 tuple 中的第一個項目： `squareIt num`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

同樣地，只是做為識別碼`num`而且可以是整數 10 交替使用，因此可以識別項`squareIt`和 lambda 運算式`fun n -> n * n`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a>將值傳遞做為引數

如果某個值有一種語言中的第一級的狀態，您可以做為引數傳遞至函式。 例如，常會傳遞整數和字串當做引數。 下列程式碼顯示整數和字串做為 F # 中的引數傳遞。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

如果函式的第一級的狀態，您必須是能夠將其做為引數傳遞方式相同。 請記住，這是較高順序函式的第一個特性。

在下列範例中，函式`applyIt`有兩個參數，`op`和`arg`。 如果您傳送的其中一個參數的函式中`op`和適當的引數的函式的`arg`，此函數會傳回套用的結果`op`至`arg`。 在下列範例中，函式引數和此整數引數會傳送相同的方式，使用它們的名稱。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

能夠將函式做為引數傳送至另一個函式做為功能性程式設計語言的詳細資訊，例如對應或篩選作業中的通用抽象概念。 對應 」 作業，例如，是較高順序函式可擷取共用逐步執行清單，執行某個動作，每個項目，然後傳回結果的清單的函式所計算。 您可能想遞增每個項目清單中的整數，或方形每個項目，或將改成大寫的字串清單中的每個項目。 計算的容易發生錯誤的部分是遞迴程序，透過的清單，該步驟，並建置要傳回的結果的清單。 對應函式中擷取的組件。 您只需要撰寫特定的應用程式是您想要個別套用至每個清單項目函式 （加入、 number、 變更大小寫）。 函式會傳送做為引數以對應的函式，就如同`squareIt`傳送至`applyIt`前一個範例中。

F # 提供的對應方法大部分的集合型別，包括[列出](../language-reference/lists.md)，[陣列](../language-reference/arrays.md)，和[序列](../language-reference/sequences.md)。 下列範例會使用清單。 語法是`List.map <the function> <the list>`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

如需詳細資訊，請參閱[列出](../language-reference/lists.md)。

## <a name="return-the-value-from-a-function-call"></a>從函式呼叫傳回值

最後，如果函式具有第一級的狀態，在語言中，您必須是能夠將其傳回做為值的函式呼叫，就如同您傳回其他型別，包括像是整數和字串。

下列函式呼叫會傳回整數，並加以顯示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

下列函式呼叫傳回的字串。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

下列函式呼叫，宣告為內嵌，會傳回布林值。 顯示的值是`True`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

傳回做為值的函式呼叫的函式的能力是第二個特性的較高順序函式。 在下列範例中，`checkFor`定義為接受一個引數的函式`item`，並傳回新的函式做為其值。 傳回的函式接受清單做為其引數， `lst`，並搜尋`item`中`lst`。 如果`item`已存在，則函數會傳回`true`。 如果`item`不存在，則函數會傳回`false`。 下列程式碼會提供的清單的函式，使用如前一節所示[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)，若要在清單中搜尋。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

下列程式碼會使用`checkFor`來建立新的函式採用一個引數清單，以及搜尋 7 清單中。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

下列範例使用在 F # 第一級函式的狀態，宣告函式， `compose`，傳回兩個函式引數的組合。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
即使較短的版本，請參閱下一節 < Curried 函數 >。


下列程式碼會傳送兩個函式做為引數`compose`，這兩個的其中採用相同類型的單一引數。 傳回值是新的函式所組成的兩個函式引數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
F # 提供兩個運算子，`<<`和`>>`，撰寫函式。 例如，`let squareAndDouble2 = doubleIt << squareIt`相當於`let squareAndDouble = compose doubleIt squareIt`前一個範例中。

下列範例會傳回做為值的函式呼叫的函式會建立簡單的猜測遊戲。 若要建立的遊戲，請呼叫`makeGame`值想要其他人猜出針對傳入`target`。 函式的傳回值`makeGame`是採用一個引數 （猜測），並報告猜測是否正確的函數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

下列程式碼會呼叫`makeGame`，傳送值`7`如`target`。 識別項`playGame`繫結至傳回的 lambda 運算式。 因此，`playGame`是採用一個引數為值的函式`guess`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a>局部調用函式

許多上一節中的範例藉由運用隱含可以更精確地撰寫*對*F # 函式宣告中。 對是轉換成一系列的內嵌函式，每一個都有一個單一參數的多個參數的函式的程序。 在 F # 中，原本就調用函式具有一個以上的參數。 例如，`compose`前一節可以撰寫下列精簡樣式，有三個參數中所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

不過，結果會傳回一個參數，依序傳回一個參數，另一個函式的函式中所示的一個參數的函式`compose4curried`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

您可以存取此函式數種方式。 每一個下列範例會傳回並顯示 18。 您可以取代`compose4`與`compose4curried`中任何的範例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

若要確認，函式仍能運作與以前一樣，原始的測試案例再試一次。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
您可以限制對住 tuple 的參數。 如需詳細資訊，請參閱 < 參數模式 」 中[參數和引數](../language-reference/parameters-and-arguments.md)。

下列範例會使用隱含對要寫入的較短`makeGame`。 詳細資料請參閱`makeGame`建構及傳回`game`函式是較不明確的格式，但您可以使用原始的測試案例結果是相同檢查。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

對的詳細資訊，請參閱 「 部分應用程式的引數 」，在[函式](../language-reference/functions/index.md)。


## <a name="identifier-and-function-definition-are-interchangeable"></a>是可互換的識別項和函式定義
變數的名稱`num`中上一個範例會評估為整數 10，而且不會對該位置`num`是有效，10 也是有效的。 函式識別項和其值也是一樣： 隨處可用的函式名稱，它繫結的 lambda 運算式可以使用。

下列範例會定義`Boolean`函式，呼叫`isNegative`，然後使用函式的名稱和函式定義交換使用。 接下來三個範例全部都會傳回並顯示`False`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

若要提升其進一步，以取代值的`applyIt`就繫結至`applyIt`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>函式是在 F # 第一級值 #

上一節的範例將示範在 F # 中的函式符合在 F # 第一級值的準則：

- 您可以將識別項繫結至函式定義。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- 您可以在資料結構儲存函式。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- 您可以將函式傳遞做為引數。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- 您可以傳回函式做為函式呼叫的值。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

如需 F # 的詳細資訊，請參閱[F # 語言參考](../language-reference/index.md)。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列程式碼包含本主題中的所有範例。

### <a name="code"></a>程式碼

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a>另請參閱

[清單](../language-reference/lists.md)

[元組](../language-reference/tuples.md)

[函式](../language-reference/functions/index.md)

[`let` 繫結](../language-reference/functions/let-bindings.md)

[Lambda 運算式：`fun`關鍵字](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
