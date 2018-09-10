---
title: 可為 Null 的型別 (C# 程式設計指南)
description: 深入了解 C# 可為 Null 的型別和其使用方式
ms.date: 07/30/2018
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: 2af0704abcad00c75a5d40bfe2d0523d07ee6a3f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205584"
---
# <a name="nullable-types-c-programming-guide"></a>可為 Null 的型別 (C# 程式設計指南)

可為 Null 的型別是 <xref:System.Nullable%601?displayProperty=nameWithType> 結構的執行個體。 可為 Null 的型別能代表基礎類型 `T` 的所有值，以及額外的 [null](../../language-reference/keywords/null.md) 值。 基礎類型 `T` 可以是任何不可為 Null 的[實值型別](../../language-reference/keywords/value-types.md)。 `T` 不可為參考型別。

例如，您可以指派 `null` 或介於 <xref:System.Int32.MinValue?displayProperty=nameWithType> 到 <xref:System.Int32.MaxValue?displayProperty=nameWithType> 的任何整數值給 `Nullable<int>`，以及指派 [true](../../language-reference/keywords/true-literal.md)、[false](../../language-reference/keywords/false-literal.md) 或 `null` 給 `Nullable<bool>`。

當您需要表示基礎類型的未定義值時，可使用可為 Null 的型別。 布林值變數只可有兩個值：true 和 false。 但不會有任何「未定義」的值。 在許多程式設計應用程式最值得注意的資料庫互動中，可能未定義或缺少變數值。 例如，資料庫中的欄位可能包含 true 或 false 兩種值，但也可能完全不包含任何值。 在此情況下，可使用 `Nullable<bool>` 類型。

可為 Null 的型別特色如下：
  
- 可為 Null 的型別代表可指派 `null` 值的實值型別變數。 您無法根據參考型別建立可為 Null 的型別。 (參考型別已經支援 `null` 值)。  
  
- 語法 `T?`是 `Nullable<T>` 的略寫。 這兩種格式是可互換的。  
  
- 將值指派給可為 Null 的型別，就像您指派值給基礎實值型別一樣：`int? x = 10;` 或 `double? d = 4.108;`。 您也可以指派 `null` 值：`int? x = null;`。  
  
- 使用 <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 和 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 唯讀屬性可測試是否有 Null，並擷取該值，如下列範例所示：`if (x.HasValue) y = x.Value;`  
  
  - 如果變數包含值，<xref:System.Nullable%601.HasValue%2A> 屬性會傳回 `true`，若為 `null`，則傳回 `false`。
  
  - 若 <xref:System.Nullable%601.HasValue%2A> 傳回 `true`，<xref:System.Nullable%601.Value%2A> 屬性會傳回值。 否則會擲回 <xref:System.InvalidOperationException>。  
  
- 您也可以使用 `==` 和 `!=` 運算子搭配可為 Null 的型別，如下列範例所示︰`if (x != null) y = x.Value;`。 如果 `a` 和 `b` 都是 Null，`a == b` 會評估為 `true`。  

- 從 C# 7.0 開始，您就可以使用[模式比對](../../pattern-matching.md#the-is-type-pattern-expression)檢查及取得可為 Null 型別的值：`if (x is int valueOfX) y = valueOfX;`。
  
- `T?` 的預設值為 <xref:System.Nullable%601.HasValue%2A> 屬性傳回 `false` 的執行個體。  

- 使用 <xref:System.Nullable%601.GetValueOrDefault> 方法可傳回指派的值，如果可為 Null 的型別值為 `null`，則傳回基礎實值型別的[預設](../../language-reference/keywords/default-values-table.md)值。  

- 使用 <xref:System.Nullable%601.GetValueOrDefault(%600)> 方法可傳回指派的值，如果可為 Null 的型別值為 `null`，則傳回提供的預設值。
  
- 使用[聯合 Null 的運算子](../../language-reference/operators/null-coalescing-operator.md) `??`可將值指派給以可為 Null 之型別值為基礎的基礎類型：`int? x = null; int y = x ?? -1;`。 在範例中，因為 `x` 是 Null，所以結果值 `y` 是 `-1`。

- 如果在兩種資料類別之間定義使用者定義轉換，則這些資料類型的可為 Null 版本也可使用相同的轉換。
  
- 不允許巢狀可為 Null 的型別。 系統不會編譯下列這一行：`Nullable<Nullable<int>> n;`  

如需詳細資訊，請參閱[使用可為 Null 的型別](using-nullable-types.md)和[如何：識別可為 Null 的型別](how-to-identify-a-nullable-type.md)主題。
  
## <a name="see-also"></a>請參閱

- <xref:System.Nullable%601?displayProperty=nameWithType>  
- <xref:System.Nullable?displayProperty=nameWithType>  
- [??運算子](../../language-reference/operators/null-coalescing-operator.md)  
- [C# 程式設計指南](../index.md)  
- [C# 指南](../../index.md)  
- [C# 參考](../../language-reference/index.md)  
- [可為 Null 的實值型別 (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
