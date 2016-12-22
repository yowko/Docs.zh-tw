---
title: "Walkthrough: Manipulating Files and Directories in Visual Basic | Microsoft Docs"
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
  - "files, reading text"
  - "reading files, text"
  - "I/O [Visual Basic], walkthroughs"
  - "text, writing to files"
  - "text, reading from files"
  - "reading text from files, walkthroughs"
  - "Visual Basic code, file access"
  - "files, writing text"
  - "I/O [Visual Basic], writing text to files"
  - "file access, walkthroughs"
  - "writing to files, walkthroughs"
  - "I/O [Visual Basic], reading text from files"
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
caps.latest.revision: 49
caps.handback.revision: 49
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Manipulating Files and Directories in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

這個逐步解說將介紹 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中 I\/O 檔案的基本原則。  它將說明如何建立一個小型應用程式，此應用程式會列出並檢查目錄中的文字檔。  這個應用程式會為每個選取的文字檔，提供檔案屬性及第一行內容。  還有一個將資訊寫入記錄檔的選項。  
  
 本逐步解說會使用 `My.Computer.FileSystem Object` 的成員，這些成員可從 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 取得。  如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.FileIO.FileSystem>。  在本逐步解說的最後，將提供同等的範例，它會使用來自 <xref:System.IO> 命名空間的類別。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### 若要建立專案  
  
1.  在 \[**檔案**\] 功能表上，按一下 \[**新增專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即出現。  
  
2.  在 \[**已安裝的範本**\] 窗格中，展開 \[**Visual Basic**\]，然後按一下 \[**Windows**\]。  在中間的 \[**範本**\] 窗格中，按一下 \[**Windows Form 應用程式**\]。  
  
3.  在 \[**名稱**\] 方塊中輸入 `FileExplorer` 設定專案名稱，然後按一下 \[**確定**\]。  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] 會將專案加入 \[**方案總管**\] 中，並開啟 Windows Form 設計工具。  
  
4.  將下表中的控制項加入表單，並設定控制項屬性的對應值。  
  
    |控制項|屬性|值|  
    |---------|--------|-------|  
    |**ListBox**|**名稱**|`filesListBox`|  
    |**Button**|**名稱**<br /><br /> **文字**|`browseButton`<br /><br /> 瀏覽|  
    |**Button**|**名稱**<br /><br /> **文字**|`examineButton`<br /><br /> 檢查|  
    |**CheckBox**|**名稱**<br /><br /> **文字**|`saveCheckBox`<br /><br /> 儲存結果|  
    |**FolderBrowserDialog**|**名稱**|`FolderBrowserDialog1`|  
  
### 若要選取資料夾，並列出資料夾中的檔案  
  
1.  按兩下表單上的控制項來建立 `browseButton` 的 `Click` 事件處理常式。  程式碼編輯器立即開啟。  
  
2.  將下列程式碼加入至 `Click` 事件處理常式。  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     `FolderBrowserDialog1.ShowDialog` 呼叫會開啟 \[**瀏覽資料夾**\] 對話方塊。  在使用者按一下 \[**確定**\] 後，<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> 屬性會以引數的形式傳送到 `ListFiles` 方法，此方法會在下一個步驟加入。  
  
3.  加入下列 `ListFiles` 方法。  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     這個程式碼會先清除 \[**ListBox**\]。  
  
     接著，<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> 方法會擷取一個字串集合，一個字串代表目錄中的一個檔案。  `GetFiles` 方法會接受搜尋模式引數，以擷取符合特定模式的檔案。  在這個範例中，只會傳回副檔名為 .txt 的檔案。  
  
     然後，會將 `GetFiles` 方法所傳回的字串加入至 \[**ListBox**\]。  
  
4.  執行應用程式。  按一下 \[**瀏覽**\] 按鈕。  在 \[**瀏覽資料夾**\] 對話方塊中，瀏覽至包含 .txt 檔案的資料夾，然後選取該資料夾，再按一下 \[**確定**\]。  
  
     `ListBox` 包含所選資料夾中的 .txt 檔案清單。  
  
