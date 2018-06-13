---
title: ~ 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 25b157fafde7d2b75cd8b112848a01e9b3fb0db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270299"
---
# <a name="-operator-c-reference"></a>~ 運算子 (C# 參考)
`~` 運算子會對其運算元執行位元補數運算，其有反轉每個位元的效果。 位元補數運算子會針對 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md) 和[ulong](../../../csharp/language-reference/keywords/ulong.md) 預先定義。  
  
> [!NOTE]
>  `~` 符號也用來宣告完成項。 如需詳細資訊，請參閱[完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)。  
  
## <a name="remarks"></a>備註  
 使用者定義型別可以多載 `~` 運算子。 如需詳細資訊，請參閱[運算子](../../../csharp/language-reference/keywords/operator.md)。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)  
 [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)
