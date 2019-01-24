---
title: '&lt;&lt;= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 4513c4b78dea3e8102c72a43249b4a44ffa2421d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333248"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;= 運算子 (C# 參考)

左移指派運算子。

## <a name="remarks"></a>備註

以下格式的運算式

```csharp
x <<= y
```

評估為

```csharp
x = x << y
```

但只會評估 `x` 一次。 [<< 運算子](left-shift-operator.md)會將 `x` 左移 `y` 所指定的位元數。

無法直接多載 `<<=` 運算子，但使用者定義型別可以多載 [<< 運算子](left-shift-operator.md) (請參閱 [operator](../keywords/operator.md))。

## <a name="example"></a>範例

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
