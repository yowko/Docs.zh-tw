---
title: "使用 .NET Framework 方法管理檔案 (Visual Basic) | Microsoft Docs"
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
- I/O [Visual Basic], walkthroughs
- text files, writing to
- reading text files
- text, writing to files
- files, searching
- StreamReader class, walkthroughs
- files, accessing
- I/O [Visual Basic], writing text to files
- writing to files, walkthroughs
- StreamWriter class, walkthroughs
- text files, reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
caps.latest.revision: 18
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e8bf73f32dba51455542778ed91ef3bfd2898754
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>逐步解說：使用 .NET Framework 方法管理檔案 (Visual Basic)
本逐步解說示範如何使用 <xref:System.IO.StreamReader> 類別以開啟和讀取檔案、檢查是否正在存取檔案、在 <xref:System.IO.StreamReader> 類別執行個體讀取的檔案內搜尋字串，並使用 <xref:System.IO.StreamWriter> 類別寫入檔案。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-the-application"></a>建立應用程式  
 若要啟動 [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] 並開始專案，您可以建立表單，以供使用者寫入至指定的檔案。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  在 [檔案]**** 功能表上，選取 [新增專案]****。  
  
2.  按一下 [新增專案]**** 窗格的 [Windows 應用程式]****。  
  
3.  在 [名稱]**** 方塊中，輸入 `MyDiary` 並按一下 [確定]****。  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] 即會將專案新增到方案總管****中，並開啟 **Windows Forms 設計工具**。  
  
4.  將下表中的控制項新增至表單，並設定其屬性的對應值。  
  
|**物件**|**屬性**|**值**|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|**Name**<br /><br /> **文字**|`Submit`<br /><br /> **提交項目**|  
|<xref:System.Windows.Forms.Button>|**Name**<br /><br /> **文字**|`Clear`<br /><br /> **清除項目**|  
|<xref:System.Windows.Forms.TextBox>|**Name**<br /><br /> **文字**<br /><br /> **多行**|`Entry`<br /><br /> **請輸入某些內容。**<br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a>寫入檔案  
 若要新增透過應用程式寫入檔案的功能，請使用 <xref:System.IO.StreamWriter> 類別。 <xref:System.IO.StreamWriter> 是專為以特定的編碼方式輸出字元而量身打造，而<xref:System.IO.Stream> 類別則是針對位元組輸入和輸出而設計。 使用 <xref:System.IO.StreamWriter> 將資訊行寫入標準文字檔案。 如需 <xref:System.IO.StreamWriter> 類別的詳細資訊，請參閱 <xref:System.IO.StreamWriter>。  
  
#### <a name="to-add-writing-functionality"></a>若要新增寫入功能  
  
1.  從 [檢視]**** 功能表上，選擇 [程式碼]**** 以開啟程式碼編輯器。  
  
2.  由於應用程式會參考 <xref:System.IO> 命名空間，因此請在表單類別宣告開始之前 (其會開始 `Public Class Form1`)，於程式碼開頭加入下列陳述式。  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     在寫入檔案之前，您必須建立 <xref:System.IO.StreamWriter> 類別的執行個體。  
  
3.  從 [檢視]**** 功能表上，選擇 [設計工具]**** 以返回 **Windows Forms 設計工具**。 按兩下 `Submit` 按鈕，建立該按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，然後加入下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  Visual Studio 整合式開發環境 (IDE) 會返回程式碼編輯器，並在事件處理常式中放入您應該新增程式碼的位置插入點。  
  
1.  若要寫入檔案，請使用 <xref:System.IO.StreamWriter> 類別的 <xref:System.IO.StreamWriter.Write%2A> 方法。 將下列程式碼新增至 `Dim fw As StreamWriter` 正後方。 您不用擔心系統會在找不到檔案時擲回例外狀況，因為若檔案不存在，系統會加以建立。  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  您可在 `Dim ReadString As String` 正後方加入下列程式碼，確定使用者無法提交空白項目。  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  由於此為日記，因此使用者會需要針對每個項目指派日期。 在 `fw = New StreamWriter("C:\MyDiary.txt", True)` 之後插入下列程式碼，以將 `Today` 變數設為目前的日期。  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  最後，附加程式碼以清除 <xref:System.Windows.Forms.TextBox>。 將下列程式碼新增至 `Clear` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a>新增日記的顯示功能  
 在這個區段中，您會新增功能以顯示 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中的最新項目。 您也可以新增 <xref:System.Windows.Forms.ComboBox> 以顯示各種項目，使用者即可從中選取要在 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中顯示的項目。 <xref:System.IO.StreamReader> 類別的執行個體會從 `MyDiary.txt` 進行讀取。 如同 <xref:System.IO.StreamWriter> 類別一般，<xref:System.IO.StreamReader> 是與文字檔案搭配使用。  
  
 在本節逐步解說中，請將下表的控制項新增至表單，並設定其屬性的對應值。  
  
