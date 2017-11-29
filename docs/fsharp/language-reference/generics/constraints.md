---
title: "條件約束 (F#)"
description: "深入了解 F # 條件約束套用至泛型類型參數，以指定泛型型別或函式中的型別引數的需求。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f232a3a-9486-48fb-9759-f23404ed4b52
ms.openlocfilehash: 91854fd2f692688e0f1c27aba1422eff64156048
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="constraints"></a>條件約束

本主題描述條件約束，您可以套用至泛型類型參數的泛型型別或函式中指定型別引數的需求。


## <a name="syntax"></a>語法

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>備註
有數個不同的條件約束，您可以套用來限制可用於泛型類型的類型。 下表列出並描述這些條件約束。

|條件約束|語法|描述|
|----------|------|-----------|
|類型條件約束|*型別參數*:&gt; *類型*|提供的型別必須是等於或衍生型別指定，或者，如果類型是介面，提供的類型必須實作的介面。|
|Null 條件約束|*型別參數*: null|提供的類型必須支援 null 常值。 這包括所有.NET 物件類型但不是 F # 清單、 tuple、 函式、 類別、 記錄或等位型別。|
|明確成員條件約束|（[)]*型別參數*[或...或*型別參數*)]: (* 成員簽章 *)|至少其中一個提供的型別引數必須具有指定的簽章; 的成員不提供一般用途。 成員必須是明確定義明確的成員條件約束的有效目標的類型或隱含型別延伸模組的一部分。|
|建構函式條件約束|*型別參數*: (new： 單位-&gt; ')|提供的類型必須有預設建構函式。|
|實值類型條件約束|： 結構|提供的類型必須是.NET 實值類型。|
|參考類型條件約束|： 不結構|提供的類型必須是.NET 參考類型。|
|列舉型別條件約束|： 列舉&lt;*基礎類型*&gt;|提供的類型必須是列舉型別具有指定的基礎類型。不提供一般用途。|
|委派的條件約束|： 委派&lt;*tuple 參數型別*，*傳回型別*&gt;|提供的類型必須是委派類型具有指定的引數和傳回值;不提供一般用途。|
|比較條件約束|： 比較|提供的類型必須支援的比較。|
|等號比較條件約束|： 等號比較|提供的類型必須支援等號比較。|
|未受管理的條件約束|： 未受管理|提供的類型必須是 unmanaged 的類型。 Unmanaged 的類型為特定基本型別 (`sbyte`， `byte`， `char`， `nativeint`， `unativeint`， `float32`， `float`， `int16`， `uint16`， `int32`， `uint32`， `int64`， `uint64`，或`decimal`)，列舉型別`nativeptr&lt;_&gt;`，或其欄位是不受管理的所有類型的非泛型結構。|
您必須加入條件約束時使用的功能一般是用於條件約束類型但不是在型別，對您的程式碼。 比方說，如果您使用的類型條件約束指定類別類型時，您可以使用其中一個該類別中的泛型函式或類型的方法。

指定條件約束時，有時需要明確地撰寫型別參數因為如果沒有限制，編譯器無法驗證您所使用的功能將會在任何可能會提供在執行階段類型的類型參數。

您在 F # 程式碼中使用的最常見的條件約束會指定基底類別或介面的型別條件約束。 其他條件約束的 F # 程式庫用來實作特定功能，例如 明確成員條件約束，用來實作運算子多載算術運算子，或提供主要是因為 F # 支援的完整一組條件約束所支援的通用語言執行平台。

類型推斷程序，在某些條件約束會自動由編譯器所推斷。 例如，如果您使用`+`運算子函式中的，編譯器會推斷變數的運算式中使用的型別上的明確成員條件約束。

下列程式碼將說明一些條件約束宣告。

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
[泛型](index.md)

[條件約束](constraints.md)
