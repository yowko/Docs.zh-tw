---
title: '&gt;&gt;= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 02a9559a5c4086eeed09094c15c3620366ffad8c
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333680"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= 運算子 (C# 參考)

右移指派運算子。

## <a name="remarks"></a>備註

以下格式的運算式

```csharp
x >>= y
```

評估為

```csharp
x = x >> y
```

但只會評估 `x` 一次。 [>> 運算子](right-shift-operator.md)會將 `x` 右移 `y` 所指定的數量。

無法直接多載 >>= 運算子，但使用者定義型別可以多載 [>> 運算子](right-shift-operator.md) (請參閱 [operator](../keywords/operator.md))。

## <a name="example"></a>範例

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)