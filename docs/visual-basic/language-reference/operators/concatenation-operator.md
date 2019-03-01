---
title: '&amp; 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 2237da5d64ada6817d3a9a88b04b76f573bd76c0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976508"
---
# <a name="amp-operator-visual-basic"></a>&amp; 運算子 (Visual Basic)
會產生兩個運算式的字串串連。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何`String`或`Object`變數。  
  
 `expression1`  
 必要項。 任何運算式資料類型可擴展為`String`。  
  
 `expression2`  
 必要項。 任何運算式資料類型可擴展為`String`。  
  
## <a name="remarks"></a>備註  
 如果您的資料類型`expression1`或`expression2`不是`String`但可擴展為`String`，則會轉換成`String`。 如果其中一種資料類型不會不會擴展為`String`，編譯器會產生錯誤。  
  
 資料類型`result`是`String`。 如果一或兩個運算式都評估為[Nothing](../../../visual-basic/language-reference/nothing.md)或值為<xref:System.DBNull.Value?displayProperty=nameWithType>，它們會被視為值為字串""。  
  
> [!NOTE]
>  `&`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
> [!NOTE]
>  連字號 (&) 字元也可用來識別做為類型的變數`Long`。 如需詳細資訊，請參閱 <<c0> [ 類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用`&`強制字串串連運算子。 結果是字串值，表示兩個字串運算元串連。  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>另請參閱
- [&= 運算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [串連運算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的串連運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
