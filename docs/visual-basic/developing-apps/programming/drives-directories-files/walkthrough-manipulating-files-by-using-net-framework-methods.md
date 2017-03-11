---
title: "Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic) | Microsoft Docs"
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
  - "I/O [Visual Basic], walkthroughs"
  - "text files, writing to"
  - "reading text files"
  - "text, writing to files"
  - "files, searching"
  - "StreamReader class, walkthroughs"
  - "files, accessing"
  - "I/O [Visual Basic], writing text to files"
  - "writing to files, walkthroughs"
  - "StreamWriter class, walkthroughs"
  - "text files, reading"
  - "I/O [Visual Basic], reading text from files"
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本逐步解說會示範如何使用 <xref:System.IO.StreamReader> 類別開啟及讀取檔案、檢查是否正在存取該檔案、搜尋使用 <xref:System.IO.StreamReader> 類別之執行個體讀取的檔案內字串，以及使用 <xref:System.IO.StreamWriter> 類別寫入檔案。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
## 建立應用程式  
 啟動 [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs-md.md)]，並且藉由建立使用者可用於寫入至指定之檔案的表單，以便開始專案。  
  
#### 若要建立專案  
  
1.  在 \[**檔案**\] 功能表上選取 \[**新增專案**\]。  
  
2.  在 \[**新增專案**\] 窗格中，按一下 \[**Windows 應用程式**\]。  
  
3.  在 \[**名稱**\] 方塊中輸入 `MyDiary`，再按一下 \[**確定**\]。  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs-md.md)] 會將專案加入 \[**方案總管**\] 中，並開啟 \[**Windows Form 設計工具**\]。  
  
4.  將下表中的控制項加入至表單，並且設定相對應的屬性值。  
  
||||  
|-|-|-|  
|**物件**|**屬性**|**值**|  
|<xref:System.Windows.Forms.Button>|**名稱**<br /><br /> **文字**|`Submit`<br /><br /> 送出項目|  
|<xref:System.Windows.Forms.Button>|**名稱**<br /><br /> **文字**|`Clear`<br /><br /> 清除項目|  
|<xref:System.Windows.Forms.TextBox>|**名稱**<br /><br /> **文字**<br /><br /> **Multiline**|`Entry`<br /><br /> 請輸入<br /><br /> `False`|  
  
## 寫入至檔案  
 若要加入透過應用程式寫入檔案的能力，請使用 <xref:System.IO.StreamWriter> 類別。  <xref:System.IO.StreamWriter> 是為特定編碼方式的字元輸出而設計，而 <xref:System.IO.Stream> 類別則是為位元組輸入和輸出而設計。  使用 <xref:System.IO.StreamWriter> 將資訊行寫入至標準文字檔。  如需 <xref:System.IO.StreamWriter> 類別的詳細資訊，請參閱 <xref:System.IO.StreamWriter>。  
  
#### 若要加入寫入功能  
  
1.  從 \[**檢視**\] 功能表，選擇 \[**程式碼**\] 以開啟 \[程式碼編輯器\]。  
  
2.  因為應用程式會參考 <xref:System.IO> 命名空間，所以請將下列陳述式加在程式碼的起始處 \(需在以 `Public Class Form1` 開頭的表單類別宣告之前\)。  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_1.vb)]  
  
     在寫入檔案之前，您必須建立 <xref:System.IO.StreamWriter> 類別的執行個體。  
  
3.  從 \[**檢視**\] 功能表，選擇 \[**設計工具**\] 以返回 \[**Windows Form 設計工具**\]。  按兩下 \[`Submit`\] 按鈕，建立按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，然後加入下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_2.vb)]  
  
> [!NOTE]
>  Visual Studio 整合式開發環境 \(IDE\) 將會返回 \[程式碼編輯器\]，並且將插入點放在事件處理常式內您該加入程式碼的位置。  
  
1.  若要寫入至檔案，請使用 <xref:System.IO.StreamWriter> 類別的 <xref:System.IO.StreamWriter.Write%2A> 方法。  將下列程式碼直接加到 `Dim fw As StreamWriter` 後方。  您不需要擔心如果找不到檔案會擲回例外狀況，因為如果檔案不存在，就會建立檔案。  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_3.vb)]  
  
2.  請將下列程式碼直接加在 `Dim ReadString As String` 之後，以便確定使用者無法送出空白項目。  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_4.vb)]  
  
3.  因為這是日記簿，所以使用者會想要指派每個項目的日期。  將下列程式碼插入到 `fw = New StreamWriter("C:\MyDiary.txt", True)` 之後，將變數 `Today` 設定為目前日期。  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_5.vb)]  
  
4.  最後，附加程式碼以清除 <xref:System.Windows.Forms.TextBox>。  將下列程式碼加入至 `Clear` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_6.vb)]  
  
