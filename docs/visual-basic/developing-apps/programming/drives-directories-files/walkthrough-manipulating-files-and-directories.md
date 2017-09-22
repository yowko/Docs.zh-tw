---
title: "在 Visual Basic 中管理檔案和目錄"
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
- files, reading text
- reading files, text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files, walkthroughs
- Visual Basic code, file access
- files, writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files, walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
caps.latest.revision: 49
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e66d062df07fc23dfbd5d509e08ccd08813db15
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>逐步解說：在 Visual Basic 中管理檔案和目錄
本逐步解說提供 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 中檔案 I/O 的基本概念簡介。 其中說明如何建立一個小型應用程式，以提列並檢查目錄中的文字檔案。 針對每個選取的文字檔案，應用程式會提供檔案屬性和第一行內容。 您也可以選擇將資訊寫入記錄檔。  
  
 本逐步解說使用 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 所提供的 `My.Computer.FileSystem Object` 成員。 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.FileIO.FileSystem>。 本逐步解說最後會提供使用來自 <xref:System.IO> 命名空間之類別的對等範例。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>若要建立專案  
  
1.  按一下 [檔案] 功能表上的 [新增專案]。  
  
     [ **新增專案** ] 對話方塊隨即出現。  
  
2.  在 [已安裝的範本] 窗格中，展開 [Visual Basic]，然後按一下 [Windows]。 在中間的 [範本] 窗格中，按一下 [Windows Forms 應用程式]。  
  
3.  在 [名稱] 方塊中，輸入 `FileExplorer` 以設定專案名稱，然後按一下 [確定]。  
  
     [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 即會將專案新增到方案總管中，並開啟 Windows Forms 設計工具。  
  
4.  將下表的控制項新增至表單，並設定其屬性的對應值。  
  
    |控制項|屬性|值|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Name**|`filesListBox`|  
    |**Button**|**Name**<br /><br /> **文字**|`browseButton`<br /><br /> **瀏覽**|  
    |**Button**|**Name**<br /><br /> **文字**|`examineButton`<br /><br /> **檢查**|  
    |**CheckBox**|**Name**<br /><br /> **文字**|`saveCheckBox`<br /><br /> **儲存結果**|  
    |**FolderBrowserDialog**|**Name**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>若要選取資料夾，並列出資料夾中的檔案  
  
1.  按兩下表單的控制項，以建立 `browseButton` 的 `Click` 事件處理常式。 [程式碼編輯器] 隨即開啟。  
  
2.  將下列程式碼加入至 `Click` 事件處理常式。  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     `FolderBrowserDialog1.ShowDialog` 呼叫會開啟 [瀏覽資料夾] 對話方塊。 使用者按一下 [確定] 之後，系統會以引數形式將 <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> 屬性傳送給 `ListFiles` 方法，以在下一個步驟中加入。  
  
3.  新增下列 `ListFiles` 方法。  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     此程式碼會先清除 **ListBox**。  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> 方法接著會擷取一組字串，目錄中每個檔案一個字串。 `GetFiles` 方法可接受搜尋模式引數，以擷取符合特定模式的檔案。 在此範例中，僅會傳回副檔名為 .txt 的檔案。  
  
     隨即將 `GetFiles` 方法所傳回的字串新增至 **ListBox**。  
  
4.  執行應用程式。 按一下 [瀏覽] 按鈕。 在 [瀏覽資料夾] 對話方塊中，瀏覽至包含 .txt 檔案的資料夾，然後選取資料夾並按一下 [確定]。  
  
     `ListBox` 包含所選資料夾中的 .txt 檔案清單。  
  
5.  停止執行應用程式。  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>若要取得檔案的屬性以及文字檔案的內容  
  
1.  按兩下表單上的控制項，以建立 `examineButton` 的 `Click` 事件處理常式。  
  
2.  將下列程式碼加入至 `Click` 事件處理常式。  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     程式碼會驗證 `ListBox` 中已選取項目。 接著，它會從 `ListBox` 取得檔案路徑的項目。 <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> 方法用來檢查檔案是否仍然存在。  
  
     系統會以引數形式將檔案路徑傳送給 `GetTextForOutput` 方法，以在下一個步驟中加入。 這個方法會傳回字串，其中包含檔案資訊。 **MessageBox** 中會顯示檔案資訊。  
  
3.  新增下列 `GetTextForOutput` 方法。  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     程式碼使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> 方法來取得檔案參數。 檔案參數會新增至 <xref:System.Text.StringBuilder>。  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> 方法會將檔案內容讀入 <xref:System.IO.StreamReader>。 系統會由 `StreamReader` 取得第一行的內容，並將其新增至 `StringBuilder`。  
  
4.  執行應用程式。 按一下 [瀏覽]，並瀏覽至包含 .txt 檔案的資料夾。 按一下 [確定]。  
  
     選取 `ListBox` 中的檔案，然後按一下 [檢查]。 `MessageBox` 隨即顯示檔案資訊。  
  
5.  停止執行應用程式。  
  
### <a name="to-add-a-log-entry"></a>若要新增記錄項目  
  
1.  將下列程式碼加入 `examineButton_Click` 事件處理常式的結尾。  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     程式碼會將記錄檔路徑設為將記錄檔放入所選檔案的相同目錄中。 記錄項目的文字則會設為目前的日期和時間，後面接著檔案資訊。  
  
     將 `append` 引數設定為 `True` 的 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> 方法用來建立記錄項目。  
  
2.  執行應用程式。 瀏覽至文字檔案，在 `ListBox` 中加以選取，並選取 [儲存結果] 核取方塊，然後按一下 [檢查]。 確認記錄項目已寫入 `log.txt` 檔案。  
  
3.  停止執行應用程式。  
  
### <a name="to-use-the-current-directory"></a>若要使用目前的目錄  
  
1.  按兩下表單的控制項，以建立 `Form1_Load` 的事件處理常式。  
  
2.  將下列程式碼加入事件處理常式。  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     此程式碼會將資料夾瀏覽器的預設目錄設為目前的目錄。  
  
3.  執行應用程式。 當您首次按一下 [瀏覽] 時，[瀏覽資料夾] 對話方塊即會開啟至目前目錄。  
  
4.  停止執行應用程式。  
  
### <a name="to-selectively-enable-controls"></a>若要選擇性地啟用控制項  
  
1.  新增下列 `SetEnabled` 方法。  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     `SetEnabled` 方法會依據 `ListBox` 中是否選取項目，來啟用或停用控制項。  
  
2.  按兩下表單的 `ListBox` 控制項，以建立 `filesListBox` 的 `SelectedIndexChanged` 事件處理常式。  
  
3.  在新的 `filesListBox_SelectedIndexChanged` 事件處理常式中，新增 `SetEnabled` 的呼叫。  
  
4.  在 `browseButton_Click` 事件處理常式結尾，新增 `SetEnabled` 的呼叫。  
  
5.  在 `Form1_Load` 事件處理常式結尾，新增 `SetEnabled` 的呼叫。  
  
6.  執行應用程式。 如果 `ListBox` 中未選取項目，則會停用 [儲存結果] 核取方塊和 [檢查] 按鈕。  
  
## <a name="full-example-using-mycomputerfilesystem"></a>使用 My.Computer.FileSystem 的完整範例  
 下列是完整範例。  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a>使用 System.IO 的完整範例  
 下列對等範例使用來自 <xref:System.IO> 命名空間的類別，而不是使用 `My.Computer.FileSystem` 物件。  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>   
 [逐步解說：使用 .NET Framework 方法管理檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)

