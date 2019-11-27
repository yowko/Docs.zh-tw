---
title: 如何：定義運算子
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
ms.openlocfilehash: b99af8ff4d5428f1749bfc1a4c51a136f12405ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344867"
---
# <a name="how-to-define-an-operator-visual-basic"></a>如何：定義運算子 (Visual Basic)
如果您已定義類別或結構，當其中一個或兩個運算元屬於您的類別或結構類型時，可以定義標準運算子的行為（例如 `*`、`<>`或 `And`）。  
  
 將標準運算子定義為類別或結構內的運算子程式。 所有的運算子程式都必須 `Public` `Shared`。  
  
 在類別或結構上定義運算子*也稱為多*載運算子。  
  
## <a name="example"></a>範例  
 下列範例會針對稱為 `height`的結構定義 `+` 運算子。 結構會使用以英尺和英寸測量的高度。 1*英寸*是2.54 釐米，而一*英尺*是12英寸。 為確保正規化的值（英寸 < 12.0），此函式會執行*模數*12 算數運算。 `+` 運算子會使用此函數來產生正規化的值。  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 您可以使用下列程式碼來測試結構 `height`。  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a>另請參閱

- [運算子程序](./operator-procedures.md)
- [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)
- [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)
- [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)
- [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)