5.  停止執行應用程式。  
  
### 若要取得檔案屬性和文字檔內容  
  
1.  按兩下表單上的控制項來建立 `examineButton` 的 `Click` 事件處理常式。  
  
2.  將下列程式碼加入至 `Click` 事件處理常式。  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     這個程式碼會驗證 `ListBox` 中是否有選取項目，  然後從 `ListBox` 取得檔案路徑項目。  <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> 方法是用來檢查檔案是否仍然存在。  
  
     檔案路徑會以引數形式傳送到 `GetTextForOutput` 方法，此方法會在下一個步驟加入。  此方法會傳回包含檔案資訊的字串。  檔案資訊會出現在 \[**MessageBox**\] 中。  
  
3.  加入下列 `GetTextForOutput` 方法。  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     這個程式碼會使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> 方法取得檔案參數。  檔案參數會加入至 <xref:System.Text.StringBuilder>。  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> 方法會將檔案內容讀入 <xref:System.IO.StreamReader>。  第一行內容會從 `StreamReader` 取得，並加入至 `StringBuilder`。  
  
4.  執行應用程式。  按一下 \[**瀏覽**\] 瀏覽至包含 .txt 檔案的資料夾。  按一下 \[**確定**\]。  
  
     選取 `ListBox` 中的檔案，然後按一下 \[**檢查**\]。  `MessageBox` 隨即顯示檔案資訊。  
  
5.  停止執行應用程式。  
  
### 若要加入記錄項目  
  
1.  將下列程式碼加入至 `examineButton_Click` 事件處理常式的結尾。  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     這個程式碼會設定記錄檔路徑，將記錄檔放在與所選檔案相同的目錄中。  記錄項目的文字會設為目前的日期和時間，後面接著檔案資訊。  
  
     `append` 引數設為 `True` 的 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> 方法是用來建立記錄項目。  
  
2.  執行應用程式。  瀏覽至文字檔並在 `ListBox` 中加以選取，然後選取 \[**儲存結果**\] 核取方塊，再按一下 \[**檢查**\]。  驗證記錄項目是否已寫入 `log.txt` 檔案。  
  
3.  停止執行應用程式。  
  
### 若要使用目前的目錄  
  
1.  在表單上按兩下以建立 `Form1_Load` 的事件處理常式。  
  
2.  將下列程式碼加入至事件處理常式。  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     這個程式碼會將資料夾瀏覽器的預設目錄設為目前的目錄。  
  
3.  執行應用程式。  第一次按下 \[**瀏覽**\] 時，\[**瀏覽資料夾**\] 對話方塊會開啟目前的目錄。  
  
4.  停止執行應用程式。  
  
### 若要選擇性地啟用控制項  
  
1.  加入下列 `SetEnabled` 方法。  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     `SetEnabled` 方法會根據 `ListBox` 中是否有選取項目，啟用或停用控制項。  
  
2.  按兩下表單上的 `ListBox` 控制項來建立 `filesListBox` 的 `SelectedIndexChanged` 事件處理常式。  
  
3.  在新的 `filesListBox_SelectedIndexChanged` 事件處理常式中加入 `SetEnabled` 的呼叫。  
  
4.  在 `browseButton_Click` 事件處理常式的結尾加入 `SetEnabled` 的呼叫。  
  
5.  在 `Form1_Load` 事件處理常式的結尾加入 `SetEnabled` 的呼叫。  
  
6.  執行應用程式。  如果 `ListBox` 中沒有選取項目，則會停用 \[**儲存結果**\] 核取方塊和 \[**檢查**\] 按鈕。  
  
## 使用 My.Computer.FileSystem 的完整範例  
 完整範例如下。  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## 使用 System.IO 的完整範例  
 下列同等的範例會使用來自 <xref:System.IO> 命名空間的類別，而非使用 `My.Computer.FileSystem` 物件。  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## 請參閱  
 <xref:System.IO>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>   
 [Walkthrough: Manipulating Files by Using .NET Framework Methods](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)