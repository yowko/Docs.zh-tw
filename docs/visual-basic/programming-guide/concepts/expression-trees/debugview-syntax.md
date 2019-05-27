---
title: 使用 DebugView 屬性 (Visual Basic) 的語法
description: 描述用來產生運算式樹狀架構的字串表示 DebugView 屬性的特殊語法
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 1b2a1164f02208cc7578820d8f8ed3bc145fb5b8
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196528"
---
# <a name="debugview-syntax"></a>`DebugView` 語法 

`DebugView`屬性 （只在偵錯時，才會提供） 所提供的運算式樹狀架構的字串呈現。 大部分是語法的很容易就能了解;特殊的情況下是由下列各節所述。

每個範例後面的註解區塊包含`DebugView`。 

## <a name="parameterexpression"></a>ParameterExpression

顯示 <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> 變數名稱時，其開頭會加上 "$" 符號。

如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。

### <a name="examples"></a>範例

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a>ConstantExpression

對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> 物件，會顯示常數的值。

對於某些數值類型，尾碼新增到的值：

| 類型 | 關鍵字 | 尾碼 |  
|--|--|--|
| <xref:System.UInt32> | [UInteger](../../../language-reference/data-types/uinteger-data-type.md) | U |
| <xref:System.Int64> | [Long](../../../language-reference/data-types/long-data-type.md) | L |
| <xref:System.UInt64> | [ULong](../../../language-reference/data-types/ulong-data-type.md) | UL |
| <xref:System.Double> | [Double](../../../language-reference/data-types/double-data-type.md) | D |
| <xref:System.Single> | [Single](../../../language-reference/data-types/single-data-type.md) | F | 
| <xref:System.Decimal> | [Decimal](../../../language-reference/data-types/decimal-data-type.md) | M |

### <a name="examples"></a>範例

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a>BlockExpression

如果類型<xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType>物件不同於在區塊中的最後一個運算式的類型，類型會顯示在角括弧內 (`<`和`>`)。 否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。

### <a name="examples"></a>範例

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object), 
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> 物件會與其委派類型一起顯示。

如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。

### <a name="examples"></a>範例

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a>LabelExpression

如果您指定 <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> 物件之前。

`.Label` 語彙基元表示標籤的開頭。 `.LabelTarget` 語彙基元表示要跳至的目標目的地。

如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。

### <a name="examples"></a>範例

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), 
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a>檢查的運算子

檢查的運算子中會顯示與`#`，運算子前面的符號。 例如，已檢查的加法運算子會顯示為 `#+`。

### <a name="examples"></a>範例

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```