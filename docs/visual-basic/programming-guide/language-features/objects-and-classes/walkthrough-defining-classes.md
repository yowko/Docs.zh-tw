---
title: "定義類別 (Visual Basic) |Microsoft 文件"
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
- execution, ending
- objects [Visual Basic], initializing
- Initialize event
- files, closing
- programs, quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event
- execution, stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
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
ms.openlocfilehash: aeaa5c2bb85c1a642da15c6a29546cf065380e27
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-defining-classes-visual-basic"></a>逐步解說：定義類別 (Visual Basic)
本逐步解說示範如何定義類別，您可以用它來建立物件。 它也說明如何將屬性和方法新增至新的類別，並示範如何初始化物件。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-a-class"></a>若要定義類別  
  
1.  按一下 建立專案**新的專案**上**檔案**功能表。 [ **新增專案** ] 對話方塊隨即出現。  
  
2.  從清單選取 Windows 應用程式[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案範本，以顯示新的專案。  
  
3.  將新類別加入專案，依序按一下**加入類別**上**專案**功能表。 **加入新項目** 對話方塊隨即出現。  
  
4.  選取**類別**範本。  
  
5.  將新類別`UserNameInfo.vb`，然後按一下 **新增**以顯示新的類別的程式碼。  
  
     [!code-vb[VbVbalrOOP #&5;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  您可以使用[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]**程式碼編輯器**將類別加入至啟動表單中，輸入`Class`關鍵字後面加上新類別的名稱。 **程式碼編輯器**提供對應`End Class`為您的陳述式。  
  
6.  藉由加入下列程式碼之間定義類別的私用欄位`Class`和`End Class`陳述式︰  
  
     [!code-vb[VbVbalrOOP #&7;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     宣告欄位設為`Private`表示中，才可以使用它。 您可以讓欄位可從類別外使用存取修飾詞，例如`Public`可提供更多存取權。 如需詳細資訊，請參閱[在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
7.  藉由加入下列程式碼中定義類別的屬性︰  
  
     [!code-vb[VbVbalrOOP #&8;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  定義類別的方法，加入下列程式碼︰  
  
     [!code-vb[VbVbalrOOP #&9;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. 加入名為程序來定義新類別的參數化建構函式`Sub New`:  
  
     [!code-vb[VbVbalrOOP #&10;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     `Sub New`根據此類別的物件建立時自動呼叫建構函式。 這個建構函式設定的保留使用者名稱欄位的值。  
  
### <a name="to-create-a-button-to-test-the-class"></a>若要建立一個按鈕來測試類別  
  
1.  以滑鼠右鍵按一下其名稱變更為設計模式的啟動表單**方案總管] 中**，然後按一下 [**檢視表設計工具**。 根據預設，Windows 應用程式專案啟動表單稱為 Form1.vb。 接著會出現在主要表單。  
  
2.  將按鈕加入至主表單，然後按兩下以顯示的程式碼`Button1_Click`事件處理常式。 新增下列程式碼來呼叫測試程序︰  
  
     [!code-vb[VbVbalrOOP #&12;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a>執行應用程式  
  
1.  按 f5 鍵執行應用程式。 按一下表單上的按鈕來呼叫測試程序。 它會顯示訊息，指出原始`UserName`是 「 摩爾 BOBBY 」，因為呼叫此程序`Capitalize`物件的方法。  
  
2.  按一下 **確定**來解除訊息方塊。 `Button1 Click`程序變更的值`UserName`屬性，並顯示訊息，指出新的值`UserName`是 「 Worden Joe 」。  
  
## <a name="see-also"></a>另請參閱  
 [物件導向程式設計](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)   
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

