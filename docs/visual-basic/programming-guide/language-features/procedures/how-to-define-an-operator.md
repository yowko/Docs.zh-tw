---
title: HOW TO：定義運算子 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 1e7d767b1ba370ac7303abfd8aa3606a43c33de9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973284"
---
# <a name="how-to-define-an-operator-visual-basic"></a>HOW TO：定義運算子 (Visual Basic)
如果您已定義類別或結構，您可以定義標準運算式的行為 (例如`*`， `<>`，或`And`) 當一或兩個運算元屬於您自己的類別或結構的類型。  
  
 標準的運算子定義為類別或結構中的運算子程序。 必須是所有的運算子程序`Public` `Shared`。  
  
 類別或結構上定義的運算子，也稱為*多載*運算子。  
  
## <a name="example"></a>範例  
 下列範例會定義`+`結構的運算子稱為`height`。 結構會使用以英呎和英吋為單位的高度。 一*英吋*是 2.54 公分為單位，而另一個*步行*12 英吋。 若要確保正規化的值 (英吋為單位 < 12.0)，建構函式會執行*模數*12 算術。 `+`運算子使用建構函式來產生正規化的值。  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 您可以測試結構`height`為下列程式碼。  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  
  
  
## <a name="see-also"></a>另請參閱
- [運算子程序](./operator-procedures.md)
- [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)
- [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)
- [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)
- [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)
