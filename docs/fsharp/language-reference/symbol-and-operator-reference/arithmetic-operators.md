---
title: 算術運算子
description: 瞭解程式F#設計語言中可用的算術運算子。
ms.date: 04/04/2018
ms.openlocfilehash: b783a0134541f11f06dde83af97676699b797da1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630777"
---
# <a name="arithmetic-operators"></a>算術運算子

本主題描述F#語言中可用的算術運算子。

## <a name="summary-of-binary-arithmetic-operators"></a>二進位算術運算子的摘要

下表摘要說明可用於取消裝箱整數和浮點類型的二元算術運算子。

|二元運算子|附註|
|---------------|-----|
|`+`(加法、plus)|選定. 當數位同時加上, 且總和超出類型所支援的最大絕對值時, 可能發生溢位條件。|
|`-`(減法, 減號)|選定. 當減去不帶正負號的類型時, 或是浮點值太小而無法以類型表示時, 可能出現的下溢條件。|
|`*`(乘法, times)|選定. 當數位相乘且產品超出類型所支援的最大絕對值時, 可能發生溢位條件。|
|`/`(相除, 除以)|零除會導致<xref:System.DivideByZeroException>整數類資料類型。 對於浮點類型, 零除會提供您特殊的浮點值`+Infinity`或。 `-Infinity` 當浮點數太小而無法以類型表示時, 還有可能出現的下溢條件。|
|`%`(餘數, rem)|傳回除法運算的餘數。 結果的正負號與第一個運算元的正負號相同。|
|`**`(乘冪, 表示的乘冪)|當結果超出類型的最大絕對值時, 可能發生溢位條件。<br /><br />乘冪運算子僅適用于浮點類型。|

## <a name="summary-of-unary-arithmetic-operators"></a>一元算術運算子的摘要

下表摘要說明可用於整數和浮點類型的一元算術運算子。

|一元運算子|附註|
|--------------|-----|
|`+`3.402823e38|可以套用至任何算術運算式。 不會變更值的正負號。|
|`-`(負, 負值)|可以套用至任何算術運算式。 變更值的正負號。|

整數類資料類型溢位或下溢的行為是要換行。 這會導致不正確的結果。 整數溢位是可能嚴重的問題, 可能會導致未撰寫軟體的安全性問題。 如果這是您應用程式的顧慮, 請考慮在中`Microsoft.FSharp.Core.Operators.Checked`使用檢查的運算子。

## <a name="summary-of-binary-comparison-operators"></a>二進位比較運算子的摘要

下表顯示整數和浮點類型可用的二進位比較運算子。 這些運算子會傳回類型`bool`的值。

因為 IEEE 浮點標記法不支援完全相等的作業, 所以不應直接將浮點數與相等進行比較。 藉由檢查程式碼, 您可以輕鬆驗證的兩個數字, 實際上可能會有不同的位標記法。

|運算子|附註|
|--------|-----|
|`=`(相等、等於)|這不是指派運算子。 僅用於比較。 這是泛型運算子。|
|`>`(大於)|這是泛型運算子。|
|`<`(小於)|這是泛型運算子。|
|`>=`(大於或等於)|這是泛型運算子。|
|`<=`(小於或等於)|這是泛型運算子。|
|`<>`(不等於)|這是泛型運算子。|

## <a name="overloaded-and-generic-operators"></a>多載和泛型運算子

本主題中討論的所有運算子都定義于**fsharp.core**命名空間中。 某些運算子是使用靜態解析的類型參數來定義。 這表示與該運算子搭配使用的每個特定型別都有個別的定義。 所有的一元和二元算術和位運算子都是在此類別中。 比較運算子是泛型的, 因此可與任何類型搭配使用, 而不只是基本的算術類型。 區分聯集和記錄類型有自己的自訂實作為F#編譯器所產生。 類別類型使用方法<xref:System.Object.Equals%2A>。

泛型運算子是可自訂的。 若要自訂比較函數, <xref:System.Object.Equals%2A>請覆寫以提供您自己的自訂相等<xref:System.IComparable>比較, 然後執行。 介面具有單一方法, 也就是<xref:System.IComparable.CompareTo%2A>方法。 <xref:System.IComparable?displayProperty=nameWithType>

## <a name="operators-and-type-inference"></a>運算子和型別推斷

在運算式中使用運算子, 會限制該運算子上的型別推斷。 此外, 使用運算子會防止自動一般化, 因為使用運算子意指算術類型。 如果沒有任何其他資訊, F#編譯器會推斷`int`為算術運算式的類型。 您可以藉由指定其他類型來覆寫此行為。 因此`function1` `int`, 會將`function2` 下列`float`程式碼中的引數類型和傳回類型推斷為, 但是的類型會推斷為。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>另請參閱

- [符號和運算子參考](index.md)
- [運算子多載](../operator-overloading.md)
- [位元運算子](bitwise-operators.md)
- [布林運算子](boolean-operators.md)
