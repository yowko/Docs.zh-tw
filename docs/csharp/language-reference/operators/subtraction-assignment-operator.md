---
title: -= 運算子 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 3b6890be4460a599a5d2f5f5f6ee1627be933f0b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333326"
---
# <a name="--operator-c-reference"></a>-= 運算子 (C# 參考)

減法指派運算子。

## <a name="remarks"></a>備註

使用 `-=` 指派運算子的運算式，例如

```csharp
x -= y
```

 相當於

```csharp
x = x - y
```

但只會評估 `x` 一次。 [- 運算子](subtraction-operator.md) 的意義取決於 `x` 和 `y` 的類型 (數字運算元表示減法、委派運算元表示委派移除等等)。

無法直接多載 `-=` 運算子，但使用者定義型別可以多載 [- 運算子](subtraction-operator.md) (請參閱 [operator](../keywords/operator.md))。

-= 運算子也會用於 C# 中，以取消事件的訂閱。 如需詳細資訊，請參閱[＜How to：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。

## <a name="example"></a>範例

[!code-csharp[csRefOperators#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#6)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
