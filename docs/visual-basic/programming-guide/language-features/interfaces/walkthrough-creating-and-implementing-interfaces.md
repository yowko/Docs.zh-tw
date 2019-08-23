---
title: 建立和執行介面 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 62e301e9eb366d14b58088d3e2cda3b567d17f5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923312"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>逐步解說：建立和執行介面 (Visual Basic)

介面會描述屬性、方法和事件的特性, 但會將執行詳細資料保持在結構或類別的最上方。  
  
 本逐步解說示範如何宣告和執行介面。  
  
> [!NOTE]
> 本逐步解說並未提供如何建立使用者介面的相關資訊。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>若要定義介面
  
1. 開啟新的 Visual Basic Windows 應用程式專案。  
  
2. 按一下 [**專案**] 功能表上的 [**加入模組**], 將新的模組加入至專案。  
  
3. 為新模組`Module1.vb`命名, 然後按一下 [**新增**]。 新模組的程式碼隨即顯示。  
  
4. 在`TestInterface` 和`Module` `Module1` 語句之間`Interface TestInterface`輸入, 然後按 enter 鍵, 以定義中名為的介面。 `End Module` [程式**代碼編輯器**] `Interface`會縮排關鍵字`End Interface` , 並加入語句以形成程式碼區塊。  
  
5. 藉由將`Interface`下列程式碼放在和`End Interface`語句之間, 定義介面的屬性、方法和事件:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>實作

 您可能會注意到, 用來宣告介面成員的語法與用來宣告類別成員的語法不同。 這種差異反映了介面不能包含實作為程式碼的事實。  
  
### <a name="to-implement-the-interface"></a>若要執行介面
  
1. 加入名`ImplementationClass`為的類別, 方法是將下列`Module1`語句加入至`End Interface`語句之後但在`End Module`語句之前, 然後按 enter 鍵:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     如果您是在整合式開發環境中工作, 則當您按下 enter `End Class`時, 程式**代碼編輯器**會提供相符的語句。  
  
2. 將下列`Implements`語句新增至`ImplementationClass`, 以命名類別所要執行的介面:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     與類別或結構頂端的其他專案分開列出時, `Implements`語句會指出類別或結構會執行介面。  
  
     如果您在整合式開發環境中工作, 程式`TestInterface` **代碼編輯器**會在您按下 enter 時, 執行所需的類別成員, 而您可以略過下一個步驟。  
  
3. 如果您不是在整合式開發環境中工作, 則必須執行介面`MyInterface`的所有成員。 將下列程式碼新增`ImplementationClass`至, `Event1`以`Method1`執行、 `Prop1`和:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements`語句會命名要實作為介面和介面成員。  
  
4. 藉`Prop1`由將私用欄位新增至儲存屬性值的類別, 完成的定義:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     `pval`從屬性 get 存取子傳回的值。  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     `pval`在屬性集存取子中設定的值。  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. 新增下列`Method1`程式碼, 以完成的定義。  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>測試介面的執行
  
1. 在 **方案總管**中, 以滑鼠右鍵按一下專案的 啟動 表單, 然後按一下 **查看程式碼**。 編輯器會顯示您的啟動表單的類別。 根據預設, 會呼叫`Form1`啟動表單。  
  
2. 將下列`testInstance`欄位新增`Form1`至類別:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     藉由宣告`WithEvents` `Form1`為, 類別可以處理其事件。 `testInstance`  
  
3. 將下列事件處理常式新增至`Form1`類別, 以處理所引發`testInstance`的事件:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. 將名`Test`為的`Form1`副程式新增至類別, 以測試執行類別:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     程式會建立執行之類別的實例`testInstance` 、將該實例指派給欄位、設定屬性,以及透過介面執行方法。`MyInterface` `Test`  
  
5. 新增程式碼, 以`Test`從啟動窗`Form1 Load`體的程式呼叫程式:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. `Test`按 F5 鍵執行程式。 [Prop1 已設定為 9] 訊息隨即顯示。 按一下 [確定] 之後, 就會顯示「Method1 的 X 參數是5」的訊息。 按一下 [確定], 就會顯示 [事件處理常式攔截事件] 訊息。  
  
## <a name="see-also"></a>另請參閱

- [Implements 陳述式](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [介面](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface 陳述式](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Event 陳述式](../../../../visual-basic/language-reference/statements/event-statement.md)
