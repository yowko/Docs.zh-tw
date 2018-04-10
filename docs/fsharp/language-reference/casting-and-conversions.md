---
title: 轉型和轉換 (F#)
description: '了解如何 F # 程式語言提供的轉換運算子的各種基本型別之間的算術轉換。'
keywords: Visual F#, F#, 函式程式設計
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: db30db67-da21-4206-bf0c-9211bd3cb22f
ms.openlocfilehash: df8352b0dd8651f1480515311454a218ea79b971
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="casting-and-conversions-f"></a>轉型和轉換 (F#)

本主題描述支援 F # 中的型別轉換。

## <a name="arithmetic-types"></a>算術類型
F # 提供的轉換運算子算術轉換之間各種基本型別，例如整數和浮點類型之間。 整數類資料類型和 char 的轉換運算子有核取及取消核取的表單。浮點運算子和`enum`轉換運算子不這麼做。 若未選取的表單中定義`Microsoft.FSharp.Core.Operators`且已檢查的表單定義於`Microsoft.FSharp.Core.Operators.Checked`。 選取的表單溢位檢查，並產生執行階段例外狀況，如果產生的值超過限制的目標類型。

每個這些運算子有相同名稱做為目的地類型的名稱。 例如，在下列程式碼中的類型必須明確標註，`byte`與兩個不同的意義會出現。 第一個型別，而第二個轉換運算子。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

下表顯示 F # 中定義的轉換運算子。

|運算子|描述|
|--------|-----------|
|`byte`|將轉換成 byte、 8 位元不帶正負號類型。|
|`sbyte`|將轉換成帶正負號的位元組。|
|`int16`|將轉換成 16 位元帶正負號的整數。|
|`uint16`|將轉換成 16 位元不帶正負號的整數。|
|`int32, int`|將轉換為 32 位元帶正負號的整數。|
|`uint32`|將轉換為 32 位元不帶正負號的整數。|
|`int64`|將轉換為 64 位元帶正負號的整數。|
|`uint64`|將轉換為 64 位元不帶正負號的整數。|
|`nativeint`|將轉換成原生的整數。|
|`unativeint`|將轉換成原生不帶正負號的整數。|
|`float, double`|將轉換為 64 位元雙精度 IEEE 浮點數。|
|`float32, single`|將轉換為 32 位元單精確度 IEEE 浮點數。|
|`decimal`|將轉換成`System.Decimal`。|
|`char`|將轉換成`System.Char`，Unicode 字元。|
|`enum`|轉換為列舉類型。|
除了內建基本類型，您可以使用這些運算子實作的型別與`op_Explicit`或`op_Implicit`具有適當簽章的方法。 例如，`int`轉換運算子搭配任何類型，提供靜態方法`op_Explicit`採用做為參數的型別，並傳回`int`。 為一般的規則不傳回型別多載方法的特殊例外狀況，您可以`op_Explicit`和`op_Implicit`。

## <a name="enumerated-types"></a>列舉的類型
`enum`運算子是採用一個代表類型的型別參數的泛型運算子`enum`轉換。 當轉換為列舉類型時，類型推斷嘗試判斷型別`enum`您想要轉換成。 在下列範例中，變數`col1`沒有明確標註，但其類型會推斷從更新版本的等號比較測試。 因此，編譯器可以減少您轉換成`Color`列舉型別。 或者，您可以提供類型註釋，如同`col2`在下列範例中。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]
    
您也可以明確指定的目標列舉型別與型別參數，如下列程式碼所示：

```fsharp
let col3 = enum<Color> 3
```

請注意，列舉型別會轉換為工作只有在列舉的基礎類型是轉換的類型相容。 下列程式碼，則轉換會失敗編譯因為之間不相符`int32`和`uint32`。

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

如需詳細資訊，請參閱[列舉](enumerations.md)。

## <a name="casting-object-types"></a>轉型物件類型
物件階層中的類型之間的轉換是對物件導向程式設計基礎。 有兩個基本類型的轉換: （向上轉型） 向上轉型及向下 （向下轉型） 轉型。 階層架構中向上轉型表示從衍生的物件參考的基底物件參考的轉型。 這類轉換保證可以運作，只要基底類別是在衍生類別的繼承階層架構中。 從衍生的物件參考的基底物件參考的階層中向轉型成功只有物件實際上是正確的目的地 （衍生） 型別或目的型別衍生之類型的執行個體。

F # 提供這些類型之轉換的運算子。 `:>`運算子會轉換為階層中往上和`:?>`運算子會轉換為階層中向下。

### <a name="upcasting"></a>向上轉型
在許多物件導向語言中，向上轉型是隱含的;F # 中的規則有些許不同。 將引數傳遞給方法的物件類型時，會自動套用向上轉型。 不過，對於在模組中的 let 繫結函式，向上轉型不是自動，除非參數型別宣告為有彈性的類型。 如需詳細資訊，請參閱[彈性類型](flexible-Types.md)。

`:>`運算子會執行轉換，這表示成功的轉型由決定在編譯時期靜態。 如果使用 cast`:>`會編譯成功，它是有效的轉換，在執行階段有未故障的時候。

您也可以使用`upcast`運算子來執行這類轉換。 下列運算式會指定在階層中向上轉換：

```fsharp
upcast expression
```

當您使用 upcast 運算子時，編譯器會嘗試推斷您從內容轉換成的型別。 如果編譯器無法判斷目標類型，編譯器會報告錯誤。

### <a name="downcasting"></a>向下轉型
`:?>`運算子會執行轉換，這表示成功的轉型會在執行階段決定的動態。 使用 cast`:?>`運算子不會檢查在編譯時期; 但在執行階段，嘗試轉型為指定的型別。 如果物件是相容的目標類型，轉換就會成功。 如果物件不相容於目標型別，就會引發執行階段`InvalidCastException`。

您也可以使用`downcast`運算子來執行動態類型轉換。 下列運算式會指定從程式內容推斷的型別階層中向下轉換：

```fsharp
downcast expression
```

與`upcast`運算子，如果編譯器無法推斷特定目標類型從內容，則會回報錯誤。

下列程式碼說明如何使用`:>`和`:?>`運算子。 程式碼會說明`:?>`運算子最適合在您知道轉換成功，因為它會擲回`InvalidCastException`如果轉換失敗。 如果您不知道，轉換會成功，會使用的型別測試`match`運算式是更好，因為它可避免產生例外狀況的額外負荷。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

因為泛型運算子`downcast`和`upcast`依賴類型推斷來判斷引數和傳回型別，上述程式碼中的，您可以取代

```fsharp
let base1 = d1 :> Base1
```

取代為

```fsharp
let base1 = upcast d1
```

在先前的程式碼中，引數類型和傳回型別是`Derived1`和`Base1`分別。

如需類型測試的詳細資訊，請參閱[比對運算式](match-Expressions.md)。

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)
