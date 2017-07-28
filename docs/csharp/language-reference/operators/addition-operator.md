---
title: "+ 運算子 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3c6ef1acc69fed1c43f0a249287ca8819c8f091c
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>+ 運算子 (C# 參考)
`+` 運算子可以作為一元或二元運算子。  
  
## <a name="remarks"></a>備註  
 會預先定義所有數字類型的一元 `+` 運算子。 對數字類型執行一元 `+` 運算的結果就是運算元的值。  
  
 會預先定義數字和字串類型的二元 `+` 運算子。 針對數字類型，+ 會計算其兩個運算元的總和。 一或兩個運算元的類型為 string 時，+ 會串連以字串呈現的運算元。  
  
 委派類型也會提供可執行委派串連的二元 `+` 運算子。  
  
 使用者定義型別可以多載一元 `+` 和二元 `+` 運算子。 整數類資料類型上的作業通常允許用於列舉類型。 如需詳細資訊，請參閱 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)。  
  
## <a name="example"></a>範例  
 [!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)   
 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)
