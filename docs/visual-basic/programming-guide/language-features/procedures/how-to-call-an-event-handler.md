---
title: "How to: Call an Event Handler in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, procedures"
  - "event handlers, calling"
  - "event handlers"
  - "procedures, event handlers"
  - "procedures, calling"
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Call an Event Handler in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*事件*」\(Event\) 是指某個程式元件可以辨認，而且您可以撰寫程式碼予以回應的動作或項目，例如按一下滑鼠或信用額度超過。  「*事件處理常式*」\(Event Handler\) 是撰寫來回應事件的程式碼。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的事件處理常式是 `Sub` 程序。  不過，您通常不會以呼叫其他 `Sub` 程序的相同方式來呼叫它，  而是將程序識別為事件的處理常式。  使用 [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) 子句和 [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) 變數，或使用 [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md)，即可做這樣的處理。  使用 `Handles` 子句是在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中宣告事件處理常式的預設方法。  這是在整合式開發環境 \(IDE\) 中進行程式設計時，設計工具撰寫事件處理常式的方式。  `AddHandler` 陳述式 \(Statement\) 適合在執行階段動態引發事件。  
  
 發生事件時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會自動呼叫事件處理常式程序。  具有事件存取權的所有程式碼只要執行 [RaiseEvent Statement](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)，即可引發該事件。  
  
 可使一個以上的事件處理常式與相同事件產生關聯。  在一些情況下，可取消處理常式與事件的關聯。  如需詳細資訊，請參閱 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)。  
  
### 若要使用 Handles 和 WithEvents 呼叫事件處理常式  
  
1.  請確定是使用 [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md)來宣告事件。  
  
2.  使用 [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) 關鍵字，在模組或類別 \(Class\) 層級宣告物件變數。  這個變數的 `As` 子句必須指定可引發該事件的類別。  
  
3.  在事件處理 `Sub` 程序的宣告中，加入可指定 `WithEvents` 變數和事件名稱的 [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) 子句。  
  
4.  發生事件時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會自動呼叫 `Sub` 程序。  程式碼可使用 `RaiseEvent` 陳述式來引發該事件。  
  
     下列範例會定義事件和 `WithEvents` 變數，這個變數會參考可引發該事件的類別。  事件處理 `Sub` 程序會使用 `Handles` 子句，指定它所處理的類別和事件。  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### 若要使用 AddHandler 呼叫事件處理常式  
  
1.  請確定是使用 `Event` 陳述式來宣告事件。  
  
2.  執行 [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md)，以動態連接事件處理 `Sub` 程序與事件。  
  
3.  發生事件時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會自動呼叫 `Sub` 程序。  程式碼可使用 `RaiseEvent` 陳述式來引發該事件。  
  
     下列範例會定義 `Sub` 程序，以處理表單的 <xref:System.Windows.Forms.Form.Closing> 事件。  然後，使用 [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md)將 `catchClose` 程序關聯成 <xref:System.Windows.Forms.Form.Closing> 的事件處理常式。  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     執行 [RemoveHandler Statement](../../../../visual-basic/language-reference/statements/removehandler-statement.md)，即可取消事件處理常式與事件的關聯。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [How to: Create a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [How to: Call a Procedure that Does Not Return a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-does-not-return-a-value.md)