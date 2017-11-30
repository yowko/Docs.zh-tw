---
title: "如何：防止程序引數的值變更 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7975cbbc38c39223a4af5c87ac6bb090be548f2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>如何：防止程序引數的值變更 (Visual Basic)
如果程序宣告為參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供程序程式碼直接呼叫程式碼中的引數的基礎的程式設計項目參考。 這可讓程序來變更呼叫的程式碼中引數的基礎值。 在某些情況下呼叫的程式碼可能會想要防止這類變更。  
  
 您一律可以保護在變更引數，藉由宣告的對應參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序中。 如果您想要能夠變更在某些情況下，而不是其他指定的引數，您可以將它宣告`ByRef`，並讓呼叫的程式碼，判斷每個呼叫中的傳遞機制。 它會由封閉式括號，以傳值，對應的引數，或不將其括在括號，以傳址方式傳遞。 如需詳細資訊，請參閱[如何： 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
## <a name="example"></a>範例  
 下列範例會示範兩個程序的方式取得陣列變數和操作其項目上。 `increase`程序只會加入一個，以便每個項目。 `replace`程序會將新的陣列指派給參數`a()`再加入一個，以便每個項目。 不過，重新指派不會影響呼叫的程式碼中的陣列變數。  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 第一個`MsgBox`呼叫顯示"之後 increase(n): 11、 21、 31、 41"。 因為陣列`n`是參考型別，`replace`可以變更其成員，即使傳遞機制`ByVal`。  
  
 第二個`MsgBox`呼叫顯示"之後 replace(n): 11、 21、 31、 41"。 因為`n`傳遞`ByVal`，`replace`無法修改變數`n`指定新的陣列，讓呼叫的程式碼中。 當`replace`建立新的陣列執行個體`k`並將它指派給本機變數`a`，就會失去參考`n`傳入呼叫程式碼。 它會變更的成員`a`，只有本機陣列`k`會受到影響。 因此，`replace`不會遞增的值陣列的`n`呼叫的程式碼中。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 中的預設值[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]是以傳值方式傳遞引數。 不過，它是良好的程式設計作法中包含  [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。 這可讓您的程式碼更容易讀取。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)  
 [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)  
 [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)  
 [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
