---
title: + 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: b49694bc8937c58bd295f0f8e57c378802d0dfb9
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46470781"
---
# <a name="-operator-c-reference"></a>+ 運算子 (C# 參考)
`+` 運算子可以作為一元或二元運算子。  
  
## <a name="remarks"></a>備註  
 會預先定義所有數字類型的一元 `+` 運算子。 對數字類型執行一元 `+` 運算的結果就是運算元的值。  
  
 會預先定義數字和字串類型的二元 `+` 運算子。 針對數字類型，+ 會計算其兩個運算元的總和。 一或兩個運算元的類型為 string 時，+ 會串連以字串呈現的運算元。  
  
 委派類型也會提供可執行委派串連的二元 `+` 運算子。  
  
 使用者定義型別可以多載一元 `+` 和二元 `+` 運算子。 整數類資料類型上的作業通常允許用於列舉類型。 如需詳細資訊，請參閱 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)  
- [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)
