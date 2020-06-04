---
title: 定義類別
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
ms.openlocfilehash: 646c6ce307131f3edba194af19920eade9c1753c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389110"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>逐步解說：定義類別 (Visual Basic)

本逐步解說示範如何定義類別，您可以用它來建立物件。 它也會示範如何將屬性和方法新增至新的類別，以及如何初始化物件。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>若要定義類別
  
1. 按一下 **[檔案**] 功能表上的 [**新增專案**] 來建立專案。 [新增專案]  對話方塊隨即出現。  
  
2. 從 Visual Basic 專案範本清單中選取 [Windows 應用程式]，以顯示新的專案。  
  
3. 按一下 [**專案**] 功能表上的 [**加入類別**]，將新的類別加入至專案。 [加入新項目] **** 對話方塊隨即出現。  
  
4. 選取 [**類別**] 範本。  
  
5. 將新類別命名為 `UserNameInfo.vb` ，然後按一下**Add** [新增] 以顯示新類別的程式碼。  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > 您可以使用 [Visual Basic 程式**代碼編輯器**]，輸入 `Class` 關鍵字並在後面加上新類別的名稱，以將類別新增至啟動表單。 [程式**代碼編輯器**] `End Class` 會為您提供對應的語句。  
  
6. 在和語句之間加入下列程式碼，以定義類別的私用欄位 `Class` `End Class` ：  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     將欄位宣告為， `Private` 表示它只能在類別中使用。 您可以使用存取修飾詞（例如 `Public` ，提供更多存取權），將欄位從類別外部提供。 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../declared-elements/access-levels.md)。  
  
7. 藉由新增下列程式碼來定義類別的屬性：  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. 藉由新增下列程式碼來定義類別的方法：  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. 藉由新增名為的程式，為新的類別定義參數化的函式 `Sub New` ：  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New`建立以這個類別為基礎的物件時，會自動呼叫此函式。 此函式會設定保留使用者名稱的欄位值。  
  
## <a name="to-create-a-button-to-test-the-class"></a>若要建立按鈕來測試類別
  
1. 將 [啟動表單] 變更為 [設計] 模式，方法是以滑鼠右鍵按一下**方案總管**中的名稱，然後按一下 [ **View Designer**]。 根據預設，Windows 應用程式專案的啟動表單名為 form1.vb。 然後會出現主要表單。  
  
2. 將按鈕新增至主要表單，然後按兩下以顯示 `Button1_Click` 事件處理常式的程式碼。 新增下列程式碼以呼叫測試程式：  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>執行應用程式
  
1. 按 F5 鍵執行您的應用程式。 按一下表單上的按鈕以呼叫測試程式。 它會顯示一則訊息，說明原始的 `UserName` 是 "摩爾，胡，"，因為程式呼叫了 `Capitalize` 物件的方法。  
  
2. 按一下 [確定]**** 來解除訊息方塊。 此程式 `Button1 Click` 會變更屬性的值 `UserName` ，並顯示一則訊息，指出的新值 `UserName` 為 "Worden，Joe"。  
  
## <a name="see-also"></a>另請參閱

- [物件導向程式設計 (Visual Basic)](../../concepts/object-oriented-programming.md)
- [物件和類別](index.md)
