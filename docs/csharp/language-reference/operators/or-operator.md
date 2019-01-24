---
title: '| 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 185ea3aabff4794ec08cca541773dbec3574ab4b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333508"
---
# <a name="-operator-c-reference"></a>| 運算子 (C# 參考)

整數型別和 `bool` 會預先定義二元 `|` 運算子。 對於整數型別，`|` 會計算其運算元的位元 OR。 對於 `bool` 運算元，`|` 會計算其運算元的邏輯 OR；亦即，如果且唯有當其兩個運算元都是 `false` 時，結果會是 `false`。

## <a name="remarks"></a>備註

不同於[條件式 OR 運算子](conditional-or-operator.md) `||`，二元 `|` 運算子會評估兩個運算元，不論第一個運算元的值為何。

使用者定義型別可以多載 `|` 運算子 (請參閱 [operator](../keywords/operator.md))。

## <a name="example"></a>範例

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)