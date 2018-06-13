---
title: 如何：在 Visual Basic 中呼叫事件處理常式
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 4e6aeaee8027e462dcdf80cae34b4b246fd58cf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652678"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>如何：在 Visual Basic 中呼叫事件處理常式
*事件*是動作或狀況，例如滑鼠點選或信用限制，或是超過 — 辨認某個程式元件，而且您可以撰寫程式碼回應。 *事件處理常式*是您撰寫來回應事件的程式碼。  
  
 在 Visual Basic 中的事件處理常式是`Sub`程序。 不過，您不正常呼叫它相同方式其他`Sub`程序。 相反地，您會識別此程序為事件處理常式。 您可以執行方式是使用[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句和[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)變數，或使用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。 使用`Handles`子句是宣告的事件處理常式，在 Visual Basic 中的預設方式。 這是整合式的開發環境 (IDE) 中進行程式設計時，事件處理常式由設計工具所撰寫的方式。 `AddHandler`陳述式適合用來在執行階段動態地引發事件。  
  
 發生事件時，Visual Basic 會自動呼叫事件處理常式的程序。 具有事件的存取權的任何程式碼可能會導致它藉由執行發生[RaiseEvent 陳述式](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)。  
  
 您可以將多個事件處理常式與相同的事件產生關聯。 在某些情況下，您可以中斷關聯的事件處理常式。 如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>若要呼叫事件處理常式使用控制代碼和 WithEvents  
  
1.  請確定事件宣告為[Event 陳述式](../../../../visual-basic/language-reference/statements/event-statement.md)。  
  
2.  宣告物件變數在模組或類別層級，請使用[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)關鍵字。 `As`子句，這個變數必須指定引發事件的類別。  
  
3.  宣告中的事件處理`Sub`程序中，加入[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)指定子句`WithEvents`變數和事件名稱。  
  
4.  Visual Basic 事件發生時，會自動呼叫`Sub`程序。 您的程式碼可以使用`RaiseEvent`陳述式就會發生此事件。  
  
     下列範例會定義事件和`WithEvents`指的是在類別中引發事件的變數。 事件處理`Sub`程序會使用`Handles`子句，以指定的類別和它所處理的事件。  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>若要呼叫事件處理常式使用 AddHandler  
  
1.  請確定事件宣告為`Event`陳述式。  
  
2.  執行[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)動態連接事件處理`Sub`程序與事件。  
  
3.  Visual Basic 事件發生時，會自動呼叫`Sub`程序。 您的程式碼可以使用`RaiseEvent`陳述式就會發生此事件。  
  
     下列範例會定義`Sub`程序處理<xref:System.Windows.Forms.Form.Closing>表單的事件。 然後它會使用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)關聯`catchClose`與事件處理常式的程序<xref:System.Windows.Forms.Form.Closing>。  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     您可以藉由執行中斷關聯事件的事件處理常式[RemoveHandler 陳述式](../../../../visual-basic/language-reference/statements/removehandler-statement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [Sub 程序](./sub-procedures.md)  
 [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [AddressOf 運算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [如何：建立程序](./how-to-create-a-procedure.md)  
 [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)
