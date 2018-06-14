---
title: 參數和引數 (F#)
description: '深入了解 F # 語言定義參數及支援將引數傳遞至函式、 方法和屬性。'
ms.date: 05/16/2016
ms.openlocfilehash: 319cf0e7346d498ce34e41a9993fe0160038461a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566216"
---
# <a name="parameters-and-arguments"></a>參數和引數

本主題描述針對定義參數並將引數傳遞給函式、 方法和屬性的語言支援。 其中包括如何以傳參考，以及如何定義和使用可變數目的引數的方法的相關資訊。


## <a name="parameters-and-arguments"></a>參數和引數
詞彙*參數*用來描述應提供的值的名稱。 詞彙*引數*用於提供每個參數的值。

Tuple 或局部調用的表單，或兩者的組合，可以指定參數。 您可以使用明確的參數名稱傳遞引數。 方法的參數可以指定為選擇性，並指定預設值。


## <a name="parameter-patterns"></a>參數模式
提供給函式和方法的參數，在一般情況下，模式會以空格分隔。 這表示，在一般的原則中的任何模式中所述[比對運算式](match-expressions.md)可用參數清單中的函式或成員。

方法通常會使用傳遞引數的 tuple 形式。 由於 tuple 形式比對引數會傳入的.NET 方法的方式，這就會達到從其他.NET 語言的觀點來看更清楚結果。

局部調用的表單最常搭配使用所建立的函式`let`繫結。

下列虛擬程式碼顯示 tuple 和局部調用引數的範例。

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

結合的表單可能會當某些引數的 tuple 而某些則不會。

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

其他模式也可用在參數清單中，但如果參數模式不符合所有可能的輸入，可能有不完整的相符項目在執行階段。 例外狀況`MatchFailureException`引數的值與參數清單中指定的模式不相符時產生。 參數模式允許不完整的相符項目時，編譯器會發出警告。 至少一個其他的模式是常用於參數清單，而這是萬用字元模式。 當您只想要忽略會提供任何引數時，您可以使用參數清單中的萬用字元模式。 下列程式碼說明如何使用引數清單中的萬用字元模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

萬用字元模式可能會很有用，每當您不需要在傳遞的引數，例如主要進入點至程式中，您不感興趣通常會提供以字串陣列，如下列程式碼所示的命令列引數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

偶爾會用在引數的其他模式為`as`模式，以及差別等位和作用中的模式與相關聯的識別項模式。 您可以使用單一案例差別等位模式，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

輸出如下。

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

現用模式相當適合做為參數，例如，將引數轉換成所需的格式，如下列範例所示：

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

您可以使用`as`將相符的值做為本機的值，如下列程式碼所示的模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

偶爾使用的另一種模式是離開藉由提供，做為函式的主體未命名的最後一個引數的函式、 lambda 運算式的隱含引數會立即執行模式比對。 舉例來說，這是下列程式碼行。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

此程式碼定義的函式採用的泛型清單，並傳回`true`如果清單是空的與`false`否則。 使用這類技術可讓程式碼更難閱讀。

有時候，牽涉到未完成的比對的模式會很有用，例如，如果您知道您的程式中的清單有只有三個項目，您可能會使用如下所示的模式參數清單中。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

使用具有不完整的比對的模式最，保留供快速原型化和其他暫時性使用。 編譯器會發出這類程式碼的警告。 這類模式無法涵蓋所有可能的輸入值的一般情況下，因此不是適用於應用程式開發介面的元件。

## <a name="named-arguments"></a>具名引數
方法的引數可以指定在以逗號分隔的引數清單中的位置，或它們可以傳遞至方法明確地提供的名稱，後面接著等號和傳入的值。 如果指定藉由提供名稱，可以在宣告中所使用的不同順序顯示。

具名引數可讓程式碼更容易閱讀及可調整至特定類型的 API，例如重新排列方法參數中的變更。

若是方法，只允許具名引數不適用於`let`-繫結函式、 函式值或 lambda 運算式。

下列程式碼範例示範如何使用具名引數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

在類別建構函式呼叫中，您可以使用類似的具名引數的語法來設定類別的屬性值。 下列範例會顯示此語法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

如需詳細資訊，請參閱[建構函式 （F #）](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)。

## <a name="optional-parameters"></a>選擇性參數
您可以使用參數名稱前面的問號，來指定方法的選擇性參數。 選擇性參數會被解譯為 F # 選項類型，因此您可以查詢它們，查詢的選項類型，使用的一般方式`match`運算式`Some`和`None`。 只有在成員，使用所建立的函式上不允許選擇性參數`let`繫結。

您也可以使用函式`defaultArg`，它會設定預設值是選擇性引數。 `defaultArg`函數接受選擇性參數做為第一個引數，而且預設值為第二個。

下列範例說明如何使用選擇性參數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

輸出如下。

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>傳址方式傳遞
F # 支援`byref`關鍵字可指定傳址方式傳遞參數。 這表示值的任何變更會保留在執行函式之後。 值提供給`byref`參數必須是可變動。 或者，您可以傳遞的適當類型的參考儲存格。

依用來從函式傳回一個以上的值，進而發展的.NET 語言中的參考傳遞。 在 F # 中，您可以傳回 tuple，以供此目的，或使用做為參數的可變動參考儲存格。 `byref`之互通性的.NET 程式庫主要是提供的參數。

下列範例說明使用`byref`關鍵字。 請注意，當您使用做為參數的參考儲存格，您必須建立參考儲存格一個具名值為和用來做為參數，不只是加入`ref`運算子的第一個呼叫中所示`Increment`下列程式碼。 建立參考儲存格建立基礎值的複本，因為第一次呼叫只會遞增暫時的值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

您也可以做為傳回值使用 tuple，儲存任何`out`.NET 程式庫方法中的參數。 或者，您可以將視為`out`參數做為`byref`參數。 下列程式碼範例將說明這兩種方式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>參數陣列
有時候會需要 」 定義接受任意數目的異質的型別參數的函式。 它不會實際建立無法使用的所有類型的所有可能多載的方法。 .NET 實作這類方法，透過參數陣列功能提供支援。 採用其簽章中的參數陣列的方法可供任意數目的參數使用。 參數會放入陣列。 陣列項目的類型會決定可以傳遞至函數的參數類型。 如果您定義的參數陣列`System.Object`做為項目類型，然後用戶端程式碼可以傳遞任何類型的值。

在 F # 中，參數陣列只可以定義在方法中。 它們不能在獨立函式或模組中定義的函式。

您可以使用定義的參數陣列`ParamArray`屬性。 `ParamArray`屬性只能套用至最後一個參數。

下列程式碼說明這兩個呼叫.NET 方法在 F # 具有採用參數陣列的方法會採用一個參數陣列和類型的定義。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

專案中執行時，先前的程式碼的輸出如下所示：

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>另請參閱
[成員](members/index.md)
