---
title: 如何：識別可為 null 的實值C#類型-程式設計指南
ms.custom: seodec18
description: 瞭解如何判斷類型是否為可為 null 的實數值型別，或實例是否屬於可為 null 的實數值型別
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 15b1ffedf57648955ee5a004514841a5d140292b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392603"
---
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a>如何：識別可為 null 的實值C#型別（程式設計手冊）

下列範例示範如何判斷 <xref:System.Type?displayProperty=nameWithType> 實例是否代表封閉式泛型可為 null 的實值型別，也就是具有指定之型別參數的 <xref:System.Nullable%601?displayProperty=nameWithType> 型別 `T`：

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

如範例所示，您使用 [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) 運算子來建立 <xref:System.Type?displayProperty=nameWithType> 物件。

如果您想要判斷實例是否屬於可為 null 的實值型別，請不要使用 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法來取得要使用上述程式碼測試的 <xref:System.Type> 實例。 當您在可為 null 的實數值型別的實例上呼叫 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法時，實例會被[封裝](using-nullable-types.md#boxing-and-unboxing)為 <xref:System.Object>。 當可為 null 的實數值型別之非 null 實例的裝箱相當於基礎類型值的裝箱時，<xref:System.Object.GetType%2A> 會傳回代表可為 null 實數值型別之基礎類型的 @no__t 1 物件：

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

請勿使用[is](../../language-reference/keywords/is.md)運算子來判斷實例是否屬於可為 null 的實數值型別。 如下列範例所示，您無法使用 `is` 運算子來區別可為 null 的實數值型別和其基礎類型的實例類型：

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

您可以使用下列範例所顯示的程式碼，來判斷實例是否為可為 null 的實數值型別：

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a>另請參閱

- [可為 Null 的實值型別](index.md)
- [使用可為 null 的實數值型別](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
