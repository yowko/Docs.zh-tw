---
title: -&gt; 運算子 (C# 參考)
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 178724ede105d809bd812461121a38d5a0e90517
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144126"
---
# <a name="-gt-operator-c-reference"></a>-&gt; 運算子 (C# 參考)

指標成員存取運算子 `->` 結合了指標間接取值和成員存取。

如果 `x` 是 `T*` 型別的指標，而 `y` 是 `T` 的可存取成員，則以下形式的運算式

```csharp
x->y
```

相當於

```csharp
(*x).y
```

`->` 運算子需要 [unsafe](../keywords/unsafe.md) 內容。

如需詳細資訊，請參閱[如何：使用指標存取成員](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

無法多載 `->` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[指標成員存取](~/_csharplang/spec/unsafe-code.md#pointer-member-access)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)
