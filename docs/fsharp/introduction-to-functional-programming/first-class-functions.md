---
title: 一級函式
description: '瞭解第一級函式，以及它們對於 F # 中的函式程式設計有何重要性。'
ms.date: 10/29/2018
ms.openlocfilehash: 1dc8eae1655187282f05bf4e9501ecc8a17deba8
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810907"
---
# <a name="first-class-functions"></a>一級函式

函式程式設計語言的定義特性是將函式提升為第一級狀態的功能。 您應該能夠使用函式來處理其他內建類型的值，而且能夠以相當程度的投入量來進行。

第一個類別狀態的典型量值包括下列各項：

- 您可以將函式系結至識別碼嗎？ 也就是說，您可以為它們命名嗎？

- 您可以將函數儲存在資料結構中，例如清單中？

- 您可以在函式呼叫中傳遞函式作為引數嗎？

- 您可以從函式呼叫傳回函數嗎？

最後兩個量值會定義所謂的 *高階作業* 或 *更高順序*的函式。 高階函式接受函數做為引數，並傳回函式作為函式呼叫的值。 這些作業支援將函數設計支柱為對應函式和函式組合。

## <a name="give-the-value-a-name"></a>為值命名

如果函式是第一級的值，您必須能夠命名它，就像您可以命名整數、字串和其他內建類型一樣。 這在功能程式設計文獻中稱為將識別碼系結至值。 F # 使用系結將名稱系[ `let` 結至值](../language-reference/functions/let-bindings.md)： `let <identifier> = <value>` 。 下列程式碼顯示兩個範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

