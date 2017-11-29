---
title: "算術運算子 (F#)"
description: "深入了解 F # 程式語言中可用的算術運算子。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 75ddcfa3-564e-4382-80a3-f9da73d0f0ea
ms.openlocfilehash: 237b97c24f207b3a9b4661d66f029f1b18b8fec7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="arithmetic-operators"></a>算術運算子

本主題說明在 F # 語言中可用的算術運算子。

## <a name="summary-of-binary-arithmetic-operators"></a>二進位算術運算子的摘要
下表摘述 unboxed 整數和浮點數類型都提供二進位算術運算子。

|二元運算子|備註|
|---------------|-----|
|`+`(另外，加上)|若未選取。 數字加在一起時，可能有溢位條件和總和超過該類型支援的最大絕對值。|
|`-`(減法、 減號)|若未選取。 可能的反向溢位條件，或不帶正負號的類型都減去時，浮點值太小，表示型別時。|
|`*`（「 乘法 」、 「 時間 」）|若未選取。 可能有溢位條件時數字相乘, 和產品超過最大絕對值的型別支援。|
|`/`（除法，除以）|除數為零原因<xref:System.DivideByZeroException>整數類資料類型。 浮點類型，除數為零會提供您的特殊的浮點值`+Infinity`或`-Infinity`。 浮點數太小，表示型別時，也是產生可能的反向溢位條件。|
|`%`（模數，mod）|傳回除法運算的餘數。 結果的正負號不在第一個運算元的正負號相同。|
|`**`（乘冪的乘冪）|可能有溢位條件結果超過最大絕對值類型時。<br /><br />乘冪運算子只適用於浮點型別。|

## <a name="summary-of-unary-arithmetic-operators"></a>一元算術運算子的摘要
下表摘要說明一元算術運算子都適用於整數和浮點數的類型。


|一元運算子|備註|
|--------------|-----|
|`+`（正）|可以套用至任何算術運算式。 不會變更值的正負號。|
|`-`（否定，負數）|可以套用至任何算術運算式。 變更值的正負號。|
行為，溢位或反向溢位的整數類資料類型為循環使用。 這會導致不正確的結果。 整數的溢位是潛在嚴重的問題不會寫入帳戶為其軟體時可能造成安全性問題。 如果這是您的應用程式的問題，請考慮使用中的核取的運算子`Microsoft.FSharp.Core.Operators.Checked`。


## <a name="summary-of-binary-comparison-operators"></a>二進位比較運算子的摘要
下表顯示適用於整數和浮點類型的二進位比較運算子。 這些運算子會傳回型別的值`bool`。

浮點數應該永遠不會直接針對相等進行比較，因為 IEEE 浮點表示不支援的確切的等號比較運算。 您可以輕鬆地驗證，以進行相等檢查的程式碼的兩個數字實際上可能會有不同的位元表示方式。



|運算子|備註|
|--------|-----|
|`=`（等號比較、 等號）|這不是指派運算子。 它只適用於比較。 這是一般的運算子。|
|`>`（大於）|這是一般的運算子。|
|`<`（小於）|這是一般的運算子。|
|`>=`(大於或等於)|這是一般的運算子。|
|`<=`(小於或等於)|這是一般的運算子。|
|`<>`（不等於）|這是一般的運算子。|

## <a name="overloaded-and-generic-operators"></a>多載和一般運算子
所有本主題所討論的運算子都定義在**Microsoft.FSharp.Core.Operators**命名空間。 某些運算子會定義使用以統計方式解析的型別參數。 這表示該運算子適用於每種特定類型的個別定義。 所有一元和二元算術以及位元運算子都是此類別中。 比較運算子都是泛型，因此使用任何類型，而不只基本算術類型。 差別等位和記錄類型有它們自己的自訂實作所產生的 F # 編譯器。 類別型別使用的方法<xref:System.Object.Equals%2A>。

泛型的運算子都可自訂的。 若要自訂比較函式，請覆寫<xref:System.Object.Equals%2A>以提供您自己自訂的相等比較，然後實作<xref:System.IComparable>。 <xref:System.IComparable?displayProperty=nameWithType>介面具有單一方法<xref:System.IComparable.CompareTo%2A>方法。


## <a name="operators-and-type-inference"></a>運算子和類型推斷
在運算式中運算子的使用限制在該運算子的類型推斷。 此外，使用運算子，可以防止自動一般化，因為使用運算子表示算術類型。 如果沒有任何其他資訊，F # 編譯器會推斷`int`當做算術運算式的類型。 您可以指定另一個類型，以覆寫此行為。 因此引數類型和傳回型別`function1`下列程式碼會被推斷為`int`，但類型`function2`被推斷為`float`。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]
    
## <a name="see-also"></a>另請參閱
[符號和運算子參考](index.md)

[運算子多載](../operator-overloading.md)

[位元運算子](bitwise-operators.md)

[布林運算子](boolean-operators.md)
