---
title: '&gt;&gt; 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: f7cacd740966f0716e125887568a39abf0d9e454
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725424"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt; 運算子 (C# 參考)

右移運算子 (`>>`) 會向其第一個運算元右移第二個運算元所指定的位元數。

## <a name="remarks"></a>備註

如果第一個運算元是 [int](../keywords/int.md) 或 [uint](../keywords/uint.md) (32 位元數量)，則是由第二個運算元的低序位五位元指定移位計數 (第二個運算元 & 0x1f)。

如果第一個運算元是 [long](../keywords/long.md) 或 [ulong](../keywords/ulong.md) (64 位元數量)，則是由第二個運算元的低序位六位元指定移位計數 (第二個運算元 & 0x3f)。

如果第一個運算元是 [int](../keywords/int.md) 或 [long](../keywords/long.md)，則右移是算術移位 (高序位空位元會設定為正負號位元)。 如果第一個運算元的類型為 [uint](../keywords/uint.md) 或 [ulong](../keywords/ulong.md)，則右移是邏輯移位 (高序位位元會填上零)。

使用者定義型別可以多載 `>>` 運算子；第一個運算元的類型必須是使用者定義型別，而第二個運算元的類型必須是 [int](../keywords/int.md)。如需詳細資訊，請參閱[運算子](../keywords/operator.md)。 二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。

## <a name="example"></a>範例

[!code-csharp[csRefOperators#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#26)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)