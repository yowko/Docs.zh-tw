---
title: '|= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: f4f7806c8679af400a371decd0c367929b3fb81d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333261"
---
# <a name="-operator-c-reference"></a>|= 運算子 (C# 參考)

OR 指派運算子。

## <a name="remarks"></a>備註

使用 `|=` 指派運算子的運算式，例如

```csharp
x |= y
```

相當於

```csharp
x = x | y
```

但只會評估 `x` 一次。 [&#124; 運算子](or-operator.md) 在整數運算元上執行位元邏輯 OR 運算，在 bool 運算元上執行邏輯 OR。

無法直接多載 `|=` 運算子，但使用者定義型別可以多載 [&#124; 運算子](or-operator.md) (請參閱 [operator](../keywords/operator.md))。

## <a name="example"></a>範例

[!code-csharp[csRefOperators#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#10)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)