---
title: 可為 null 的C#實數值型別-程式設計指南
ms.custom: seodec18
description: 瞭解C#可為 null 的實值型別，以及如何使用它們
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#]
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: b8b52e7fb34adf65d5c76d59811ea6dd0ab16a98
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396214"
---
# <a name="nullable-value-types-c-programming-guide"></a>可為 null 的C#實數值型別（程式設計手冊）

可為 null 的實數值型別是 <xref:System.Nullable%601?displayProperty=nameWithType> 結構的實例。 可為 null 的實數值型別可以代表基礎類型的所有值，`T`，以及額外的[null](../../language-reference/keywords/null.md)值。 基礎類型 `T` 可以是任何不可為 Null 的[實值型別](../../language-reference/keywords/value-types.md)。 `T` 不可為參考型別。

> [!NOTE]
> C#8.0 引進了可為 null 的參考型別功能。 如需詳細資訊，請參閱[可為 null 的參考型別](../../nullable-references.md)。 從C# 2 開始可以使用可為 null 的實數值型別。

例如，您可以指派 `null` 或介於 <xref:System.Int32.MinValue?displayProperty=nameWithType> 到 <xref:System.Int32.MaxValue?displayProperty=nameWithType> 的任何整數值給 `Nullable<int>`，以及指派 [true](../../language-reference/keywords/true-literal.md)、[false](../../language-reference/keywords/false-literal.md) 或 `null` 給 `Nullable<bool>`。

當您需要表示基礎類型的未定義值時，您可以使用可為 null 的實數值型別。 布林變數只能有兩個值： `true` 和 `false`。 但不會有任何「未定義」的值。 在許多程式設計應用程式最值得注意的資料庫互動中，可能未定義或缺少變數值。 例如，資料庫中的欄位可能包含 true 或 false 兩種值，但也可能完全不包含任何值。 在此情況下，可使用 `Nullable<bool>` 類型。

可為 null 的實數值型別具有下列特性：

- 可為 null 的實數值型別代表可以指派給 `null` 值的實數值型別變數。

- 語法 `T?`是 `Nullable<T>` 的略寫。 這兩種格式是可互換的。

- 將值指派給可為 null 的實值型別，就像您在基礎實值型別中所做的一樣： `int? x = 10;` 或 `double? d = 4.108;`。 您也可以指派 `null` 值：`int? x = null;`。

- 使用 <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 和 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 唯讀屬性可測試是否有 Null，並擷取該值，如下列範例所示：`if (x.HasValue) y = x.Value;`

  - 如果變數包含值，<xref:System.Nullable%601.HasValue%2A> 屬性會傳回 `true`，若為 `null`，則傳回 `false`。

  - 若 <xref:System.Nullable%601.HasValue%2A> 傳回 `true`，<xref:System.Nullable%601.Value%2A> 屬性會傳回值。 否則會擲回 <xref:System.InvalidOperationException>。

- 您也可以使用具有 null 實數值型別的 `==` 和 `!=` 運算子，如下列範例所示： `if (x != null) y = x.Value;`。 如果 `a` 和 `b` 都是 Null，`a == b` 會評估為 `true`。

- 從 C# 7.0 開始，您就可以使用[模式比對](../../pattern-matching.md#the-is-type-pattern-expression)檢查及取得可為 Null 型別的值：`if (x is int valueOfX) y = valueOfX;`。

- `T?` 的預設值為 <xref:System.Nullable%601.HasValue%2A> 屬性傳回 `false` 的執行個體。

- 使用 <xref:System.Nullable%601.GetValueOrDefault> 方法可傳回指派的值，如果可為 Null 的型別值為 `null`，則傳回基礎實值型別的[預設](../../language-reference/keywords/default-values-table.md)值。

- 使用 <xref:System.Nullable%601.GetValueOrDefault(%600)> 方法可傳回指派的值，如果可為 Null 的型別值為 `null`，則傳回提供的預設值。

- 使用[null 聯合運算子](../../language-reference/operators/null-coalescing-operator.md)`??`，根據可為 null 的類型值，將值指派給基礎數值型別的變數： `int? x = null; int y = x ?? -1;`。 在此範例中，由於 `x` 是 `null`，因此 `y` 的結果值會 `-1`。

- 如果在兩個實數值型別之間定義使用者定義的轉換，則相同的轉換也可以搭配對應的可為 null 類型使用。

- 不允許嵌套的可為 null 的實數值型別。 系統不會編譯下列這一行：`Nullable<Nullable<int>> n;`

如需詳細資訊，請參閱[使用可為 null 的實數值型別](using-nullable-types.md)和[如何：識別可為 null 的實數值型別](how-to-identify-a-nullable-type.md)主題。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [??運算子](../../language-reference/operators/null-coalescing-operator.md)
- [可為 Null 的實值型別 (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