## 將顯示功能加入至日記簿  
 在本節中，您將加入一個可在 `DisplayEntry` <xref:System.Windows.Forms.TextBox> 中顯示最新項目的功能。  另外，也可以加入能顯示各種項目的 <xref:System.Windows.Forms.ComboBox>，使用者可以由此處選取要在 `DisplayEntry` <xref:System.Windows.Forms.TextBox> 中顯示的項目。  <xref:System.IO.StreamReader> 類別的執行個體會從 `MyDiary.txt` 讀取。  如同 <xref:System.IO.StreamWriter> 類別，<xref:System.IO.StreamReader> 主要用於文字檔。  
  
 針對本逐步解說章節，將下表中的控制項加入至表單，並且設定相對應的屬性 \(Property\) 值。  
  
|控制項|屬性|值|  
|---------|--------|-------|  
|<xref:System.Windows.Forms.TextBox>|**名稱**<br /><br /> **Visible**<br /><br /> **Size**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**名稱**<br /><br /> **文字**|`Display`<br /><br /> Display|  
|<xref:System.Windows.Forms.Button>|**名稱**<br /><br /> **文字**|`GetEntries`<br /><br /> 取得項目|  
|<xref:System.Windows.Forms.ComboBox>|**名稱**<br /><br /> **文字**<br /><br /> **Enabled**|`PickEntries`<br /><br /> 選取項目<br /><br /> `False`|  
  
#### 若要填入下拉式方塊  
  
1.  `PickEntries` <xref:System.Windows.Forms.ComboBox> 用於顯示使用者送出每個項目的日期，讓使用者可以從特定日期選取項目。  建立 `GetEntries` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_7.vb)]  
  
2.  若要測試程式碼，請按 F5 編譯應用程式，然後按一下 \[**取得項目**\]。  按一下 <xref:System.Windows.Forms.ComboBox> 中的下拉箭頭，以顯示項目日期。  
  
#### 若要選擇並顯示個別項目  
  
1.  建立 `Display` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並且加入下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_8.vb)]  
  
2.  若要測試程式碼，請按 F5 編譯應用程式，然後送出項目。  按一下 \[**取得項目**\]，從 <xref:System.Windows.Forms.ComboBox> 選取項目，再按一下 \[**顯示**\]。  所選取項目的內容會顯示在 `DisplayEntry` <xref:System.Windows.Forms.TextBox> 中。  
  
## 讓使用者能夠刪除或修改項目  
 最後，您可以納入其他功能，讓使用者能夠使用 `DeleteEntry` 和 `EditEntry` 按鈕，刪除或修改項目。  這兩個按鈕在項目顯示之前會維持在停用狀態。  
  
 將下表中的控制項加入至表單，並且設定相對應的屬性值。  
  
|控制項|屬性|值|  
|---------|--------|-------|  
|<xref:System.Windows.Forms.Button>|**名稱**<br /><br /> **文字**<br /><br /> **Enabled**|`DeleteEntry`<br /><br /> 刪除項目<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**名稱**<br /><br /> **文字**<br /><br /> **Enabled**|`EditEntry`<br /><br /> 編輯項目<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**名稱**<br /><br /> **文字**<br /><br /> **Enabled**|`SubmitEdit`<br /><br /> 送出編輯結果<br /><br /> `False`|  
  
#### 若要啟用項目的刪除和修改功能  
  
1.  將下列程式碼加入至 `Display` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件，放在 `DisplayEntry.Text = ReadString` 之後。  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_9.vb)]  
  
2.  建立 `DeleteEntry` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_10.vb)]  
  
3.  當使用者顯示項目時，`EditEntry` 按鈕會變成可用狀態。  將下列程式碼加入至 `Display` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件，放在 `DisplayEntry.Text = ReadString` 之後。  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_11.vb)]  
  
4.  建立 `EditEntry` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_12.vb)]  
  
5.  建立 `SubmitEdit` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_1_13.vb)]  
  
 若要測試程式碼，請按 F5 編譯應用程式。  按一下 \[**取得項目**\]、選取項目，再按一下 \[**顯示**\]。  項目會顯示在 `DisplayEntry` <xref:System.Windows.Forms.TextBox> 中。  按一下 \[**編輯項目**\]。  項目會顯示在 `Entry` <xref:System.Windows.Forms.TextBox> 中。  編輯 `Entry` <xref:System.Windows.Forms.TextBox> 中的項目，並且按一下 \[**送出編輯結果**\]。  開啟 `MyDiary.txt` 檔案以確認修正。  現在，選取項目並按一下 \[**刪除項目**\]。  當 <xref:System.Windows.Forms.MessageBox> 要求確認時，請按一下 \[**確定**\]。  關閉應用程式並開啟 `MyDiary.txt` 以確認刪除。  
  
## 請參閱  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.StreamWriter>   
 [Walkthroughs](../../../../visual-basic/walkthroughs.md)