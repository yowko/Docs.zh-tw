---
title: 測量單位 (F#)
description: 了解如何浮點數和帶正負號的整數值，F# 中可以有關聯的量值，通常用來表示長度、 磁碟區，以及大量的單位。
ms.date: 05/16/2016
ms.openlocfilehash: ad2193e25f3c0cee6e73cd529ab43d1e4b6b549b
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "45972513"
---
# <a name="units-of-measure"></a>測量單位

在 F# 浮點和帶正負號的整數值可以具有相關聯的度量單位，通常用來表示長度，磁碟區，大量，依此類推。 藉由使用單位數量，您可以讓編譯器無法驗證算術的關聯性具有正確的單位，這有助於防止程式設計錯誤。

## <a name="syntax"></a>語法

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>備註

先前的語法會定義*單位名稱*做為度量單位。 選擇性的部分用來定義新的量值，依據先前定義的單位。 例如下, 面這一行會定義量值`cm`（公分）。

```fsharp
[<Measure>] type cm
```

下面這一行會定義量值`ml`(milliliter) 為三次方公分 (`cm^3`)。

```fsharp
[<Measure>] type ml = cm^3
```

在先前的語法*量值*是涉及單位的公式。 在涉及單位的公式，整數類資料的力量並支援 （正面和負面），單位之間的空格會指出兩個單位，產品`*`也表示的單位，產品和`/`表示單位的商數。 交互單位，您可以使用負值的整數冪或`/`表示的分子和分母單元公式的區隔。 應該以括號括住在分母中的多個單位。 單位以之後的空格分隔`/`解譯為屬於分母，但遵循任何單位`*`都會解譯為屬於分子。

在單位運算式中，請單獨來指示此數量，或與其他單位，例如分子，您可以使用 1。 比方說，單位的費率會寫成`1/s`，其中`s`表示秒數。 括號不會在單位公式中使用。 您沒有指定單位公式; 中數字轉換常數不過，您可以分開定義單位轉換常數和單位檢查計算中使用它們。

代表相同意義的單位公式可以以各種不同的對等方式。 因此，編譯器會將單位公式轉換成一致的格式，這會將負乘方倒數，群組單位轉換成單一的分子和分母中，並依字母順序排列的分子和分母的單位。

比方說，單位公式`kg m s^-2`並`m /s s * kg`都會轉換成`kg m/s^2`。

您可以使用測量的單位中浮動點運算式。 使用浮點數與相關聯的單位量值新增另一個層級的型別安全，並有助於避免使用弱型別浮點數時，可以發生在公式中的單元不符錯誤。 如果您撰寫的浮動點使用單位的運算式，必須符合在運算式中的單位。

下列範例所示，您可以標註具有單元公式在角括弧中的常值。

```fsharp
1.0<cm>
55.0<miles/hour>
```

請勿在數字的角括號; 之間的空間不過，您可以包含常值後置詞例如`f`，如下列範例所示。

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

這類的註解變更的常值型別從其基本類型 (例如`float`) 為維度的類型，例如`float<cm>`或在此情況下， `float<miles/hour>`。 單位註釋`<1>`指出此數量，以及它的型別等於單元參數的基本類型。

測量單位的類型是浮點數或帶正負號整數類資料類型，以及額外的單位註釋，方括號中指出。 因此，當您撰寫的類型轉換`g`（字母組） 到`kg`（公斤），描述類型，如下所示。

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

測量單位用於檢查的編譯時間單位，但不是會保存在執行階段環境。 因此，它們不會影響效能。

測量單位可以套用至任何類型，不只浮點類型;不過，只有浮點類型，所簽署的整數類資料類型，以及十進位型別建立維度的支援數量。 因此，它才有意義的基本型別和包含這些基本類型的彙總上使用的測量單位。

下列範例說明如何使用的測量單位。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

下列程式碼範例說明如何將此的浮點數轉換為維度的浮動點值。 您只是乘以 1.0 時，將套用至 1.0 的維度。 您可以執行像是函式簡化`degreesFahrenheit`。

此外，當您將維度的值傳遞至預期此浮點數的函式時，您必須先取消外延展單位或轉換成`float`使用`float`運算子。 在此範例中，除以`1.0<degC>`的引數`printf`因為`printf`預期此數量。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

下列範例工作階段會顯示此程式碼的輸入與輸出。

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>使用泛型的單位

您可以撰寫操作的泛型函式有相關聯的量值單位的資料。 您可以指定類型，以及泛型的單元型別參數，如下列程式碼範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>使用泛型的單位建立彙總類型

下列程式碼示範如何建立彙總類型，其中包含的個別浮動點值都是泛型的單位。 這可讓單一類型來建立可搭配各種不同的單位。 此外，泛型的單位，來確保泛型型別具有一組的單位類型不同於相同的泛型型別具有一組不同的單位保留型別安全。 這項技術的基礎在於`Measure`屬性可以套用至型別參數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>在執行階段的單位

測量單位用於靜態類型檢查。 浮點值編譯時，會刪除的測量單位，因此在執行階段的單位都會遺失。 因此，任何嘗試實作取決於在執行階段檢查單位的功能不可能。 比方說，實作`ToString`函式來列印外延展單位不可能。

## <a name="conversions"></a>轉換

若要將具有單位的類型 (例如`float<'u>`) 沒有單位的類型，您可以使用標準轉換函式。 例如，您可以使用`float`要轉換成`float`沒有單位，如下列程式碼所示的值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

若要 unitless 值轉換為具有單位的值，可以將由值為 1 或 1.0 標註，利用適當的單位。 不過，撰寫互通性層級，也有一些明確函數可用來將 unitless 值轉換為值，單位。 這些是在[Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3)模組。 例如，若要從 unitless 轉換`float`要`float<cm>`，使用[FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>F# 核心程式庫中的測量單位

單位程式庫都有`FSharp.Data.UnitSystems.SI`命名空間。 它包含這兩個符號格式的 SI 單位 (類似`m`個計量器) 中`UnitSymbols`子命名空間和其完整名稱 (例如`meter`個計量器) 中`UnitNames`子命名空間。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
