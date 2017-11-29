---
title: "如何：定義運算子 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51921ee38204fd528ed19436806fc9433abbdc5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-an-operator-visual-basic"></a>如何：定義運算子 (Visual Basic)
如果您已定義類別或結構，您可以定義標準的運算子的行為 (例如`*`， `<>`，或`And`) 當一或兩個運算元是類別或結構的類型。  
  
 標準的運算子定義為類別或結構中的運算子程序。 所有的運算子程序必須是`Public` `Shared`。  
  
 在類別或結構上定義運算子，也稱為*多載*運算子。  
  
## <a name="example"></a>範例  
 下列範例會定義`+`結構的運算子稱為`height`。 結構會使用以英呎，英吋為單位的高度。 一個*英吋*是 2.54 公分為單位，以及一*步行*是 12 英吋。 為了確保正規化的值 (英吋 < 12.0)，建構函式會執行*模數*12 算術。 `+`運算子使用建構函式來產生正規化的值。  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 您可以測試的結構`height`為下列程式碼。  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 如需詳細資訊和範例，請參閱 [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703) (Visual Basic 2005 中的運算子多載)。  
  
## <a name="see-also"></a>另請參閱  
 [運算子程序](./operator-procedures.md)  
 [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)  
 [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)  
 [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)  
 [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)
