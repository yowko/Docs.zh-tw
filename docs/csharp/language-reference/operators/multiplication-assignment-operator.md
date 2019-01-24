---
title: '*= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 2038f3b55d46f3503496275b3d25b17663b8c1db
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333430"
---
# <a name="-operator-c-reference"></a>\*= 運算子 (C# 參考)

二進位乘法指派運算子。

## <a name="remarks"></a>備註

使用 `*=` 指派運算子的運算式，例如

```csharp
x *= y
```

相當於

```csharp
x = x * y
```

但只會評估 `x` 一次。 對於對要執行乘法的數值類型，已預先定義 [\* 運算子](multiplication-operator.md)。

無法直接多載 `*=` 運算子，但使用者定義型別可以多載 [\* 運算子](multiplication-operator.md) (請參閱 [operator](../keywords/operator.md))。

## <a name="example"></a>範例

[!code-csharp[csRefOperators#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#13)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
