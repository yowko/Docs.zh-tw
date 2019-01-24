---
title: '! 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- '! operator [C#]'
- logical negation operator (!) [C#]
- NOT operator [C#]
ms.assetid: f5ae133f-8f64-4560-b34f-cd9cd5eed4ad
ms.openlocfilehash: 6b6d1796032f536aac0be49d4f101c1380b4e98f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333222"
---
# <a name="-operator-c-reference"></a>! operator (C# 參考)

邏輯負運算子 (`!`) 是將運算元變成負值的一元運算子。 它是針對 `bool` 所定義，並且只有在其運算元為 `false` 時，才會傳回 `true`。

## <a name="remarks"></a>備註

使用者定義型別可以多載 `!` 運算子 (請參閱 [operator](../keywords/operator.md))。

## <a name="example"></a>範例

[!code-csharp[csRefOperators#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#7)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)