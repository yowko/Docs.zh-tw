---
title: '&lt;= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: afbb932c1be010790236bec73a36acf0f01b97f4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44180692"
---
# <a name="lt-operator-c-reference"></a>&lt;= 運算子 (C# 參考)
如果第一個運算元小於或等於第二個運算元，則所有數值和列舉類型都會定義「小於或等於」關係運算子 (`<=`) 以傳回 `true`否則為 `false`。  
  
## <a name="remarks"></a>備註  
 使用者定義型別可以多載 `<=` 運算子。 如需詳細資訊，請參閱[運算子](../../../csharp/language-reference/keywords/operator.md)。 如果多載 `<=`，也必須多載 [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md)。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)  
- [explicit](../../../csharp/language-reference/keywords/explicit.md)