|控制項|屬性|值|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|**Name**<br /><br /> **可見**<br /><br /> **Size**<br /><br /> **多行**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Name**<br /><br /> **文字**|`Display`<br /><br /> **顯示**|  
|<xref:System.Windows.Forms.Button>|**Name**<br /><br /> **文字**|`GetEntries`<br /><br /> **取得項目**|  
|<xref:System.Windows.Forms.ComboBox>|**Name**<br /><br /> **文字**<br /><br /> **已啟用**|`PickEntries`<br /><br /> **選取項目**<br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a>若要填入下拉式方塊  
  
1.  系統會使用 `PickEntries`<xref:System.Windows.Forms.ComboBox> 來顯示使用者提交每個項目的日期，因此使用者可以從特定日期選取項目。 建立 `GetEntries` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  若要測試您的程式碼，請按 F5 以編譯應用程式，然後按一下 [取得項目]****。 按一下 <xref:System.Windows.Forms.ComboBox> 中的下拉式箭頭以顯示項目日期。  
  
#### <a name="to-choose-and-display-individual-entries"></a>若要選擇並顯示個別項目  
  
1.  建立 `Display` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  若要測試您的程式碼，請按 F5 以編譯應用程式，然後提交項目。 按一下 取得項目****，並從 <xref:System.Windows.Forms.ComboBox> 中選取一個項目，然後按一下 顯示****。 選取的項目內容會出現在 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中。  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a>讓使用者可以刪除或修改項目  
 最後，您可以包含其他功能，讓使用者可以利用 `DeleteEntry` 和 `EditEntry` 按鈕，刪除或修改項目。 未顯示項目時，這兩個按鈕皆為停用狀態。  
  
 將下表的控制項新增至表單，並設定其屬性的對應值。  
  
|控制項|屬性|值|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|**Name**<br /><br /> **文字**<br /><br /> **已啟用**|`DeleteEntry`<br /><br /> **刪除項目**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Name**<br /><br /> **文字**<br /><br /> **已啟用**|`EditEntry`<br /><br /> **編輯項目**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Name**<br /><br /> **文字**<br /><br /> **已啟用**|`SubmitEdit`<br /><br /> **提交編輯**<br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a>若要啟用項目的刪除和修改功能  
  
1.  將下列程式碼新增至 `Display` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件，於 `DisplayEntry.Text = ReadString` 後方。  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  建立 `DeleteEntry` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並新增下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  當使用者顯示項目時，`EditEntry` 按鈕即變成啟用。 將下列程式碼新增至 `Display` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件，於 `DisplayEntry.Text = ReadString` 後方。  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  建立 `EditEntry` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並新增下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  建立 `SubmitEdit` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並新增下列程式碼。  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 若要測試您的程式碼，請按 F5 以編譯應用程式。 按一下 [取得項目]****，並選取項目，然後按一下 [顯示]****。 項目會出現在 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中。 按一下 [編輯項目]****。 項目會出現在 `Entry`<xref:System.Windows.Forms.TextBox> 中。 編輯 `Entry`<xref:System.Windows.Forms.TextBox> 中的項目，然後按一下 [提交編輯]****。 開啟 `MyDiary.txt` 檔案，確認您的修正。 現在，選取項目，然後按一下 [刪除項目]****。 當 <xref:System.Windows.Forms.MessageBox> 要求進行確認時，請按一下 [確定]****。 關閉應用程式，並開啟 `MyDiary.txt` 以確認刪除。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.StreamWriter>   
 [逐步解說](../../../../visual-basic/walkthroughs.md)

