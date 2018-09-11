---
title: 算術運算子 (F#)
description: '深入了解可在 F # 程式設計語言中的算術運算子。'
ms.date: 04/04/2018
ms.openlocfilehash: 008aa84b8736bb3a734ce8bb9713d34c17f1b76e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271844"
---
# <a name="arithmetic-operators"></a>算術運算子

本主題描述可在 F # 語言中的算術運算子。

## <a name="summary-of-binary-arithmetic-operators"></a>二進位的算術運算子的摘要

下表摘要說明適用於 unboxed 整數和浮點數類型的二進位算術運算子。

|二元運算子|備註|
|---------------|-----|
|`+` (此外，再加上)|未選取。 數字加在一起時，可能的溢位狀況和總和超過類型支援的最大絕對值。|
|`-` (減法、 減號)|未選取。 可能的反向溢位條件，或不帶正負號的類型減去時，浮點值太小，表示由型別時。|
|`*` （「 乘法 」、 「 時間 」）|未選取。 可能的溢位時個數字相乘的條件與產品超過類型支援的最大絕對值。|
|`/` （除法，除以）|除數為零的原因<xref:System.DivideByZeroException>對於整數型別。 浮點類型，除數為零會提供您特殊的浮點數值`+Infinity`或`-Infinity`。 浮點數太小，表示由型別時，也會產生可能的反向溢位條件。|
|`%` （其餘部分，rem）|傳回除法運算的餘數。 結果的正負號是第一個運算元的正負號相同。|
|`**` （冪指數）|可能的溢位條件結果超過最大絕對值類型時。<br /><br />乘冪運算子只適用於浮點類型。|

## <a name="summary-of-unary-arithmetic-operators"></a>一元算術運算子的摘要

下表摘要說明適用於整數和浮點數類型的一元算術運算子。

|一元運算子|注意|
|--------------|-----|
|`+` （正）|可以套用至任何算術運算式。 不會變更值的正負號。|
|`-` （負號、 負）|可以套用至任何算術運算式。 變更值的正負號。|
行為，溢位或反向溢位的整數類資料類型是循環使用。 這會導致不正確的結果。 整數的溢位是潛在嚴重的問題可能造成安全性問題時不會寫入帳戶為其軟體。 如果這是您的應用程式的問題，請考慮使用中檢查的運算子`Microsoft.FSharp.Core.Operators.Checked`。

## <a name="summary-of-binary-comparison-operators"></a>二進位比較運算子的摘要

下表顯示適用於整數和浮點數類型的二進位比較運算子。 這些運算子會傳回型別的值`bool`。

浮點數應該永遠不會直接比較相等，因為 IEEE 浮點表示不支援的確切的等號比較運算。 您可以輕鬆地驗證要等於所檢查的程式碼的兩個數字實際上可能會有不同的位元表示法。

|運算子|注意|
|--------|-----|
|`=` （等號比較，equals）|這不是指派運算子。 它僅用於比較。 這是一般的運算子。|
|`>` （大於）|這是一般的運算子。|
|`<` （小於）|這是一般的運算子。|
|`>=` (大於或等於)|這是一般的運算子。|
|`<=` (小於或等於)|這是一般的運算子。|
|`<>` （不等於）|這是一般的運算子。|

## <a name="overloaded-and-generic-operators"></a>多載，並使用一般運算子

中所定義的所有本主題中討論的運算子**Microsoft.FSharp.Core.Operators**命名空間。 某些運算子使用以統計方式解析的型別參數所定義。 這表示該運算子適用於每種特定類型的個別定義。 所有一元和二元算術以及位元運算子都是此類別中。 比較運算子是泛型，因此使用任何型別，而不只是基本的算術類型。 已區分聯集和記錄類型有自己的 F # 編譯器所產生的自訂實作。 類別型別使用方法<xref:System.Object.Equals%2A>。

泛型的運算子都可自訂的。 若要自訂比較函式，會覆寫<xref:System.Object.Equals%2A>提供您自己自訂的相等比較，並接著實作<xref:System.IComparable>。 <xref:System.IComparable?displayProperty=nameWithType>介面具有單一方法<xref:System.IComparable.CompareTo%2A>方法。

## <a name="operators-and-type-inference"></a>運算子和型別推斷

在運算式中運算子的使用限制在該運算子的型別推斷。 此外，使用運算子可防止自動一般化，因為使用運算子表示算術類型。 如果沒有使用任何其他資訊，F # 編譯器會推斷`int`當做算術運算式的類型。 您可以指定另一種類型，以覆寫此行為。 因此引數類型和傳回型別`function1`下列程式碼會推斷為`int`，但為類型`function2`推斷為`float`。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>另請參閱

- [符號和運算子參考](index.md)
- [運算子多載](../operator-overloading.md)
- [位元運算子](bitwise-operators.md)
- [布林運算子](boolean-operators.md)
