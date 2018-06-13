---
title: 建立和實作介面 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: af9305deb60637b642d091501e743f2c7a57ccad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653607"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>逐步解說：建立和實作介面 (Visual Basic)

介面描述特性的屬性、 方法和事件，但保留最多結構或類別的實作詳細資料。  
  
 本逐步解說示範如何宣告和實作介面。  
  
> [!NOTE]
>  此逐步解說不提供如何建立使用者介面的相關資訊。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>若要定義介面
  
1.  開啟新的 Visual Basic Windows 應用程式專案。  
  
2.  加入專案中的新模組，依序按一下**加入模組**上**專案**功能表。  
  
3.  將新的模組`Module1.vb`按一下**新增**。 新模組的程式碼會顯示。  
  
4.  定義名為介面`TestInterface`內`Module1`輸入`Interface TestInterface`之間`Module`和`End Module`陳述式，並按 enter。 **程式碼編輯器**縮排`Interface`關鍵字，並將`End Interface`形成程式碼區塊的陳述式。  
  
5.  將下列程式碼之間定義屬性、 方法和事件的介面`Interface`和`End Interface`陳述式：  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>實作

 您可能會注意到用來宣告介面成員不同於用來宣告類別成員宣告的語法。 這項差異會反映介面不能包含實作程式碼的事實。  
  
### <a name="to-implement-the-interface"></a>若要實作介面
  
1.  將類別命名為`ImplementationClass`加入下列陳述式`Module1`，之後`End Interface`陳述式之前`End Module`陳述式，並按 enter:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     如果您要使用整合式的開發環境中，**程式碼編輯器**提供比對`End Class`陳述式，當您按下 ENTER。  
  
2.  加入下列`Implements`陳述式來`ImplementationClass`，其中的類別命名介面實作：  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     當從其他項目上方的類別或結構，分別列於`Implements`陳述式表示類別或結構實作介面。  
  
     如果您要使用整合式的開發環境中，**程式碼編輯器**實作所需的類別成員`TestInterface`當您按下 ENTER，以及您可以略過下一個步驟。  
  
3.  如果您不使用整合式的開發環境中，您必須實作介面的所有成員`MyInterface`。 將下列程式碼加入`ImplementationClass`實作`Event1`， `Method1`，和`Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements`陳述式命名的介面和實作介面成員。  
  
4.  完成的定義`Prop1`將私用欄位加入至儲存屬性值的類別：  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     傳回值的`pval`從屬性 get 存取子。  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     值設定`pval`在屬性 set 存取子。  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5.  完成的定義`Method1`加入下列程式碼。  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>若要測試介面的實作
  
1.  以滑鼠右鍵按一下 [啟動表單的專案中的**方案總管] 中**，然後按一下**檢視程式碼**。 編輯器會顯示啟動表單的類別。 根據預設，會呼叫啟動表單`Form1`。  
  
2.  加入下列`testInstance`欄位設為`Form1`類別：  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     藉由宣告`testInstance`為`WithEvents`、`Form1`類別可以處理的事件。  
  
3.  新增下列事件處理常式`Form1`處理所引發的事件類別`testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4.  加入名為的副程式`Test`至`Form1`測試實作類別的類別：  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test`程序會建立實作類別的執行個體`MyInterface`，會指派至該執行個體`testInstance` 欄位中，設定屬性，並透過介面執行方法。  
  
5.  加入程式碼以呼叫`Test`程序從`Form1 Load`啟動表單的程序：  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6.  執行`Test`按 f5 鍵的程序。 會顯示訊息 「 Prop1 已設為 9"。 您按一下 [確定]，訊息 「 Method1 的 X 參數 」 5 之後隨即顯示。 按一下 [確定]，並顯示 「 事件處理常式會攔截事件 」 的訊息。  
  
## <a name="see-also"></a>另請參閱

 [Implements 陳述式](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [介面](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Interface 陳述式](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Event 陳述式](../../../../visual-basic/language-reference/statements/event-statement.md)  