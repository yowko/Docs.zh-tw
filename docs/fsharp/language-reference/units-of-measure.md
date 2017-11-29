---
title: "測量單位 (F#)"
description: "了解如何浮點數和 F # 中的帶正負號的整數值可以具有相關聯的度量單位，通常會表示長度、 磁碟區，以及大量使用。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: cb2eb658-df6c-422e-afad-97422609c773
ms.openlocfilehash: 2d0683e864c5684a78c02e177c296d3067295723
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="units-of-measure"></a>測量單位

浮點和帶正負號的整數值在 F # 中可以有關聯的度量單位，通常用來表示長度，磁碟區、 大量，依此類推。 您可以藉由使用單位的數量，啟用編譯器驗證算術的關聯性沒有正確的單位，這有助於防止程式設計錯誤。


## <a name="syntax"></a>語法

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>備註
先前語法定義*單位名稱*做為度量單位。 選擇性的部分用來定義新的量值，根據先前定義的單位。 例如，下列一行會定義量值`cm`（公分）。

```fsharp
[<Measure>] type cm
```

下列一行會定義量值`ml`(milliliter) 為三次方公分 (`cm^3`)。

```fsharp
[<Measure>] type ml = cm^3
```

在先前的語法，*量值*是一種公式，包括單位。 在公式中涉及的單位，整數次方 （正數和負數） 支援、 單位之間的空格會表示產品的兩個單位，`*`也會指出單位的產品和`/`表示單位的商數。 交互單位，您可以使用負值的整數次方或`/`指出分子之間分母單元公式的隔離。 應該以括號括住在分母中的多個單位。 單位以之後的空格分隔`/`會解譯為屬於分母，但下列任何單元`*`都會解譯為分子的一部分。

您可以使用 1 單位在運算式中，單獨用於表示程度的數量，或搭配其他的單位，例如分子。 比方說，率的單位會寫成`1/s`，其中`s`表示秒數。 括號不會以單元公式。 單元公式; 中沒有指定數值的轉換常數不過，分別定義轉換常數的單位，然後在單位檢查計算中使用它們。

相同的意義的單元公式可以撰寫以相等的各種方式。 因此，編譯器會將單位公式轉換成一致的格式，將負乘方倒數、 群組單位轉換成單一的分子和，並依字母順序排列的分子和分母中的單元。

例如，單元公式`kg m s^-2`和`m /s s * kg`都會轉換成`kg m/s^2`。

您可以使用測量的單位的浮動點運算式。 使用浮點數連同相關聯的單位量值加入另一個層級的型別安全，因此有助於避免使用弱型別浮點數時，可以發生在公式中的單位不符錯誤。 如果您撰寫的浮動點使用的單位的運算式，必須符合在運算式中的單位。

下列範例所示，您可以標註具有單元公式在角括弧中的常值。

```fsharp
1.0<cm>
55.0<miles/hour>
```

您不將放在數字的角括號; 之間的空間不過，您可以包含常值後置詞例如`f`，如下列範例所示。

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

這類的註解變更自其基本類型的常值類型 (例如`float`) 為維度的類型，例如`float<cm>`或在此情況下， `float<miles/hour>`。 單位註解`<1>`指出程度的數量，而它的類型相當於沒有單元參數的基本類型。

測量單位的型別是浮點數或帶正負號整數類資料類型以及額外單元註釋，方括號中指出。 因此，當您撰寫的類型轉換，以從`g`（字母組） 到`kg`（公斤），描述類型，如下所示。

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

測量單位用於檢查的編譯時間單位，但不是會保存在執行階段環境。 因此，它們不會影響效能。

測量單位可以套用至任何類型，不只浮點類型。不過，只有浮點類型，帶正負號整數類資料類型和十進位型別的支援建立維度數量。 因此，它才有意義的基本型別和彙總包含這些基本型別上使用的測量單位。

下列範例說明如何使用的測量單位。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
下列程式碼範例說明如何從程度的浮點數轉換成維度的浮動點值。 您只將其乘以 1.0，套用到 1.0 的維度。 您可以執行像是函式來擷取這`degreesFahrenheit`。

此外，當您將維度的值傳遞至函式的預期程度的浮點數時，您必須先取消出單位或轉型為`float`使用`float`運算子。 在此範例中，除以`1.0<degC>`的引數`printf`因為`printf`必須要有此數量。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

下列範例工作階段顯示的輸出和輸入此程式碼。

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>使用泛型單位
您可以撰寫操作的泛型函式有相關聯的量值單位的資料。 您藉由指定的類型與泛型單位做為型別參數，如下列程式碼範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a>建立彙總類型與泛型單位
下列程式碼會示範如何建立彙總類型組成的個別浮動點值都是泛型的單位。 這可讓單一類型來建立適用於各種不同的單位。 此外，泛型單位保留型別安全確保擁有單位的一組的泛型類型的類型不同於相同的泛型類型具有一組不同的單位。 這項技術的基礎在於`Measure`屬性可以套用至型別參數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a>在執行階段的單位
測量單位用於靜態類型檢查。 浮點值會進行編譯，當的測量單位也會刪除，因此單位都將在執行階段遺失。 因此，任何嘗試實作取決於執行階段檢查之單元的功能不可能。 例如，實作`ToString`函式，以列印出單位不可能。


## <a name="conversions"></a>轉換
要轉換的類型具有單位 (例如， `float<'u>`) 型別，但是沒有單位，您可以使用標準轉換函式。 例如，您可以使用`float`將轉換成`float`沒有單位，如下列程式碼所示的值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

若要將無單位的值轉換成具有單位的值，您可以乘以與適當的單位值為 1 或 1.0 標註。 不過，撰寫互通性層級，也有某些 explicit 函式可讓您將無單位的值轉換成值的單位。 這些是在[Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3)模組。 例如，若要將無單位轉換`float`至`float<cm>`，使用[FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a>F # Power Pack 中的度量單位
提供 F # PowerPack 單元程式庫。 單元程式庫包含 SI 單位和實體的常數。


## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)
