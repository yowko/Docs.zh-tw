---
title: DebugView 屬性 (C#) 所使用的語法
description: 描述 DebugView 屬性用來產生運算式樹狀架構之字串呈現的特殊語法
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: bc3fc579ed8031d818241f41ac728ef7e5be0b99
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690117"
---
# <a name="debugview-syntax"></a>`DebugView` 語法

`DebugView` 屬性 (僅於偵錯時提供使用) 能提供運算式樹狀架構的字串呈現。 此語法大部分皆相當容易了解；其特殊案例已於下列各節中描述。

每個範例後面都會有區塊註解，其中包含 `DebugView`。

## <a name="parameterexpression"></a>ParameterExpression

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> 變數名稱顯示時，其開頭會加上 `$` 符號。

如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。

### <a name="examples"></a>範例

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a>ConstantExpression

對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> 物件，會顯示常數的值。

對於具有標準尾碼為 C# 常值的數值類型，尾碼會新增至值。 下表顯示各種不同之數值類型的相關聯尾碼。

| 類型 | 關鍵字 | 尾碼 |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [uint](../../../language-reference/keywords/uint.md) | U |
| <xref:System.Int64?displayProperty=nameWithType> | [long](../../../language-reference/keywords/long.md) | L |
| <xref:System.UInt64?displayProperty=nameWithType> | [ulong](../../../language-reference/keywords/ulong.md) | UL |
| <xref:System.Double?displayProperty=nameWithType> | [double](../../../language-reference/keywords/double.md) | D |
| <xref:System.Single?displayProperty=nameWithType> | [float](../../../language-reference/keywords/float.md) | F |
| <xref:System.Decimal?displayProperty=nameWithType> | [decimal](../../../language-reference/keywords/decimal.md) | M |

### <a name="examples"></a>範例

```csharp
int num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a>BlockExpression

如果 <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> 物件的類型與區塊中最後一個運算式的類型不同，該類型會顯示於角括弧 (`<` 和 `>`) 之內。 否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。

### <a name="examples"></a>範例

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> 物件會與其委派類型一起顯示。

如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。

### <a name="examples"></a>範例

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```

## <a name="labelexpression"></a>LabelExpression

如果您指定 <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> 物件之前。

`.Label` 語彙基元表示標籤的開頭。 `.LabelTarget` 語彙基元表示要跳至的目標目的地。

如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。

### <a name="examples"></a>範例

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```

## <a name="checked-operators"></a>檢查的運算子

顯示檢查的運算子時，運算子前面會有 `#` 符號。 例如，已檢查的加法運算子會顯示為 `#+`。

### <a name="examples"></a>範例

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```
