---
title: 建立及實作介面
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 47176d2e7a512d8e8c27a90ac04d2a2a2af274b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345045"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>逐步解說：建立和實作介面 (Visual Basic)

介面會描述屬性、方法和事件的特性，但會將執行詳細資料保持在結構或類別的最上方。  
  
 本逐步解說示範如何宣告和執行介面。  
  
> [!NOTE]
> 本逐步解說並未提供如何建立使用者介面的相關資訊。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>若要定義介面
  
1. 開啟新的 Visual Basic Windows 應用程式專案。  
  
2. 按一下 [**專案**] 功能表上的 [**加入模組**]，將新的模組加入至專案。  
  
3. 將新的模組命名為 `Module1.vb`，然後按一下 [**新增**]。 新模組的程式碼隨即顯示。  
  
4. 輸入 `Module` 和 `End Module` 語句之間的 `Interface TestInterface`，然後按 ENTER，以在 `Module1` 中定義名為 `TestInterface` 的介面。 [程式**代碼編輯器**] 會縮排 `Interface` 關鍵字，並加入 `End Interface` 語句以形成程式碼區塊。  
  
5. 藉由將下列程式碼放在 `Interface` 和 `End Interface` 語句之間，定義介面的屬性、方法和事件：  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>實作

 您可能會注意到，用來宣告介面成員的語法與用來宣告類別成員的語法不同。 這種差異反映了介面不能包含實作為程式碼的事實。  
  
### <a name="to-implement-the-interface"></a>若要執行介面
  
1. 將下列語句加入至 `Module1`、在 `End Interface` 語句之後、`End Module` 語句之前，然後按 ENTER 鍵，以新增名為 `ImplementationClass` 的類別：  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     如果您在整合式開發環境中工作，則當您按下 ENTER 時，程式**代碼編輯器**會提供相符的 `End Class` 語句。  
  
2. 將下列 `Implements` 語句加入 `ImplementationClass`，這會為該類別所執行的介面命名：  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     與類別或結構頂端的其他專案分開列出時，`Implements` 語句會指出類別或結構會執行介面。  
  
     如果您在整合式開發環境中工作，程式**代碼編輯器**會在您按下 enter 時，執行 `TestInterface` 所需的類別成員，而您可以略過下一個步驟。  
  
3. 如果您不是在整合式開發環境中工作，就必須執行介面的所有成員 `MyInterface`。 將下列程式碼新增至 `ImplementationClass`，以執行 `Event1`、`Method1`和 `Prop1`：  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements` 語句會命名要實作為介面和介面成員。  
  
4. 藉由將私用欄位新增至儲存屬性值的類別，完成 `Prop1` 的定義：  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     從屬性 get 存取子傳回 `pval` 的值。  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     設定屬性 set 存取子中的 `pval` 值。  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. 新增下列程式碼，以完成 `Method1` 的定義。  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>測試介面的執行
  
1. 在 **方案總管**中，以滑鼠右鍵按一下專案的 啟動 表單，然後按一下 **查看程式碼**。 編輯器會顯示您的啟動表單的類別。 預設會呼叫啟動表單 `Form1`。  
  
2. 將下列 `testInstance` 欄位新增至 `Form1` 類別：  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     藉由將 `testInstance` 宣告為 `WithEvents`，`Form1` 類別可以處理其事件。  
  
3. 將下列事件處理常式新增至 `Form1` 類別，以處理 `testInstance`所引發的事件：  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. 將名為 `Test` 的副程式新增至 `Form1` 類別，以測試執行類別：  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test` 程式會建立可執行 `MyInterface`的類別實例、將該實例指派給 `testInstance` 欄位、設定屬性，以及透過介面執行方法。  
  
5. 新增程式碼，以從啟動表單的 `Form1 Load` 程式中呼叫 `Test` 程式：  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. 按 F5 鍵執行 `Test` 程式。 [Prop1 已設定為 9] 訊息隨即顯示。 按一下 [確定] 之後，就會顯示「Method1 的 X 參數是5」的訊息。 按一下 [確定]，就會顯示 [事件處理常式攔截事件] 訊息。  
  
## <a name="see-also"></a>請參閱

- [Implements 陳述式](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [介面](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface 陳述式](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Event 陳述式](../../../../visual-basic/language-reference/statements/event-statement.md)
