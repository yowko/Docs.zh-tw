---
title: "~ 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a9b0cabcb101fce8422b1390ec8c4cb3b3849631
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>~ 運算子 (C# 參考)
`~` 運算子會對其運算元執行位元補數運算，其有反轉每個位元的效果。 位元補數運算子會針對 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md) 和[ulong](../../../csharp/language-reference/keywords/ulong.md) 預先定義。  
  
> [!NOTE]
>  `~` 符號也用來宣告完成項。 如需詳細資訊，請參閱[完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)。  
  
## <a name="remarks"></a>備註  
 使用者定義型別可以多載 `~` 運算子。 如需詳細資訊，請參閱[運算子](../../../csharp/language-reference/keywords/operator.md)。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)  
 [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)
