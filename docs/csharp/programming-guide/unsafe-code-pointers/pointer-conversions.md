---
title: 指標轉換 - C# 程式設計指南
description: 瞭解指標轉換。 請參閱隱含和明確指標轉換的資料表、程式碼範例，以及查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: c39be5cb52964abbea5bc5636c6fa74d8411a331
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382083"
---
# <a name="pointer-conversions-c-programming-guide"></a>指標轉換 (C# 程式設計手冊)
下表顯示預先定義的隱含指標轉換。 在許多情況下可能會發生隱含轉換，包括方法叫用和指派陳述式。  
  
## <a name="implicit-pointer-conversions"></a>隱含指標轉換  
  
|寄件者|收件者|  
|----------|--------|  
|任何指標類型|void*|  
|null|任何指標類型|  
  
 明確指標轉換是用來使用 cast 運算式執行轉換，而這項轉換沒有任何隱含轉換。 下表顯示這些轉換。  
  
## <a name="explicit-pointer-conversions"></a>明確指標轉換  
  
|寄件者|收件者|  
|----------|--------|  
|任何指標類型|任何其他指標類型|  
|sbyte、byte、short、ushort、int、uint、long 或 ulong|任何指標類型|  
|任何指標類型|sbyte、byte、short、ushort、int、uint、long 或 ulong|  
  
## <a name="example"></a>範例  
 在下列範例中，`int` 的指標會轉換為 `byte` 的指標。 請注意，指標會指向變數的最低定址位元組。 當您連續遞增結果時 (大小最多為 `int` (4 個位元組))，可以顯示變數的剩餘位元組。  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [指標類型](pointer-types.md)
- [參考型別](../../language-reference/keywords/reference-types.md)
- [值類型](../../language-reference/builtin-types/value-types.md)
- [不安全](../../language-reference/keywords/unsafe.md)
- [fixed 陳述式](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
