---
title: 函式 (F#)
description: '深入了解以 F # 和 F # 如何支援常見的函式程式設計建構函式。'
ms.date: 05/16/2016
ms.openlocfilehash: 717eba7e69398048d229173e07ccc376797171bb
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326435"
---
# <a name="functions"></a>函式

函式是所有程式設計語言的基礎程式執行單位。 如同其他語言，F# 函式有名稱、可以有參數並且接受引數，而且也有主體。 F# 也支援函式程式設計建構，例如將函式視為值、在運算式中使用不具名函式、組合函式以形成新函式、局部調用函式，以及透過部分套用函式引數的隱含定義函式。

您可以使用 `let` 關鍵字定義函式，若是遞迴函式，則可以使用 `let rec` 關鍵字組合來定義函式。

## <a name="syntax"></a>語法

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>備註

*function-name* 表示函式的識別項。 *parameter-list* 由以空格分隔的連續參數所組成。 您可以指定每個參數的明確類型，如＜參數＞一節中所述。 若未指定特定的引數類型，編譯器會嘗試從函式主體推斷類型。 *function-body* 由運算式組成。 函式主體通常是由組合運算式組成，其中包含數個會產生最終運算式作為傳回值的運算式。 *return-type* 是選擇性項目，包含後面接著類型的冒號。 若您沒有明確指定傳回值的類型，則編譯器會從最終運算式判斷傳回型別。

簡單的函式定義如下所示：

```fsharp
let f x = x + 1
```

在上述範例中，函式名稱為 `f`，引數是類型為 `int` 的 `x`，函式主體為 `x + 1`，而傳回值的類型為 `int`。

函式可以標記為 `inline`。 如需 `inline` 的資訊，請參閱[內嵌函式](../functions/inline-functions.md)。

## <a name="scope"></a>範圍

在模組範圍以外的任何範圍層級，重複使用值或函式名稱並非錯誤。 若重複使用名稱，後面宣告的名稱會遮蔽前面宣告的名稱。 不過，在模組中的最上層範圍，名稱必須是唯一名稱。 例如，下列程式碼出現在模組範圍時會產生錯誤，但在函式內時則不會：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

但是，下列程式碼在任何範圍層級都可以使用：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a>參數

參數名稱必須列於函式名稱後面。 您可以指定參數的類型，如下列範例所示：

```fsharp
let f (x : int) = x + 1
```

若您指定類型，請將它放在參數名稱之後，並且以冒號來分隔類型與名稱。 若您省略此參數的類型，編譯器便會推斷參數類型。 例如，在下列函式定義中，引數 `x` 經推斷為 `int` 類型，因為 1 是 `int` 類型 。

```fsharp
let f x = x + 1
```

不過，編譯器會嘗試將函式盡可能推斷成為泛型。 例如，請注意下列程式碼：

```fsharp
let f x = (x, x)
```

函式會從任何類型的一個引數建立元組。 因為沒有指定類型，所以函式可以與任何引數類型搭配使用。 如需詳細資訊，請參閱[自動產生](../generics/automatic-generalization.md)。

## <a name="function-bodies"></a>函式主體

函式主體可以包含區域變數和函式的定義。 這類變數和函式是在目前函式主體的範圍內，而不是在主體以外。 啟用輕量型語法選項時，必須使用縮排來表示定義是在函式主體中，如下列範例所示：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

如需詳細資訊，請參閱[程式碼格式化方針](../code-formatting-guidelines.md)和[詳細語法](../verbose-syntax.md)。

## <a name="return-values"></a>傳回值

編譯器會使用函式主體中的最終運算式，來判斷傳回值和類型。 編譯器可能會從先前的運算式推斷最終運算式的類型。 在上節示範的 `cylinderVolume` 函式中，`pi` 的類型是從常值 `3.14159` 的類型經判斷為 `float`。 編譯器會使用 `pi` 的類型，判斷運算式 `h * pi * r * r` 的類型為 `float`。 因此，函式的整體傳回型別為 `float`。

若要明確指定傳回值，請撰寫如下的程式碼：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

撰寫如上所示的程式碼時，編譯器會將 **float** 套用至整個函式。若您也要將它套用至參數類型，請使用下列程式碼：

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>呼叫函式

您可以指定函式名稱，後面接著空格，再接著以空格分隔的任何引數來呼叫函式。 例如，若要呼叫函式 **cylinderVolume** 並將結果指派給值 **vol**，您可以撰寫下列程式碼：

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>部分套用引數

若您提供的引數數目比指定的數目更少，則必須建立需要其餘引數的新函式。 這個處理引數的方法稱為「局部調用」，是 F# 這類函式程式設計語言的特色。 例如，假設您要使用兩種大小的管子，其中一個半徑為 **2.0**，另一個半徑為 **3.0**。 您可以建立會判斷管子容量的函式，如下所示：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

接著，視需要為兩個不同大小的各種管子長度提供其他引數：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a>遞迴函式

「遞迴函式」是會自我呼叫的函式。 您必須在 **let** 關鍵字後面指定 **rec** 關鍵字來使用遞迴函式。 請從函式主體中叫用遞迴函式，就像叫用任何函式呼叫一樣。 下列遞迴函式會計算*n*<sup>th</sup> Fibonacci 數字。 Fibonacci 數字序列自古聞名，此序列中的每個連續數字都是前兩個數字的總和。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

若不謹慎撰寫遞迴函式，而且也不了解特殊技巧 (例如累計值和接續符號的用法)，某些遞迴函式便可能會使程式堆疊溢位，或導致執行時沒有效率。

## <a name="function-values"></a>函式值

在 F# 中，所有函式都視為值，而實際上它們稱為「函式值」。 由於函式都是值，因此可以作為其他函式的引數，或在其他會用到這些值的內容中使用。 以下是接受函式值作為引數的函式範例：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

您可以使用 `->` 語彙基元來指定函式值的類型。 在此語彙基元左邊是引數的類型，右邊則是傳回值。 在上述範例中，`apply1` 函式會接受 `transform` 函式作為引數，其中 `transform` 是接受整數並傳回另一個整數的函式。 在下列範例程式碼中，會示範 `apply1` 的用法：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

在上述程式碼執行之後，`result` 的值會是 101。

多個引數是以連續 `->` 語彙基元分隔，如下列範例所示：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

結果為 200。

## <a name="lambda-expressions"></a>Lambda 運算式

「Lambda 運算式」是不具名函式。 在上述範例中，您可以使用 Lambda 運算式，而不定義具名函式 **increment** 和 **mul**，如下所示：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

您可以透過 `fun` 關鍵字定義 Lambda 運算式。 Lambda 運算式類似函式定義，但是它使用 `->` 語彙基元來分隔引數清單與函式主體，而不是 `=` 語彙基元。 如同一般函式定義，您可以推斷或明確指定引數類型，而 Lambda 運算式的傳回型別是從主體中最後一個運算式的類型來推斷。 如需詳細資訊，請參閱 [Lambda 運算式：`fun` 關鍵字](../functions/lambda-expressions-the-fun-keyword.md)。

## <a name="function-composition-and-pipelining"></a>函式組合和管線

F# 中的函式可以從其他函式組合。 兩個函式 **function1** 和 **function2** 會組合成另一個函式，表示先套用 **function1**，接著套用 **function2**：

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

結果為 202。

管線可讓函式呼叫鏈結在一起成為連續作業。 管線運作方式如下：

```fsharp
let result = 100 |> function1 |> function2
```

結果同樣是 202。

組合運算子會採用兩個函式，並傳回一個函式。相較之下，管線運算子則採用一個函式與一個引數，並傳回一個值。 下列程式碼範例可透過示範函式簽章和使用方式的不同，顯示管線和組合運算子之間的差異。

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a>多載函式

您可以多載類型的方法，但不是函式的方法。 如需詳細資訊，請參閱[方法](../members/methods.md)。

## <a name="see-also"></a>另請參閱

- [值](../values/index.md)
- [F# 語言參考](../index.md)
