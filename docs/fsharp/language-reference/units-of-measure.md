---
title: 測量單位
description: 瞭解中的浮點數和帶正負號F#的整數值如何具有相關聯的測量單位，通常用來表示長度、數量和品質。
ms.date: 05/16/2016
ms.openlocfilehash: a81f7760301dc580e333d4659a72e6259d2c916b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216684"
---
# <a name="units-of-measure"></a>測量單位

中的浮點數和帶正負F#號的整數值可以具有相關聯的測量單位，通常用來表示長度、數量、品質等等。 藉由使用具有單位的數量，您可以讓編譯器驗證算術關聯性是否有正確的單位，這有助於防止程式設計錯誤。

## <a name="syntax"></a>語法

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>備註

先前的語法會將*單位名稱*定義為量值單位。 選擇性部分是用來根據先前定義的單位來定義新的量值。 例如，下列程式程式碼會定義量值`cm` （釐米）。

```fsharp
[<Measure>] type cm
```

下一行會將量值`ml` （milliliter）定義為三釐米（`cm^3`）。

```fsharp
[<Measure>] type ml = cm^3
```

在先前的語法中， *measure*是包含單位的公式。 在牽涉到單位的公式中，整數類支援（正和負數）、單位之間的空格表示兩個單位的產品`*` ，也表示單位的乘積，並`/`指出單位的商。 針對交互單位，您可以使用負整數乘冪或`/` ，表示單位公式的分子和分母之間的分隔。 分母中的多個單位應該以括弧括住。 以空格`/`分隔的單位會解讀為分母的一部分，但`*`後面的任何單位都會被視為分子的一部分。

您可以在單位運算式中使用1來表示量維度數量，或與其他單位（例如分子）一起使用。 例如，速率的單位會寫成`1/s`，其中`s`表示秒數。 單元公式中不使用括弧。 您不會在單元公式中指定數值轉換常數;不過，您可以分別使用單位來定義轉換常數，並在單元檢查計算中使用它們。

表示相同事物的單位公式可以用各種同等的方式撰寫。 因此，編譯器會將單元公式轉換成一致的形式，將負冪轉換成 reciprocals、將單位群組成單一分子和分母，然後 Alphabetizes 分子和分母中的單位。

例如，單位公式`kg m s^-2`和`m /s s * kg`都會轉換成`kg m/s^2`。

您在浮點運算式中使用量值單位。 使用浮點數搭配相關聯的測量單位，會增加另一層的型別安全，並協助避免當您使用弱式類型的浮點數時，公式中可能發生的單位不相符錯誤。 如果您撰寫使用單位的浮點運算式，則運算式中的單位必須相符。

您可以使用單元公式以角括弧標注常值，如下列範例所示。

```fsharp
1.0<cm>
55.0<miles/hour>
```

您不會在數位和角括弧之間加上空格。不過，您可以包含常值尾碼`f`，例如，如下列範例所示。

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

這類注釋會將常值的類型從其基本類型（例如`float`）變更為維度類型， `float<cm>`例如或`float<miles/hour>`，在此案例中為。 的`<1>`單位注釋表示量維度數量，而其類型等同于不含 unit 參數的基本型別。

量值單位的類型是一個浮點數或帶正負號的整數類資料類型，以及一個額外的單位注釋，以方括弧表示。 因此，當您將轉換類型從`g` （克`kg` ）寫入（千克）時，您會依照下列方式描述類型。

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

測量單位用於編譯時間單元檢查，但不會保存在執行時間環境中。 因此，它們不會影響效能。

量值單位可以套用至任何類型，而不只是浮點數類型。不過，只有浮點類型、帶正負號的整數類資料類型和十進位類型支援維度數量。 因此，在基本型別和包含這些基本型別的匯總上使用測量單位是合理的。

下列範例說明測量單位的使用。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

下列程式碼範例說明如何從量值浮點數轉換為已維度的浮點數。 您只要乘以1.0，就會將維度套用至1.0。 您可以將此抽象成類似`degreesFahrenheit`的函式。

此外，當您將已維度的值傳遞給預期會有量維度浮點數的函式時，您必須`float` `float`使用運算子取消單位或轉換成。 在此範例中，您會`1.0<degC>`將的`printf`引數除以`printf` ，因為需要量維度數量。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

下列範例會話會顯示此程式碼的輸出和輸入。

```console
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>使用泛型單位

您可以撰寫可在具有相關聯測量單位的資料上運作的泛型函數。 若要這麼做，您可以將類型與一般單位一起指定為類型參數，如下列程式碼範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>建立具有泛型單位的匯總類型

下列程式碼示範如何建立匯總類型，其中包含具有泛型單位的個別浮點值。 這可讓您建立單一類型，以搭配各種單位使用。 此外，一般單位會藉由確保具有一組單位的泛型型別與具有不同單位集合的相同泛型型別不同，來保留型別安全。 這項技術的基礎是`Measure`可以將屬性套用至型別參數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>執行時間的單位

測量單位用於靜態類型檢查。 當您編譯浮點值時，測量單位會被排除，因此在執行時間會遺失單位。 因此，任何嘗試執行的功能，都不可能發生于檢查執行時間的單位。 例如，不可能執行`ToString`函數來列印單位。

## <a name="conversions"></a>轉換

若要將具有單位（例如`float<'u>`）的類型轉換成不具有單位的類型，您可以使用標準轉換函數。 例如，您可以使用`float`將轉換`float`成沒有單位的值，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

若要將未使用的值轉換為具有單位的值，您可以乘以以適當單位標注的1或1.0 值。 不過，若要撰寫互通性層，還有一些明確的函式，可讓您用來將沒有單位的值轉換成值。 這些是在[languageprimitives.physicalequality](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3)模組中。 例如，若要從`float`無單位的轉換`float<cm>`為，請使用[FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>F#核心程式庫中的測量單位

在`FSharp.Data.UnitSystems.SI`命名空間中可以使用單位程式庫。 `m`它在`UnitSymbols`子命名空間中的符號形式（例如 for 計量）中包含 SI 單位，而在`UnitNames`子命名空間中， `meter`其完整名稱（例如 for 計量）。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
