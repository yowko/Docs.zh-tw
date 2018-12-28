---
title: 條件約束
description: 深入了解F#條件約束套用至泛型型別參數的泛型型別或函式中指定的類型引數的需求。
ms.date: 05/16/2016
ms.openlocfilehash: b253ce50707512a0d46c41bba2dde34adcc24d0e
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612227"
---
# <a name="constraints"></a>條件約束

本主題描述條件約束，您可以套用至泛型型別參數的泛型型別或函式中指定型別引數的需求。

## <a name="syntax"></a>語法

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>備註

有數個不同的條件約束，您可以套用至限制可用於泛型類型的類型。 下表列出並描述這些條件約束。

|條件約束|語法|描述|
|----------|------|-----------|
|類型條件約束|*型別參數*:&gt; *類型*|提供的型別必須等於或衍生自指定型別，或者，如果類型是介面，提供的型別必須實作介面。|
|Null 條件約束|*型別參數*: null|提供的型別必須支援 null 常值。 這包括所有的.NET 物件類型而非F#清單、 tuple、 函式、 類別、 記錄或等位型別。|
|明確成員的條件約束|[（]*型別參數*[或...或*型別參數*)]: (*成員簽章*)|至少其中一個提供的型別引數必須具有指定的簽章; 的成員不適用於一般用途。 成員必須是明確定義型別或隱含型別延伸模組的一部分，是明確的成員限制式的有效目標。|
|建構函式條件約束|*型別參數*: (新： 單位-&gt; ')|提供的型別必須具有預設建構函式。|
|實值類型條件約束|： 結構|提供的型別必須是.NET 實值型別。|
|參考類型條件約束|： 不結構|提供的型別必須是.NET 參考型別。|
|列舉型別條件約束|: enum&lt;*基礎類型*&gt;|提供的型別必須是列舉的類型，具有指定的基礎類型，不適用於一般用途。|
|委派條件約束|： 將委派&lt;*tuple 參數型別*，*傳回型別*&gt;|提供的型別必須是委派類型具有指定的引數和傳回值;不適用於一般用途。|
|比較條件約束|： 比較|提供的型別必須支援的比較。|
|等號比較條件約束|： 等號比較|提供的型別必須支援等號比較。|
|未受管理的條件約束|： 未受管理|提供的型別必須是 unmanaged 型別。 未受管理的類型為特定基本型別 (`sbyte`， `byte`， `char`， `nativeint`， `unativeint`， `float32`， `float`， `int16`， `uint16`， `int32`， `uint32`， `int64`， `uint64`，或`decimal`)，列舉型別`nativeptr<_>`，或其欄位為未受管理的所有類型的非泛型結構。|

您必須加入條件約束，當您的程式碼需要使用一般的條件約束的型別，但不要依賴型別上可用的功能。 例如，如果您使用的類型條件約束來指定類別類型時，您可以使用任何一種類型的泛型函式中該類別的方法。

指定條件約束時，有時必須撰寫型別參數明確，因為沒有任何限制，編譯器無法驗證您所使用的功能將會在可能會提供在執行階段類型的任何類型參數。

您在中使用的最常見的條件約束F#程式碼會指定基底類別或介面的型別條件約束。 其他條件約束是由F#來實作特定功能，例如明確成員，這個條件約束用來實作運算子多載算術的運算子，或主要是因為提供的程式庫F#支援一組完整的條件約束支援的通用語言執行平台。

在型別推斷處理序中，某些條件約束會自動由編譯器推斷。 例如，如果您使用`+`函式中的運算子，編譯器會推斷的明確成員上條件約束運算式中使用的變數類型。

下列程式碼說明一些條件約束宣告。

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

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
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