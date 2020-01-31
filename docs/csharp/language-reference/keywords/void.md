---
title: void - C# 參考
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 0624b547ee2586334ac35d366ae3c8dfd14963ee
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742768"
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

`void` 也可用於不安全的內容中，以宣告未知類型的指標。 如需詳細資訊，請參閱[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)。

`void` 是 .NET Framework <xref:System.Void?displayProperty=nameWithType> 類型的別名。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C# 關鍵字](index.md)
- [參考型別](reference-types.md)
- [實值型別](../builtin-types/value-types.md)
- [方法](../../programming-guide/classes-and-structs/methods.md)
- [Unsafe 程式碼和指標](../../programming-guide/unsafe-code-pointers/index.md)
