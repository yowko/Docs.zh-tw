---
title: HOW TO：在 Visual Basic 中呼叫事件處理常式
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 58a96ccd06b70d481de335af5c3cd2be565cbd92
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973518"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>HOW TO：在 Visual Basic 中呼叫事件處理常式
*事件*是動作或狀況，例如滑鼠按一下或一種信用限制超過 — 可以辨認某些程式的元件，以及您可以撰寫程式碼來回應。 *事件處理常式*是您撰寫來回應事件的程式碼。  
  
 在 Visual Basic 中的事件處理常式是`Sub`程序。 不過，您不正常呼叫它相同其他`Sub`程序。 相反地，您可以識別此程序為事件處理常式。 您可以使用[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句， [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)變數，或使用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。 使用`Handles`子句是宣告在 Visual Basic 中的事件處理常式的預設方式。 這是整合式的開發環境 (IDE) 中進行程式設計時，事件處理常式由設計人員所撰寫的方式。 `AddHandler`陳述式是適用於在執行階段動態地引發事件。  
  
 發生事件時，Visual Basic 會自動呼叫事件處理常式程序。 任何可存取事件的程式碼可能會導致它執行就會發生[RaiseEvent 陳述式](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)。  
  
 您可以將多個事件處理常式關聯的同一個事件。 在某些情況下，您可以解除關聯事件的處理常式。 如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>使用您建立事件處理常式處理的呼叫和 WithEvents  
  
1.  請確定事件以宣告[Event 陳述式](../../../../visual-basic/language-reference/statements/event-statement.md)。  
  
2.  宣告物件變數在模組或類別層級，請使用[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)關鍵字。 `As`子句，這個變數必須指定引發事件的類別。  
  
3.  在宣告中的事件處理`Sub`程序中，新增[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句，指定`WithEvents`變數和事件名稱。  
  
4.  發生事件時，Visual Basic 會自動呼叫`Sub`程序。 您的程式碼可以使用`RaiseEvent`陳述式，使就會發生此事件。  
  
     下列範例會定義事件和`WithEvents`引發事件的類別是指的變數。 事件處理`Sub`程序會使用`Handles`子句，以指定的類別和它所處理的事件。  
  
     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>若要呼叫事件處理常式使用 AddHandler  
  
1.  請確定事件宣告與`Event`陳述式。  
  
2.  執行[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)動態連接事件處理`Sub`與事件的程序。  
  
3.  發生事件時，Visual Basic 會自動呼叫`Sub`程序。 您的程式碼可以使用`RaiseEvent`陳述式，使就會發生此事件。  
  
     下列範例會定義`Sub`程序來處理<xref:System.Windows.Forms.Form.Closing>型態的事件。 然後它會使用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)建立關聯`catchClose`做為事件處理常式的程序<xref:System.Windows.Forms.Form.Closing>。  
  
     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]  
  
     您可以藉由執行中斷事件的事件處理常式[RemoveHandler 陳述式](../../../../visual-basic/language-reference/statements/removehandler-statement.md)。  
  
## <a name="see-also"></a>另請參閱
- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [AddressOf 運算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [如何：建立程序](./how-to-create-a-procedure.md)
- [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)
