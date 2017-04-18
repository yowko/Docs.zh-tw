---
title: "如何：使用 SaveFileDialog 元件儲存檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "檔案, 儲存"
  - "OpenFile 方法, 使用 SaveFileDialog 元件儲存檔案"
  - "SaveFileDialog 元件, 儲存檔案"
  - "儲存檔案"
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：使用 SaveFileDialog 元件儲存檔案
<xref:System.Windows.Forms.SaveFileDialog> 元件可讓使用者瀏覽檔案系統，然後選取要儲存的檔案。  對話方塊會傳回使用者在對話方塊選取的檔案名稱與路徑。  然而，您必須撰寫程式碼，才能將檔案寫入磁碟。  
  
### 若要使用 SaveFileDialog 元件儲存檔案  
  
-   顯示 \[**儲存檔案**\] 對話方塊，然後呼叫方法儲存使用者選取的檔案。  
  
     使用 <xref:System.Windows.Forms.SaveFileDialog> 元件的 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法儲存檔案。  這個方法提供您可以寫入的 <xref:System.IO.Stream> 物件。  
  
     下列範例使用 <xref:System.Windows.Forms.DialogResult> 屬性取得檔案名稱，並使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法儲存檔案。  <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法提供寫入檔案的資料流。  
  
     在下列範例中，<xref:System.Windows.Forms.Button> 控制項具有指定的影像。  按一下按鈕時，<xref:System.Windows.Forms.SaveFileDialog> 元件會藉由允許 .gif、.jpeg 和 .bmp 檔案類型的篩選常式具現化。  如果在 \[儲存檔案\] 對話方塊中選取這種類型的檔案，就會儲存按鈕的影像。  
  
    > [!IMPORTANT]
    >  若要取得或設定 <xref:System.Windows.Forms.FileDialog.FileName%2A> 屬性，組件需要 <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName> 類別授與的權限層級。  如果您正在部分信任的內容中執行動作，則會因權限不足而導致處理序擲回例外狀況。  如需詳細資訊，請參閱[程式碼存取安全性的基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
     這個範例假設您的表單具有 <xref:System.Windows.Forms.Button> 控制項，而且其 <xref:System.Windows.Forms.ButtonBase.Image%2A> 屬性設定為 .gif、.jpeg 或 .bmp 的檔案類型。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.FileDialog> 類別的 <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> 屬性 \(由於繼承的關係，而成為 <xref:System.Windows.Forms.SaveFileDialog> 類別的一部分\) 使用以一起始的索引。  如果撰寫程式碼，以特定格式儲存資料 \(例如以純文字與二進位的格式儲存檔案\)，這個屬性就非常重要。  以下範例將說明這個屬性的功能。  
  
    ```vb  
    Private Sub Button2_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button2.Click  
       ' Displays a SaveFileDialog so the user can save the Image  
       ' assigned to Button2.  
       Dim saveFileDialog1 As New SaveFileDialog()  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"  
       saveFileDialog1.Title = "Save an Image File"  
       saveFileDialog1.ShowDialog()  
  
       ' If the file name is not an empty string open it for saving.  
       If saveFileDialog1.FileName <> "" Then  
          ' Saves the Image via a FileStream created by the OpenFile method.  
          Dim fs As System.IO.FileStream = Ctype _  
             (saveFileDialog1.OpenFile(), System.IO.FileStream)  
          ' Saves the Image in the appropriate ImageFormat based upon the  
          ' file type selected in the dialog box.  
          ' NOTE that the FilterIndex property is one-based.  
          Select Case saveFileDialog1.FilterIndex  
             Case 1  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Jpeg)  
  
             Case 2  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Bmp)  
  
             Case 3  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Gif)  
           End Select  
  
           fs.Close()  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button2_Click(object sender, System.EventArgs e)  
    {  
       // Displays a SaveFileDialog so the user can save the Image  
       // assigned to Button2.  
       SaveFileDialog saveFileDialog1 = new SaveFileDialog();  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
       saveFileDialog1.Title = "Save an Image File";  
       saveFileDialog1.ShowDialog();  
  
       // If the file name is not an empty string open it for saving.  
       if(saveFileDialog1.FileName != "")  
       {  
          // Saves the Image via a FileStream created by the OpenFile method.  
          System.IO.FileStream fs =   
             (System.IO.FileStream)saveFileDialog1.OpenFile();  
          // Saves the Image in the appropriate ImageFormat based upon the  
          // File type selected in the dialog box.  
          // NOTE that the FilterIndex property is one-based.  
          switch(saveFileDialog1.FilterIndex)  
          {  
             case 1 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Jpeg);  
             break;  
  
             case 2 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Bmp);  
             break;  
  
             case 3 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Gif);  
             break;  
          }  
  
       fs.Close();  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       System::Void button2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays a SaveFileDialog so the user can save the Image  
          // assigned to Button2.  
          SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();  
          saveFileDialog1->Filter =   
             "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
          saveFileDialog1->Title = "Save an Image File";  
          saveFileDialog1->ShowDialog();  
          // If the file name is not an empty string, open it for saving.  
          if(saveFileDialog1->FileName != "")  
          {  
             // Saves the Image through a FileStream created by  
             // the OpenFile method.  
             System::IO::FileStream ^ fs =   
                safe_cast<System::IO::FileStream*>(  
                saveFileDialog1->OpenFile());  
             // Saves the Image in the appropriate ImageFormat based on  
             // the file type selected in the dialog box.  
             // Note that the FilterIndex property is one based.  
             switch(saveFileDialog1->FilterIndex)  
             {  
                case 1 :  
                   this->button2->Image->Save(fs,  
                      System::Drawing::Imaging::ImageFormat::Jpeg);  
                   break;  
                case 2 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Bmp);  
                   break;  
                case 3 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Gif);  
                   break;  
             }  
          fs->Close();  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     如需寫入檔案資料流的詳細資訊，請參閱 [FileStream.BeginWrite 方法](frlrfSystemIOFileStreamClassBeginWriteTopic)和 [FileStream.Write 方法](https://msdn.microsoft.com/en-us/library/system.io.filestream.write.aspx)。  
  
    > [!NOTE]
    >  特定控制項 \(例如 <xref:System.Windows.Forms.RichTextBox> 控制項\) 能夠儲存檔案。  如需詳細資訊，請參閱 MSDN Online Library 技術文件 [Essential Code for Windows Forms Dialog Boxes](http://go.microsoft.com/fwlink/?LinkID=102575) 的＜SaveFileDialog Component＞一節。  
  
## 請參閱  
 <xref:System.Windows.Forms.SaveFileDialog>   
 [SaveFileDialog 元件](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)