---
title: ^= 運算子 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 12189d6469a9716d3b7ebcffef23423a75692d1a
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333547"
---
# <a name="-operator-c-reference"></a>^= 運算子 (C# 參考)

互斥 OR 指派運算子。

## <a name="remarks"></a>備註

以下格式的運算式

```csharp
x ^= y
```

評估為

```csharp
x = x ^ y
```

但只會評估 `x` 一次。 [^ 運算子](xor-operator.md)會在整數運算元上執行位元互斥 OR 運算，以及在 [bool](../keywords/bool.md) 運算元上執行邏輯互斥 OR。

無法直接多載 ^= 運算子，但使用者定義型別可以多載 [^ 運算子](xor-operator.md) (請參閱 [operator](../keywords/operator.md))。

## <a name="example"></a>範例

[!code-csharp[csRefOperators#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#23)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)