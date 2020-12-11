---
title: 可為 Null 的實值型別
description: '瞭解如何使用可為 null 的實值型別，表示在 F # 中也可以是 null 的實數值型別。'
ms.date: 11/19/2020
ms.openlocfilehash: e28cbfc57c5631573f46ac36462517cf011e96d2
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009634"
---
# <a name="nullable-value-types"></a>可為 Null 的實值型別

_可為 null 的實值型_ 別 `Nullable<'T>` 代表也可以是的任何 [結構](structures.md)類型 `null` 。 當您與可選擇用來代表這些類型類型的程式庫和元件（例如整數）進行互動時，這項功能會很有説明 `null` 。 支援此結構的基礎類型為 <xref:System.Nullable%601?displayProperty=nameWithType> 。

## <a name="syntax"></a>Syntax

```fsharp
Nullable<'T>
Nullable value
```

## <a name="declare-and-assign-with-values"></a>使用值宣告並指派

宣告可為 null 的實值型別，就像在 F # 中宣告任何類似包裝函式的型別一樣：

```fsharp
open System

let x = 12
let nullableX = Nullable<int> x
```

您也可以省略泛型型別參數，並允許型別推斷來解析它：

```fsharp
open System

let x = 12
let nullableX = Nullable x
```

若要指派給可為 null 的實值型別，您也必須是明確的。 F # 定義可為 null 的實數值型別沒有隱含轉換：

```fsharp
open System

let mutable x = Nullable 12
x <- Nullable 13
```

## <a name="assign-null"></a>指派 null

您無法直接指派 `null` 給可為 null 的實值型別。 請 `Nullable()` 改用：

```fsharp
let mutable a = Nullable 42
a <- Nullable()
```

這是因為沒有 `Nullable<'T>` `null` 適當的值。

## <a name="pass-and-assign-to-members"></a>傳遞並指派給成員

使用成員和 F # 值兩者之間的主要差異在於，當您使用成員時，可以隱含推斷可為 null 的實數值型別。 請考慮採用可為 null 實值型別做為輸入的下列方法：

```fsharp
type C() =
    member _.M(x: Nullable<int>) = x.HasValue
    member val NVT = Nullable 12 with get, set

let c = C()
c.M(12)
c.NVT <- 12
```

在上述範例中，您可以傳遞 `12` 給方法 `M` 。 您也可以指派 `12` 給 auto 屬性 `NVT` 。 如果輸入可視為可為 null 的實值型別，且符合目標型別，則 F # 編譯器會隱含地轉換這類呼叫或指派。

## <a name="examine-a-nullable-value-type-instance"></a>檢查可為 null 的實值型別實例

不同于代表可能值的一般化結構，可為 null 的實值型別不 [會與模式](options.md)比對搭配使用。 相反地，您必須使用 [`if`](conditional-expressions-if-then-else.md) 運算式並檢查 `HasValue` 屬性。

若要取得基礎值，請在 `Value` 檢查之後使用屬性 `HasValue` ，如下所示：

```fsharp
open System

let a = Nullable 42

if a.HasValue then
    printfn $"{a} is {a.Value}"
else
    printfn $"{a} has no value."
```

## <a name="nullable-operators"></a>可為 null 的運算子

針對可為 null 的實數值型別（例如算術或比較）作業，可以使用 [可為 null 的運算子](symbol-and-operator-reference/nullable-operators.md)。

您可以使用命名空間中的轉換運算子，從一個可為 null 的實值型別轉換為另一個 `FSharp.Linq` ：

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt
```

您也可以使用適當的不可為 null 運算子來轉換為基本型別，如果沒有任何值，則會對例外狀況產生風險：

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

printfn $"value is %f{float nullableFloat}"
```

您也可以使用可為 null 的運算子作為檢查和的短期運算子 `HasValue` `Value` ：

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

let isBigger = nullableFloat ?> 1.0
let isBiggerLongForm = nullableFloat.HasValue && nullableFloat.Value > 1.0
```

`?>`比較會檢查左邊是否可為 null，而且只有在有值時才會成功。 它相當於其後的行。

## <a name="see-also"></a>另請參閱

- [結構](structures.md)
- [F # 選項](options.md)
