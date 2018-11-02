---
title: 轉型和轉換 (F#)
description: '了解如何 F # 程式設計語言提供轉換運算子的各種不同的基本型別之間的算術轉換。'
ms.date: 05/16/2016
ms.openlocfilehash: aca1a2523130ee485a7e7c9a6a45a410904cb246
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "45677925"
---
# <a name="casting-and-conversions-f"></a>轉型和轉換 (F#)

本主題描述支援 F # 中的型別轉換。

## <a name="arithmetic-types"></a>算術類型

F # 提供轉換運算子算術轉換之間不同的基本類型，例如整數和浮點類型之間。 整數和 char 的轉換運算子已核取及取消核取的表單;浮點運算子和`enum`轉換運算子不這麼做。 未選取的表單中所定義`Microsoft.FSharp.Core.Operators`並核取的形式定義於`Microsoft.FSharp.Core.Operators.Checked`。 已檢查的 form 溢位檢查，並產生執行階段例外狀況，如果產生的值超出目標類型的限制。

每個運算子有相同名稱做為目的地類型的名稱。 例如，在下列程式碼，在其中的類型明確註解，`byte`會顯示兩個不同的意義。 第一個相符項目類型，而且第二個是轉換運算子。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

下表顯示 F # 中定義的轉換運算子。

|運算子|描述|
|--------|-----------|
|`byte`|轉換為 byte，8 位元不帶正負號的型別。|
|`sbyte`|將轉換成帶正負號位元組。|
|`int16`|將轉換成 16 位元帶正負號的整數。|
|`uint16`|將轉換成 16 位元不帶正負號的整數。|
|`int32, int`|將轉換為 32 位元帶正負號的整數。|
|`uint32`|將轉換為 32 位元不帶正負號的整數。|
|`int64`|將轉換為 64 位元帶正負號的整數。|
|`uint64`|將轉換為 64 位元不帶正負號的整數。|
|`nativeint`|將轉換成原生整數。|
|`unativeint`|將轉換成帶正負號的原生整數。|
|`float, double`|將轉換為 64 位元雙精確度 IEEE 浮點數。|
|`float32, single`|將轉換為 32 位元單精確度 IEEE 浮點數。|
|`decimal`|將轉換成`System.Decimal`。|
|`char`|將轉換成`System.Char`，Unicode 字元。|
|`enum`|轉換為列舉類型。|
除了內建基本類型，您可以使用這些運算子與實作的型別`op_Explicit`或`op_Implicit`具有適當簽章的方法。 例如，`int`轉換運算子的運作方式與任何提供靜態方法的型別`op_Explicit`採用類型做為參數，並傳回`int`。 方法無法傳回型別多載的一般規則的特殊例外狀況，您可以在進行這`op_Explicit`和`op_Implicit`。

## <a name="enumerated-types"></a>列舉型別

`enum`運算子是一般運算子接受一個型別參數表示的型別`enum`將轉換成。 當轉換為列舉類型時，輸入判斷型別推斷嘗試`enum`您想要轉換成。 在下列範例中，變數`col1`未明確標註，但其類型從較新的等號比較測試推斷。 因此，編譯器可以推斷，您會將它轉換成`Color`列舉型別。 或者，您可以在其中提供的型別註釋，如同`col2`在下列範例中。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

您也可以明確指定目標的列舉型別與型別參數，如下列程式碼所示：

```fsharp
let col3 = enum<Color> 3
```

請注意，列舉型別轉換工作，只有當列舉的基礎類型是要轉換之類型相容。 下列程式碼，轉換無法編譯，因為不相符`int32`和`uint32`。

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

如需詳細資訊，請參閱 <<c0> [ 列舉型別](enumerations.md)。

## <a name="casting-object-types"></a>轉型物件類型

在物件階層架構中的型別之間的轉換是物件導向程式設計的基礎。 有兩個基本類型的轉換: （向上轉型） 向上轉型和轉型下 （向下轉型）。 階層架構中向上轉型表示從衍生的物件參考的基底物件參考的轉型。 這類轉換保證可以運作，只要基底類別衍生類別的繼承階層架構中。 物件實際上是正確的目的地 （衍生） 型別或目的型別衍生之類型的執行個體時，才會從衍生的物件參考的基底物件參考的階層中向下轉型成功。

F # 提供這些類型的轉換運算子。 `:>`運算子會轉換為階層架構，而`:?>`運算子會轉換為階層中向下。

### <a name="upcasting"></a>向上轉型

在許多物件導向語言中，向上轉型是隱含的;在 F # 中，規則會稍有不同。 將引數傳遞給方法的物件型別上時，會自動套用向上轉型。 不過，在模組中的 let 繫結函式，向上轉型不是自動的除非參數類型宣告為有彈性的類型。 如需詳細資訊，請參閱 <<c0> [ 彈性類型](flexible-Types.md)。

`:>`運算子會執行靜態轉型，這表示成功的轉換在編譯時期決定。 如果轉換使用`:>`會編譯成功，它是有效的轉型，並在執行階段中有不可能的失敗。

您也可以使用`upcast`運算子來執行這類轉換。 下列運算式會指定在階層中向上轉換：

```fsharp
upcast expression
```

當您使用向上轉型運算子時，編譯器會嘗試推斷您要從內容將轉換成的型別。 如果編譯器無法判斷目標型別，則編譯器會報告錯誤。

### <a name="downcasting"></a>向下轉型

`:?>`運算子會執行動態轉換，這表示成功的轉換在執行階段決定。 使用 cast`:?>`運算子不會檢查在編譯時期; 但在執行階段，嘗試轉換指定的型別。 如果物件是與目標型別相容，轉換就會成功。 如果物件不相容的目標型別，就會引發執行階段`InvalidCastException`。

您也可以使用`downcast`執行動態型別轉換運算子。 下列運算式會指定從程式內容推斷的型別階層中向下轉換：

```fsharp
downcast expression
```

與`upcast`運算子，如果編譯器無法推斷特定的目標型別，從內容，則會回報錯誤。

下列程式碼說明如何使用`:>`和`:?>`運算子。 程式碼將說明`:?>`運算子用在您知道，轉換會成功，因為它會擲回`InvalidCastException`如果轉換失敗。 如果您不知道，轉換會成功，會使用型別測試`match`運算式是較佳，因為它可避免產生例外狀況的額外負荷。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

因為泛型運算子`downcast`和`upcast`依賴類型推斷來判斷引數和傳回型別，在上述程式碼中的，您可以取代

```fsharp
let base1 = d1 :> Base1
```

取代為

```fsharp
let base1 = upcast d1
```

在先前的程式碼的引數類型和傳回類型是`Derived1`和`Base1`分別。

如需型別測試的詳細資訊，請參閱[比對運算式](match-Expressions.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
