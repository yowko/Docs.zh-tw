---
title: '&amp; 運算子'
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
ms.openlocfilehash: 4cae7e59083890e82d754bdaa58942c2224357b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336061"
---
# <a name="amp-operator-visual-basic"></a>&amp; 運算子（Visual Basic）
產生兩個運算式的字串串連。  
  
## <a name="syntax"></a>語法  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要。 任何 `String` 或 `Object` 變數。  
  
 `expression1`  
 必要。 具有擴展為 `String`之資料類型的任何運算式。  
  
 `expression2`  
 必要。 具有擴展為 `String`之資料類型的任何運算式。  
  
## <a name="remarks"></a>備註  
 如果 `expression1` 或 `expression2` 的資料類型不 `String` 但擴大到 `String`，則會轉換成 `String`。 如果其中一種資料類型不會擴展到 `String`，編譯器會產生錯誤。  
  
 `result` 的資料類型為 `String`。 如果其中一個或兩個運算式評估為不是[任何](../../../visual-basic/language-reference/nothing.md)值，或具有 <xref:System.DBNull.Value?displayProperty=nameWithType>的值，則會將其視為字串，其值為 ""。  
  
> [!NOTE]
> `&` 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
> [!NOTE]
> & 符號（&）字元也可以用來將變數識別為類型 `Long`。 如需詳細資訊，請參閱[類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用 `&` 運算子來強制執行字串串連。 結果為字串值，表示兩個字串運算元的串連。  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>請參閱

- [&= 運算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [串連運算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的串連運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
