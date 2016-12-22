---
title: "Walkthrough: Defining Classes (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "execution, ending"
  - "objects [Visual Basic], initializing"
  - "Initialize event"
  - "files, closing"
  - "programs, quitting"
  - "code, exiting"
  - "objects [Visual Basic], creating"
  - "program termination"
  - "classes [Visual Basic], walkthroughs"
  - "class modules, walkthroughs"
  - "Terminate event"
  - "execution, stopping"
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Defining Classes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

這個逐步解說會示範如何定義類別，然後您就可從類別來建立物件。  同時也顯示如何將屬性和方法加入至新類別，並示範如何初始化物件。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### 若要定義類別  
  
1.  按一下 \[**檔案**\] 功能表上的 \[**新增專案**\] 來建立專案。  \[**新增專案**\] 對話方塊隨即出現。  
  
2.  從 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 專案範本清單中選取 \[Windows 應用程式\]，以顯示新的專案。  
  
3.  按一下 \[**專案**\] 功能表中的 \[**加入類別**\]，在專案中加入一個新的類別。  \[**加入新項目**\] 對話方塊隨即出現。  
  
4.  選取 \[**類別**\] 範本。  
  
5.  將新的類別命名為 `UserNameInfo.vb`，然後按一下 \[**加入**\] 以顯示新類別的程式碼。  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  您可以使用 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 的 \[**程式碼編輯器**\]，在新類別的名稱之前輸入 `Class` 關鍵字，將類別加入至啟動表單中。  \[**程式碼編輯器**\] 會自動提供對應的 `End Class` 陳述式。  
  
6.  將下列程式碼加入到 `Class` 和 `End Class` 陳述式之間，以定義類別的私用欄位：  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     將欄位宣告為 `Private`，表示只能在該類別內使用它。  您可以使用存取修飾詞 \(例如 `Public`\)，提供範圍更廣的存取，使這些欄位變成可以從此類別的外部使用。  如需詳細資訊，請參閱 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
7.  加入下列程式碼以定義類別的屬性：  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  加入下列程式碼以定義類別的方法：  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. 加入名為 `Sub New` 的程序，以定義新類別的參數化建構函式：  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     在建立以此類別為基礎的物件時，會自動呼叫 `Sub New` 建構函式。  這個建構函式會設定保存使用者名稱的欄位值。  
  
### 若要建立一個按鈕來測試類別  
  
1.  以滑鼠右鍵按一下 \[**方案總管**\] 中的啟動表單名稱，再按一下 \[**設計工具檢視**\]，將此表單變更為設計模式。  根據預設，Windows 應用程式專案的啟動表單名稱為 Form1.vb。  然後，主要表單隨即出現。  
  
2.  在主表單中加入一個按鈕，並按兩下此按鈕，以顯示 `Button1_Click` 事件處理常式的程式碼。  加入下列程式碼以呼叫測試程序：  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### 若要執行您的應用程式  
  
1.  按 F5 鍵以執行您的應用程式。  在表單上按一下按鈕以呼叫測試程序。  它會顯示一則訊息，說明原始的 `UserName` 是 "MOORE, BOBBY"，因為程序呼叫了物件的 `Capitalize` 方法。  
  
2.  按一下 \[**確定**\] 來解除訊息方塊。  `Button1 Click` 程序會變更 `UserName` 屬性值，並顯示一則訊息，表示 `UserName` 的新值是 "Worden, Joe"。  
  
## 請參閱  
 [物件導向程式設計](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)   
 [Objects and Classes](../../../../visual-basic/reference/command-line-compiler/index.md)