您可以輕鬆地將函數命名。 下列範例會定義名為的函式，該函式會將識別碼系結 `squareIt` `squareIt` 至 [lambda 運算式](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n` 。 函式 `squareIt` 有一個參數， `n` 而它會傳回該參數的平方。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

F # 提供下列更簡潔的語法，以較少的輸入來達成相同的結果。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

接下來的範例會使用第一個樣式， `let <function-name> = <lambda-expression>` 以強調函式宣告和其他類型值的宣告之間的相似之處。 不過，所有命名的函式也可以使用精簡的語法來撰寫。 其中一些範例是以這兩種方式撰寫的。

## <a name="store-the-value-in-a-data-structure"></a>將值儲存在資料結構中

第一個類別的值可以儲存在資料結構中。 下列程式碼顯示在清單和元組中儲存值的範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

為了確認儲存在元組中的函式名稱確實是評估為函式，下列範例會使用 `fst` 和 `snd` 運算子來解壓縮元組中的第一個和第二個元素 `funAndArgTuple` 。 元組中的第一個專案是 `squareIt` ，而第二個元素是 `num` 。 `num`在先前的範例中，識別碼會系結至整數10，此為函數的有效引數 `squareIt` 。 第二個運算式會將元組中的第一個專案套用至元組中的第二個元素： `squareIt num` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

同樣地，如同識別碼 `num` 和整數10可以交替使用，因此可以使用識別碼 `squareIt` 和 lambda 運算式 `fun n -> n * n` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>傳遞值做為引數

如果某個值在語言中具有第一級的狀態，您可以將它當作引數傳遞給函式。 例如，通常會將整數和字串當作引數傳遞。 下列程式碼顯示在 F # 中做為引數傳遞的整數和字串。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

如果函式具有頂級狀態，您必須能夠以同樣的方式將它們當作引數傳遞。 請記住，這是較高順序函式的第一個特性。

在下列範例中，函數 `applyIt` 有兩個參數： `op` 和 `arg` 。 如果您在有一個參數的函式中傳送，並將函 `op` 式的適當引數傳送至，函數會傳回套用 `arg` 至的結果 `op` `arg` 。 在下列範例中，函式引數和整數引數都會以相同的方式傳送，方法是使用它們的名稱。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

將函式作為引數傳送至另一個函式的能力，是以函式程式設計語言（例如地圖或篩選作業）的常見抽象概念為基礎。 例如，對應作業是較高階的函式，它會捕捉逐步執行清單的函式所共用的計算、對每個元素執行某些動作，然後傳回結果清單。 您可能會想要遞增整數清單中的每個專案，或每個元素的平方，或是將字串清單中的每個專案變更為大寫。 計算容易出錯的部分是遞迴程式，它會逐步執行此清單，並建立要傳回的結果清單。 該元件是在對應函式中所捕捉。 您必須為特定應用程式撰寫的所有專案，都是您想要個別套用至每個清單專案的函式， (新增、求大小寫) 。 該函式會以引數的形式傳送至對應函式，就像 `squareIt` `applyIt` 在先前的範例中所傳送的一樣。

F # 為大部分的集合類型（包括 [清單](../language-reference/lists.md)、 [陣列](../language-reference/arrays.md)和 [序列](../language-reference/sequences.md)）提供對應方法。 下列範例使用清單。 語法是 `List.map <the function> <the list>`。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

如需詳細資訊，請參閱 [清單](../language-reference/lists.md)。

## <a name="return-the-value-from-a-function-call"></a>從函式呼叫傳回值

最後，如果函式在語言中具有第一級的狀態，您就必須能夠將它傳回做為函式呼叫的值，就像您傳回其他類型（例如整數和字串）一樣。

下列函式呼叫會傳回整數並加以顯示。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

下列函式呼叫會傳回字串。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

下列函式呼叫（宣告為 inline）會傳回布林值。 顯示的值為 `True` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

以函式呼叫的值傳回函式的能力，是較高順序函數的第二個特性。 在下列範例中， `checkFor` 定義為採用一個引數的函式， `item` 並傳回新的函式作為其值。 傳回的函式會接受清單作為其引數， `lst` 並 `item` 在中搜尋 `lst` 。 如果 `item` 存在，則函數會傳回 `true` 。 如果 `item` 不存在，則函數會傳回 `false` 。 如上一節所示，下列程式碼會使用提供的清單函式 [list. exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists)來搜尋清單。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

下列程式碼會使用來建立新的函式，該函式 `checkFor` 會接受一個引數、一個清單，並在清單中搜尋7。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

下列範例會使用 F # 中函式的第一個類別狀態來宣告函式， `compose` 此函式會傳回兩個函式引數的組合。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> 如需更短的版本，請參閱下一節「擴充函數」。

下列程式碼會將兩個函式作為引數傳送至，這兩個函式 `compose` 都會採用相同類型的單一引數。 傳回值是新的函式，這是兩個函式引數的組合。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> F # 提供兩個運算子， `<<` 以及 `>>` 撰寫函數。 例如， `let squareAndDouble2 = doubleIt << squareIt` `let squareAndDouble = compose doubleIt squareIt` 在上一個範例中相當於。

下列範例會傳回函式作為函式呼叫的值，以建立簡單的猜測遊戲。 若要建立遊戲，請 `makeGame` 使用您希望他人猜測的值來呼叫 `target` 。 函式的傳回值 `makeGame` 是接受一個引數 (猜測) 的函式，並報告猜測是否正確。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

下列程式碼會呼叫，並傳送 `makeGame` 的值 `7` `target` 。 識別碼 `playGame` 會系結至傳回的 lambda 運算式。 因此，是一種函式，它會將的 `playGame` 值作為其一個引數 `guess` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>擴充函數

您可以利用 F # 函式宣告中的隱含 *currying* ，更簡潔地撰寫上一節中的許多範例。 Currying 是一種程式，可將具有多個參數的函式轉換為一系列的內嵌函式，其中每個函式都有單一參數。 在 F # 中，有多個參數的函式在本質上是局部的。 例如，在 `compose` 上一節中，您可以使用三個參數，以下列簡潔的樣式來撰寫。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

不過，結果是一個參數的函式，它會傳回一個參數的函式，而後者接著會傳回一個參數的另一個函式，如下所示 `compose4curried` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

您可以透過數種方式來存取此函式。 下列每個範例都會傳回並顯示18。 您可以 `compose4` 使用 `compose4curried` 中的任何範例取代。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

若要確認函式的運作方式仍與之前相同，請再次嘗試原來的測試案例。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> 您可以藉由將元組中的參數括住來限制 currying。 如需詳細資訊，請參閱 [參數和引數](../language-reference/parameters-and-arguments.md)中的「參數模式」。

下列範例會使用隱含 currying 來寫入較短的版本 `makeGame` 。 結構和傳回函式的詳細資料 `makeGame` `game` ，在此格式中較不明確，但您可以使用原始測試案例來確認結果是相同的。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

如需 currying 的詳細資訊，請參閱函 [式中的](../language-reference/functions/index.md)「部分引數應用程式」。

## <a name="identifier-and-function-definition-are-interchangeable"></a>識別碼和函式定義是可互換的

`num`先前範例中的變數名稱會評估為整數10，而且如果 `num` 有效，則10也是有效的。 函式識別碼和其值也是如此：可以使用函式名稱的任何位置，都可以使用它所系結的 lambda 運算式。

下列範例會定義名為的函式 `Boolean` `isNegative` ，然後使用函數的名稱和函式的定義。 接下來的三個範例都會傳回並顯示 `False` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

若要進一步進行，請將系結的值取代為 `applyIt` `applyIt` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>函數是 F 中的第一個類別值\#

上述各節中的範例會示範 F # 中的函式符合 F # 中第一個類別值的準則：

- 您可以將識別碼系結至函式定義。
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- 您可以將函數儲存在資料結構中。
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- 您可以將函數當作引數傳遞。
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- 您可以傳回函數作為函式呼叫的值。
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

如需 F # 的詳細資訊，請參閱 [f # 語言參考](../language-reference/index.md)。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列程式碼包含本主題中的所有範例。

### <a name="code"></a>程式碼

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>另請參閱

- [清單](../language-reference/lists.md)
- [元組](../language-reference/tuples.md)
- [函式](../language-reference/functions/index.md)
- [`let` 綁定](../language-reference/functions/let-bindings.md)
- [Lambda 運算式： `fun` 關鍵字](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
