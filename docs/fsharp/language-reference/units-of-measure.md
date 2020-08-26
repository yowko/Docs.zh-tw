---
title: 測量單位
description: '瞭解 F # 中的浮點數和帶正負號的整數值如何有相關聯的測量單位，通常用來表示長度、數量和品質。'
ms.date: 08/15/2020
ms.openlocfilehash: 0262f89e80697dd86161c93fe37381122972b56f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811570"
---
# <a name="units-of-measure"></a>測量單位

F # 中的浮點數和帶正負號的整數值可以有相關聯的測量單位，通常用來表示長度、數量、品質等等。 藉由使用具有單位的數量，您可以讓編譯器確認算術關聯性具有正確的單位，這有助於防止程式設計錯誤。

## <a name="syntax"></a>語法

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>備註

先前的語法會將 *單位名稱* 定義為量值的單位。 選擇性元件是用來根據先前定義的單位來定義新的量值。 例如，下列程式程式碼定義 `cm` (釐米) 的量值。

```fsharp
[<Measure>] type cm
```

下列程式程式碼定義 (milliliter) 的量值， `ml` () 的三釐米 `cm^3` 。

```fsharp
[<Measure>] type ml = cm^3
```

在先前的語法中， *measure* 是包含單位的公式。 在牽涉到單元的公式中， (正面和負面) 支援整數次冪，單位之間的空格表示兩個單位的產品， `*` 也指出單位的乘積，並 `/` 指出單位的商。 若為交互單位，您可以使用負整數的乘冪或 `/` ，表示單位公式的分子和分母之間的分隔。 分母中的多個單位應以括弧括住。 以空格分隔的單位會被視為 `/` 分母的一部分，但是之後的任何單位 `*` 會被解釋為分子的一部分。

您可以單獨使用單元運算式中的1來表示維度數量，或與其他單位（例如，在分子中）一起使用。 例如，速率的單位會寫入 `1/s` ，其中 `s` 表示秒數。 單元公式中不會使用括弧。 您未在單元公式中指定數值轉換常數;不過，您可以個別定義具有單位的轉換常數，並在單元檢查計算中使用它們。

表示相同專案的單位公式可以用各種相等的方式撰寫。 因此，編譯器會將單元公式轉換成一致的表單，這會將負冪轉換成 reciprocals、將單位群組為單一分子和分母，以及 Alphabetizes 分子和分母中的單位。

例如，單位公式 `kg m s^-2` 和 `m /s s * kg` 都轉換成 `kg m/s^2` 。

您可以使用浮點數運算式中的測量單位。 使用浮點數搭配相關聯的量值，可以增加另一層級的安全性，並協助避免當您使用弱式具型別浮點數時，公式中可能發生的單元不相符錯誤。 如果您撰寫使用單位的浮點運算式，運算式中的單位必須相符。

您可以使用角括弧的單位公式來標注常值，如下列範例所示。

```fsharp
1.0<cm>
55.0<miles/hour>
```

您不會在數位和角括弧之間加上空格;不過，您可以包含常值尾碼（例如 `f` ），如下列範例所示。

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

這類批註會將常值的類型從其基本類型 (例如 `float`) 變更為維度類型，例如 `float<cm>` 或，在此案例中為 `float<miles/hour>` 。 的單位注釋 `<1>` 表示量維度數量，而其類型相當於不含 unit 參數的基本型別。

度量單位的類型是浮點數或帶正負號的整數類型，以及額外的單位注釋（以方括弧表示）。 因此，當您將轉換的類型從 (的字母 `g`) 轉換為 `kg` (公斤) 時，您會描述這些類型，如下所示。

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

測量單位會用於編譯時間單元檢查，但不會保存在執行時間環境中。 因此，它們不會影響效能。

測量單位可以套用至任何類型，而不只是浮點數類型;不過，只有浮點數類型、帶正負號的整數類資料類型和 decimal 類型支援維度數量。 因此，在基本類型上使用測量單位，以及包含這些基本型別的匯總，則只合理。

下列範例說明如何使用測量單位。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

下列程式碼範例說明如何從量值浮點數轉換為維度浮點數。 您只需乘以1.0，將維度套用至1.0。 您可以將其抽象化為類似的函式 `degreesFahrenheit` 。

此外，當您將維度值傳遞至預期可量值之浮點數的函式時，您必須使用運算子取消單位或轉型為 `float` `float` 。 在此範例中，您會將的 `1.0<degC>` 引數除以， `printf` 因為預期會有 `printf` 量維度數量。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

下列範例會話顯示此程式碼的輸出和輸入。

```console
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>使用一般單位

您可以撰寫泛型函式，以便在具有相關測量單位的資料上運作。 若要這麼做，您可以指定一種型別搭配泛型單位做為型別參數，如下列程式碼範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>使用泛型單位建立匯總類型

下列程式碼示範如何建立匯總型別，其中包含具有泛型單位之個別浮點數的值。 這可讓您建立可搭配各種單位使用的單一類型。 此外，泛型單位也會藉由確保具有一組單位的泛型型別，與具有不同單位集合的相同泛型型別不同，來保留型別安全。 這項技術的基礎是可將 `Measure` 屬性套用至型別參數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>執行時間的單位

測量單位用於靜態類型檢查。 當您編譯浮點值時，會排除測量單位，因此在執行時間會遺失單位。 因此，任何嘗試執行相依于在執行時間檢查單位的功能都是不可行的。 例如，執行函式 `ToString` 以列印出單位是不可行的。

## <a name="conversions"></a>轉換

若要轉換具有單位 (的型別（例如， `float<'u>`) 為沒有單位的型別），您可以使用標準轉換函數。 例如，您可以使用 `float` 來轉換成沒有 `float` 單位的值，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

若要將無值的值轉換成具有單位的值，您可以乘以以適當單位標注的1或1.0 值。 不過，為了撰寫互通性層，還有一些明確的函式，可讓您用來將未使用的值轉換成具有單位的值。 這些都位於 [Fsharp.core languageprimitives.physicalequality](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html) 模組中。 例如，若要從未使用的轉換成 `float` `float<cm>` ，請使用 [FloatWithMeasure](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html#FloatWithMeasure)，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>F # 核心程式庫中的測量單位

在命名空間中有提供單位程式庫 `FSharp.Data.UnitSystems.SI` 。 它會在其符號形式中包含 SI 單位 (例如 `m` 子命名空間中的計量) `UnitSymbols` ，以及其完整名稱 (例如 `meter` `UnitNames` 子命名空間中的計量) 。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
