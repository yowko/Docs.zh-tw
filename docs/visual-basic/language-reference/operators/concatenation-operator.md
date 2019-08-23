---
title: '&amp;運算子 (Visual Basic)'
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
ms.openlocfilehash: d387b2dfdbb3fefe357364f7b2a3dde155cbd489
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968347"
---
# <a name="amp-operator-visual-basic"></a>&amp;運算子 (Visual Basic)
產生兩個運算式的字串串連。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 Any `String` 或`Object` variable。  
  
 `expression1`  
 必要項。 具有擴展至`String`之資料類型的任何運算式。  
  
 `expression2`  
 必要項。 具有擴展至`String`之資料類型的任何運算式。  
  
## <a name="remarks"></a>備註  
 如果`expression1` `String`或`expression2`的資料類型不`String`是, 而是擴大到, 則會將`String`它轉換成。 如果其中一種資料類型不會擴展到`String`, 編譯器會產生錯誤。  
  
 的資料類型`result`為`String`。 如果其中一個或兩個運算式評估為不是[任何](../../../visual-basic/language-reference/nothing.md)值<xref:System.DBNull.Value?displayProperty=nameWithType>, 或其值為, 則會將它們視為字串, 其值為 ""。  
  
> [!NOTE]
> 運算子可以多載, 這表示當運算元具有該類別或結構的類型時, 類別或結構可以重新定義其行為。 `&` 如果您的程式碼在這類類別或結構上使用這個運算子, 請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
> [!NOTE]
> & 符號 (&) 字元也可以用來將變數識別為類型`Long`。 如需詳細資訊, 請參閱[類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用`&`運算子來強制執行字串串連。 結果為字串值, 表示兩個字串運算元的串連。  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [&= 運算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [串連運算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的串連運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
