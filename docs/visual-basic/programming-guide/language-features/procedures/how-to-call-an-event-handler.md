---
title: "如何︰ 在 Visual Basic 中呼叫事件處理常式 |Microsoft 文件"
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
- Visual Basic code, procedures
- event handlers, calling
- event handlers
- procedures, event handlers
- procedures, calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: c5b300feca3415d1283d24179795a4ae92c61e52
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>如何：在 Visual Basic 中呼叫事件處理常式
*事件*時的動作或狀況，例如滑鼠按一下或信用額度超過 — 辨認某個程式元件，而且您可以撰寫程式碼來回應。 *事件處理常式*是撰寫來回應事件的程式碼。  
  
 事件處理常式中的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是`Sub`程序。 不過，您不正常呼叫它相同方式其他`Sub`程序。 相反地，您可以識別程序為事件處理常式。 您可以使用[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句和[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)變數，或使用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。 使用`Handles`子句是宣告中的事件處理常式的預設方式[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。 這是在整合式的開發環境 (IDE) 中進行程式設計時，設計工具撰寫事件處理常式的方式。 `AddHandler`陳述式是適用於在執行階段動態地引發事件。  
  
 發生事件時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會自動呼叫事件處理常式的程序。 任何可以存取事件的程式碼可能會導致發生這個問題藉由執行[RaiseEvent 陳述式](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)。  
  
 您可以將多個事件處理常式與相同的事件產生關聯。 在某些情況下，您可以中斷關聯的事件處理常式。 如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>若要呼叫事件處理常式使用控制代碼和 WithEvents  
  
1.  請確定事件宣告與[Event 陳述式](../../../../visual-basic/language-reference/statements/event-statement.md)。  
  
2.  宣告物件變數在模組或類別層級，使用[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)關鍵字。 `As`子句，這個變數必須指定引發事件的類別。  
  
3.  宣告中的事件處理`Sub`程序中，加入[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句指定`WithEvents`變數和事件名稱。  
  
4.  發生事件時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動呼叫`Sub`程序。 您的程式碼可以使用`RaiseEvent`陳述式就會發生此事件。  
  
     下列範例會定義事件和`WithEvents`指的是在類別中引發事件的變數。 事件處理`Sub`程序會使用`Handles`子句，以指定的類別和它處理的事件。  
  
     [!code-vb[VbVbcnProcedures #&4;](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>若要呼叫使用 AddHandler 的事件處理常式  
  
1.  請確定事件宣告與`Event`陳述式。  
  
2.  執行[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)動態連接事件處理`Sub`與事件的程序。  
  
3.  發生事件時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動呼叫`Sub`程序。 您的程式碼可以使用`RaiseEvent`陳述式就會發生此事件。  
  
     下列範例會定義`Sub`程序處理<xref:System.Windows.Forms.Form.Closing>表單的事件。</xref:System.Windows.Forms.Form.Closing> 然後它會使用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)關聯`catchClose` <xref:System.Windows.Forms.Form.Closing>.</xref:System.Windows.Forms.Form.Closing>的事件處理常式的程序  
  
     [!code-vb[VbVbcnProcedures #&5;](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     您可以藉由執行關聯事件的事件處理常式[RemoveHandler 陳述式](../../../../visual-basic/language-reference/statements/removehandler-statement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [Sub 程序](./sub-procedures.md)   
 [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [AddressOf 運算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [如何︰ 建立程序](./how-to-create-a-procedure.md)   
 [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)
