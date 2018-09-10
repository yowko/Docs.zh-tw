---
title: 如何：識別可為 Null 的型別 (C# 程式設計手冊)
description: 了解如何判斷某個類型或執行個體是否屬於可為 Null 的型別
ms.date: 08/06/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: c65f80974154d81b5ddf239b617eeeda68434e09
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270285"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>如何：識別可為 Null 的型別 (C# 程式設計手冊)

下列範例示範如何判斷 <xref:System.Type?displayProperty=nameWithType> 執行個體是否代表可為 Null 的型別：

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

如範例所示，您使用 [typeof](../../language-reference/keywords/typeof.md) 運算子來建立 <xref:System.Type?displayProperty=nameWithType> 物件。  
  
如果您想要判斷某個執行個體是否屬於可為 Null 的型別，請勿使用 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法透過上述程式碼來測試 <xref:System.Type> 執行個體。 當您在可為 Null 的型別執行個體上呼叫 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法時，該執行個體會 [Boxing](using-nullable-types.md#boxing-and-unboxing) 處理為 <xref:System.Object>。 由於對可為 Null 型別的非 Null 執行個體進行 Boxing 處理相當於對基礎類型的值進行 Boxing 處理，因此 <xref:System.Object.GetType%2A> 會傳回<xref:System.Type> 物件，代表可為 Null 型別的基礎型別：

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

請勿使用 [is](../../language-reference/keywords/is.md) 運算子來判斷某個執行個體是否屬於可為 Null 的型別。 如下列範例所示，您無法使用 `is` 運算子來區別可為 Null 型別及其基礎類型的執行個體類型：

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

您可以使用下列範例所示的程式碼來判斷某個執行個體是否屬於可為 Null 的型別：

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a>請參閱

- [可為 Null 的型別](index.md)  
- [使用可為 Null 的型別](using-nullable-types.md)  
- <xref:System.Nullable.GetUnderlyingType%2A>  
