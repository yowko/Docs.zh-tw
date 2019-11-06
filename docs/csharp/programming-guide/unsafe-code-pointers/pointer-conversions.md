---
title: 指標轉換 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: b0a517eacc505376c9502e9d095c7aac0cd54555
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417524"
---
# <a name="pointer-conversions-c-programming-guide"></a>指標轉換 (C# 程式設計手冊)
下表顯示預先定義的隱含指標轉換。 在許多情況下可能會發生隱含轉換，包括方法叫用和指派陳述式。  
  
## <a name="implicit-pointer-conversions"></a>隱含指標轉換  
  
|From|若要|  
|----------|--------|  
|任何指標類型|void*|  
|null|任何指標類型|  
  
 明確指標轉換是用來使用 cast 運算式執行轉換，而這項轉換沒有任何隱含轉換。 下表顯示這些轉換。  
  
## <a name="explicit-pointer-conversions"></a>明確指標轉換  
  
|From|若要|  
|----------|--------|  
|任何指標類型|任何其他指標類型|  
|sbyte、byte、short、ushort、int、uint、long 或 ulong|任何指標類型|  
|任何指標類型|sbyte、byte、short、ushort、int、uint、long 或 ulong|  
  
## <a name="example"></a>範例  
 在下列範例中，`int` 的指標會轉換為 `byte` 的指標。 請注意，指標會指向變數的最低定址位元組。 當您連續遞增結果時 (大小最多為 `int` (4 個位元組))，可以顯示變數的剩餘位元組。  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [指標型別](./pointer-types.md)
- [型別](/dotnet/csharp/language-reference/keywords)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed 陳述式](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
