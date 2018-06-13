---
title: = 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 979250c91cfe2abdf7295ae3866cd6b4294285cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269276"
---
# <a name="-operator-c-reference"></a>= 運算子 (C# 參考)
指派運算子 (`=`) 將右方運算元的值儲存在儲存體位置，即由左方運算元表示的屬性或索引子，然後傳回值做為其結果。 運算元必須是相同的類型 (或右方運算元必須隱含轉換成左方運算元類型)。  
  
## <a name="remarks"></a>備註  
 無法多載指派運算子。 不過，您可以定義類型的隱含轉換運算子，這樣可讓您使用指派運算子和這些類型。 如需詳細資訊，請參閱[使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
