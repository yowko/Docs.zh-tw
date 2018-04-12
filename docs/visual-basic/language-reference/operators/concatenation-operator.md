---
title: '&amp;運算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76c8fc52a518dfe7850a5680b7d4f06f3d09bf73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a>&amp;運算子 (Visual Basic)
產生的字串串連兩個運算式。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何`String`或`Object`變數。  
  
 `expression1`  
 必要項。 任何運算式資料類型可擴展成`String`。  
  
 `expression2`  
 必要項。 任何運算式資料類型可擴展成`String`。  
  
## <a name="remarks"></a>備註  
 資料類型，是否`expression1`或`expression2`不`String`但可擴展為`String`，它會轉換成`String`。 如果資料類型並不會擴展為`String`，編譯器會產生錯誤。  
  
 資料型別`result`是`String`。 如果一或兩個運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)或具有值為<xref:System.DBNull.Value?displayProperty=nameWithType>，則會視為字串，其值為""。  
  
> [!NOTE]
>  `&`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
> [!NOTE]
>  連字號 (&) 字元也可用來識別變數類型為`Long`。 如需詳細資訊，請參閱[型別字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用`&`以強制字串串連運算子。 結果是字串值，表示兩個字串運算元的串連。  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [&= 運算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [串連運算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [在 Visual Basic 中的串連運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
