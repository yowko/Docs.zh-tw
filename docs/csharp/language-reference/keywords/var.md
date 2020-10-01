---
description: 'var-c # 參考'
title: 'var-c # 參考'
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: d04bea9bcf5be726d3e81a1a53abed31f59330a0
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608708"
---
# <a name="var-c-reference"></a>var (c # 參考) 

從 c # 3 開始，在方法範圍內宣告的變數可以有隱含的 "type" `var` 。 隱含型別區域變數如同您自己宣告的類型一樣是強型別，但是編譯器會判斷類型。 下列兩個 `i` 宣告的功能相同：

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> 當 `var` 與 [可為 null 的參考](../builtin-types/nullable-reference-types.md) 型別搭配使用時，即使運算式型別不可為 null，它一律隱含表示可為 null 的參考型別。

關鍵字的常見用法是使用「函式 `var` 調用運算式」。 使用可 `var` 讓您不在變數宣告和物件具現化中重複類型名稱，如下列範例所示：

```csharp
var xs = new List<int>();
```

從 c # 9.0 開始，您可以使用目標型別[ `new` 運算式](../operators/new-operator.md)做為替代方案：

```csharp
List<int> xs = new();
List<int>? ys = new();
```

## <a name="example"></a>範例

下例示範兩個查詢運算式。 在第一個運算式中允許使用 `var`，但並非必要，因為查詢結果的類型可以明確陳述為 `IEnumerable<string>`。 不過，在第二個運算式中，`var` 允許結果是匿名型別的集合，而且只有編譯器本身才能存取該型別的名稱。 使用 `var` 就不需要建立結果的新類別。 請注意，在範例 #2 中，`foreach` 反覆運算變數 `item` 必須也是隱含型別。

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [隱含類型區域變數](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [LINQ 查詢作業中的類型關聯性](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
