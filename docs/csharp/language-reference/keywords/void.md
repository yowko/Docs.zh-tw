---
title: "void (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords: void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a71cac30132417abce60cdde54322b5f2067d39d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="void-c-reference"></a>void (C# 參考)
當 `void` 作為方法的傳回型別時，其可指定方法不要傳回值。

方法的參數清單中不允許 `void`。 如果某方法不採用任何參數，且不傳回任何值，其宣告方法如下所示：

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` 也可用於不安全的內容中，以宣告未知類型的指標。 如需詳細資訊，請參閱[指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)。

`void` 是 .NET Framework <xref:System.Void?displayProperty=nameWithType> 類型的別名。

## <a name="c-language-specification"></a>C# 語言規格
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>請參閱
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [參考型別](../../../csharp/language-reference/keywords/reference-types.md)  
 [實值型別](../../../csharp/language-reference/keywords/value-types.md)  
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
