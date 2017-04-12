---
title: "如何︰ 防止程序引數的值變更 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedures, arguments
- procedures, parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6e18f7ceefeec9c1f422d0eae4e727700ebd8b6e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>如何：防止程序引數的值變更 (Visual Basic)
如果程序宣告為參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供程序程式碼直接呼叫程式碼中的引數的程式設計項目參考。 這可讓程序來變更基礎呼叫程式碼中的引數的值。 在某些情況下呼叫程式碼可能會想要防止這類變更。  
  
 您永遠可以保護在變更引數，藉由宣告對應參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序中。 如果您想要能夠變更在某些情況下，而不是其他指定的引數，您可以宣告`ByRef`，讓呼叫的程式碼，判斷每個呼叫中的傳遞機制。 它會藉由封閉的對應引數括號，以傳值或不括在括號，以傳址方式傳遞它。 如需詳細資訊，請參閱[如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
## <a name="example"></a>範例  
 下列範例會顯示兩個程序取得陣列變數和操作其項目上。 `increase`程序只會加入至每個項目。 `replace`程序會將新的陣列指派給參數`a()`並將每個項目。 不過，重新指派不會影響呼叫程式碼中的陣列變數。  
  
 [!code-vb[VbVbcnProcedures #&35;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&38;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 第一個`MsgBox`呼叫會顯示 「 後 increase(n): 11、 21、 31、 41 」。 因為陣列`n`是參考型別，`replace`可以變更其成員，即使傳遞機制`ByVal`。  
  
 第二個`MsgBox`呼叫會顯示 「 後 replace(n): 11、 21、 31、 41 」。 因為`n`傳遞`ByVal`，`replace`無法修改變數`n`中指定新的陣列，讓呼叫的程式碼。 當`replace`建立新的陣列執行個體`k`並將它指派給本機變數`a`，它就不會參考`n`傳入呼叫程式碼。 它會變更的成員`a`，只有本機陣列`k`會受到影響。 因此，`replace`不會增加陣列的值`n`呼叫程式碼。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 在預設[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是以傳值方式傳遞引數。 不過，它是良好的程式設計作法包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。 這可讓您的程式碼更容易讀取。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)   
 [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md)   
 [可修改和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [以傳值或參考所傳遞引數之間的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [如何︰ 變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)   
 [如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)   
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
