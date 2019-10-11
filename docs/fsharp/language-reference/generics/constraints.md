---
title: 條件約束
description: 瞭解適用F#于泛型型別參數的條件約束，以指定泛型型別或函式中的型別引數需求。
ms.date: 05/16/2016
ms.openlocfilehash: 9912ba63138d893a7c616661dd2b1cbdbe51916c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736796"
---
# <a name="constraints"></a>條件約束

本主題描述可套用至泛型型別參數的條件約束，以指定泛型型別或函式中的型別引數需求。

## <a name="syntax"></a>語法

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>備註

有幾個不同的條件約束可供您套用，以限制可用於泛型型別的類型。 下表列出並描述這些條件約束。

|條件約束|語法|描述|
|----------|------|-----------|
|類型條件約束|*type-parameter* :&gt; *type*|提供的類型必須等於或衍生自指定的類型，或者，如果類型是介面，則提供的類型必須執行介面。|
|Null 條件約束|*type-parameter* : null|提供的類型必須支援 null 常值。 這包括所有 .NET 物件類型，但F#不包含清單、元組、函式、類別、記錄或聯集類型。|
|明確成員條件約束|[（]*型別參數*[或...或*型別參數*)]: (*成員簽章*)|提供的型別引數中至少必須有一個具有指定簽章的成員;不適用於一般用途。 成員必須在類型或隱含類型延伸的一部分上明確定義，才能成為明確成員條件約束的有效目標。|
|構造函式條件約束|*類型參數*：（new： unit-&gt; ' a）|提供的類型必須具有無參數的函式。|
|實值型別條件約束|：結構|提供的類型必須是 .NET 實數值型別。|
|參考型別條件約束|： not 結構|提供的型別必須是 .NET 引用型別。|
|列舉類型條件約束|: enum&lt;*underlying-type*&gt;|提供的類型必須是具有指定基礎類型的列舉類型。不適用於一般用途。|
|委派條件約束|: delegate&lt;*tuple-parameter-type*, *return-type*&gt;|提供的類型必須是具有指定的引數和傳回值的委派類型。不適用於一般用途。|
|比較準則約束|：比較|提供的類型必須支援比較。|
|相等條件約束|：相等|提供的類型必須支援相等。|
|非受控條件約束|：非受控|提供的型別必須是非受控型別。 非受控類型為特定基本類型（`sbyte`、`byte`、`char`、`nativeint`、`unativeint`、`float32`、`float`、`int16`、`uint16`、`int32`、0、1、2 或 3）、列舉類型、4 或非泛型其欄位為非受控類型的結構。|

當您的程式碼必須使用條件約束類型（而非一般類型）上可用的功能時，您必須加入條件約束。 例如，如果您使用類型條件約束來指定類別類型，您可以在泛型函數或類型中使用該類別的任何一個方法。

明確寫入型別參數時，有時需要指定條件約束，因為沒有條件約束，編譯器無法驗證您所使用的功能是否可用於該型別的執行時間可能會提供的任何型別。實參.

您在程式碼中F#使用的最常見條件約束是指定基類或介面的類型條件約束。 連結F#庫會使用其他條件約束來執行特定功能，例如明確成員條件約束（用來執行算術運算子的運算子多載），主要是因為F#支援 common language runtime 所支援的一組完整條件約束。

在型別推斷程式期間，編譯器會自動推斷某些條件約束。 例如，如果您在函數中使用 `+` 運算子，編譯器會在運算式中使用的變數類型上推斷明確成員條件約束。

下列程式碼說明一些條件約束宣告：

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a>另請參閱

- [泛型](index.md)
- [條件約束](constraints.md)
