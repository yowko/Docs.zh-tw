---
title: 定義類別 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
ms.openlocfilehash: aac30a8b0272ae6c141138a91585953237ab8098
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650637"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>逐步解說：定義類別 (Visual Basic)

本逐步解說示範如何定義類別，您可以使用它來建立物件。 它也示範如何將屬性和方法新增至新的類別，並示範如何初始化物件。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>若要定義類別
  
1.  建立專案，依序按一下**新專案**上**檔案**功能表。 [ **新增專案** ] 對話方塊隨即出現。  
  
2.  從 Visual Basic 專案範本，以顯示新的專案清單中選取 Windows 應用程式。  
  
3.  將新類別加入專案，依序按一下**加入類別**上**專案**功能表。 [新增項目] 對話方塊隨即出現。  
  
4.  選取**類別**範本。  
  
5.  將新類別`UserNameInfo.vb`，然後按一下 **新增**以顯示新類別的程式碼。  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  您可以使用 Visual Basic**程式碼編輯器**若要將類別加入至啟動表單中，輸入`Class`關鍵字後面接著新類別的名稱。 **程式碼編輯器**提供對應`End Class`為您的陳述式。  
  
6.  藉由加入下列程式碼之間定義類別的私用欄位`Class`和`End Class`陳述式：  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     宣告為欄位`Private`表示它可以只在類別內使用。 您可以提供欄位從類別外使用存取修飾詞，例如`Public`可提供更多的存取。 如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
7.  加入下列程式碼定義類別的屬性：  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8.  加入下列程式碼定義類別的方法：  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. 加入名為程序來定義新類別的參數化建構函式`Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New`根據此類別的物件建立時自動呼叫建構函式。 這個建構函式設定的保留使用者名稱欄位的值。  
  
## <a name="to-create-a-button-to-test-the-class"></a>若要建立的按鈕來測試類別
  
1.  以滑鼠右鍵按一下其名稱變更為設計模式的啟動表單**方案總管] 中**，然後按一下 [**檢視表設計工具**。 根據預設，Windows 應用程式專案啟動表單名為 Form1.vb。 即會出現在主要表單。  
  
2.  將按鈕加入主要表單，然後按兩下以顯示的程式碼`Button1_Click`事件處理常式。 加入下列程式碼來呼叫測試程序：  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>執行應用程式
  
1.  按 F5 執行您的應用程式。 按一下呼叫測試程序表單上的按鈕。 它會顯示訊息，指出原始`UserName`是"暄 BOBBY"，因為該程序呼叫`Capitalize`物件的方法。  
  
2.  按一下**確定**來解除訊息方塊。 `Button1 Click`程序的值變更`UserName`屬性，並顯示訊息，指出新的值`UserName`是"Worden Joe"。  
  
## <a name="see-also"></a>另請參閱

[物件導向程式設計 (Visual Basic)](../../concepts/object-oriented-programming.md)  
[物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)