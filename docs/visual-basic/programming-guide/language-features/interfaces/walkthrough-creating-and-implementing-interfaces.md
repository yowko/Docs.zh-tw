---
title: "建立和實作介面 (Visual Basic) |Microsoft 文件"
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
- interfaces, walkthroughs
- interfaces, testing
- interface implementation, walkthrough
- interfaces, creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: 22
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
ms.openlocfilehash: 076bc8d33e97286c31f27a2016e39a25e9cec22c
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>逐步解說：建立和實作介面 (Visual Basic)
介面描述的特性屬性、 方法和事件，但保留最多結構或類別的實作詳細資料。  
  
 本逐步解說示範如何宣告和實作介面。  
  
> [!NOTE]
>  本逐步解說不提供有關如何建立使用者介面的資訊。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-an-interface"></a>若要定義介面  
  
1.  開啟新[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows 應用程式專案。  
  
2.  加入專案中的新模組，依序按一下**加入模組**上**專案**功能表。  
  
3.  將新的模組`Module1.vb`按一下**新增**。 隨即出現新模組的程式碼。  
  
4.  定義名為介面`TestInterface`內`Module1`輸入`Interface TestInterface`之間`Module`和`End Module`陳述式，並按 enter。 **程式碼編輯器**縮排`Interface`關鍵字，並將`End Interface`表單的程式碼區塊的陳述式。  
  
5.  將下列程式碼之間定義屬性、 方法和事件的介面`Interface`和`End Interface`陳述式︰  
  
     [!code-vb[VbVbalrOOP #&98;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a>實作  
 您可能會注意到用來宣告介面成員不同於用來宣告類別成員宣告的語法。 這項差異會反映介面不能包含實作程式碼的事實。  
  
#### <a name="to-implement-the-interface"></a>若要實作介面  
  
1.  新增名為`ImplementationClass`藉由新增下列陳述式`Module1`之後，`End Interface`陳述式之前`End Module`陳述式，並按 enter:  
  
     [!code-vb[VbVbalrOOP #&99;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     如果您使用整合式的開發環境中，**程式碼編輯器**提供相對應的`End Class`陳述式，當您按 ENTER。  
  
2.  新增下列`Implements`陳述式來`ImplementationClass`，它將類別命名介面實作︰  
  
     [!code-vb[VbVbalrOOP #&100;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     當類別或結構的最上方的其他項目分開列出`Implements`陳述式指出類別或結構實作的介面。  
  
     如果您使用整合式的開發環境中，**程式碼編輯器**實作所需的類別成員`TestInterface`當您按下 enter 鍵，並可以略過下一個步驟。  
  
3.  如果您不使用整合式的開發環境中，您必須實作介面的所有成員`MyInterface`。 加入下列程式碼以`ImplementationClass`實作`Event1`， `Method1`，和`Prop1`:  
  
     [!code-vb[VbVbalrOOP #&101;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     `Implements`陳述式名稱的介面和介面成員實作。  
  
4.  完成的定義`Prop1`私用欄位加入至類別，以儲存屬性值︰  
  
     [!code-vb[VbVbalrOOP #&102;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     傳回值的`pval`屬性 get 存取子。  
  
     [!code-vb[VbVbalrOOP #&103;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     設定的值`pval`在屬性 set 存取子。  
  
     [!code-vb[VbVbalrOOP #&104;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  完成的定義`Method1`加入下列程式碼。  
  
     [!code-vb[VbVbalrOOP #&105;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a>若要測試的介面實作  
  
1.  啟動表單的專案中以滑鼠右鍵按一下**方案總管 中**，然後按一下**檢視程式碼**。 編輯器會顯示啟動表單的類別。 根據預設，啟動表單稱為`Form1`。  
  
2.  新增下列`testInstance`欄位`Form1`類別︰  
  
     [!code-vb[VbVbalrOOP #&120;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     藉由宣告`testInstance`為`WithEvents`、`Form1`類別可以處理其事件。  
  
3.  新增下列事件處理常式`Form1`類別來處理所引發的事件`testInstance`:  
  
     [!code-vb[VbVbalrOOP #&106;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  新增名為副程式`Test`至`Form1`測試實作類別的類別︰  
  
     [!code-vb[VbVbalrOOP #&107;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     `Test`程序會建立實作類別的執行個體`MyInterface`，指派至該執行個體`testInstance` 欄位中，設定屬性，並透過介面執行方法。  
  
5.  加入程式碼以呼叫`Test`程序從`Form1 Load`啟動表單的程序︰  
  
     [!code-vb[VbVbalrOOP #&108;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  執行`Test`程序，按下 F5。 會顯示訊息 「 Prop1 已設定為 9"。 之後您按一下 [確定] 會顯示 「 Method1 的 X 參數是 5 」 的訊息。 按一下 [確定]，並顯示 「 事件處理常式會攔截事件 」 的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [Implements 陳述式](../../../../visual-basic/language-reference/statements/implements-statement.md)   
 [介面](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)   
 [Interface 陳述式](../../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Event 陳述式](../../../../visual-basic/language-reference/statements/event-statement.md)

