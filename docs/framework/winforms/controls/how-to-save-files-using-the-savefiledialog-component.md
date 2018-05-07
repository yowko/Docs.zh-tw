---
title: 如何：使用 SaveFileDialog 元件儲存檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
ms.openlocfilehash: ca6ca5adbbe20a438ba936778ba71f1a163b40e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>如何：使用 SaveFileDialog 元件儲存檔案
<xref:System.Windows.Forms.SaveFileDialog>元件可讓使用者瀏覽檔案系統，並選取要儲存檔案。 對話方塊會傳回使用者在對話方塊中所選取之檔案的路徑和名稱。 不過，您必須撰寫程式碼，以實際將檔案寫入至磁碟。  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a>使用 SaveFileDialog 元件儲存檔案  
  
-   顯示 [儲存檔案] 對話方塊，並呼叫方法來儲存使用者所選取的檔案。  
  
     使用<xref:System.Windows.Forms.SaveFileDialog>元件的<xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>方法來儲存檔案。 這個方法可讓您<xref:System.IO.Stream>可以寫入的物件。  
  
     使用下列範例<xref:System.Windows.Forms.DialogResult>屬性來取得檔案的名稱和<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法來儲存檔案。 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>方法會提供要寫入至檔案資料流。  
  
     在下列範例中，沒有<xref:System.Windows.Forms.Button>控制指派給它的映像。 當您按一下按鈕，<xref:System.Windows.Forms.SaveFileDialog>元件具現化且允許型別.gif、.jpeg、.bmp 檔案的篩選條件。 如果在 [儲存檔案] 對話方塊中選取這類型的檔案，則會儲存按鈕的影像。  
  
    > [!IMPORTANT]
    >  取得或設定<xref:System.Windows.Forms.FileDialog.FileName%2A>屬性，您的組件需要權限層級授與由<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>類別。 若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。 如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
     這個範例假設您的表單具有<xref:System.Windows.Forms.Button>用來控制其<xref:System.Windows.Forms.ButtonBase.Image%2A>屬性設定為型別.gif、.jpeg 或.bmp 檔案。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.FileDialog>類別的<xref:System.Windows.Forms.FileDialog.FilterIndex%2A>屬性 (即繼承，因為屬於<xref:System.Windows.Forms.SaveFileDialog>類別) 會使用 1 為基底的索引。 如果您要撰寫程式碼，以特定格式來儲存資料 (例如，以純文字與二進位格式儲存檔案)，則這十分重要。 下列範例具有這個屬性。  
  
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
                safe_cast\<System::IO::FileStream*>(  
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
  
     (Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     如需寫入檔案資料流的詳細資訊，請參閱<xref:System.IO.FileStream.BeginWrite%2A>和<xref:System.IO.FileStream.Write%2A>。  
  
    > [!NOTE]
    >  特定控制項，例如<xref:System.Windows.Forms.RichTextBox>控制，能夠儲存檔案。 如需詳細資訊，請參閱 MSDN Online Library 技術文件 [Essential Code for Windows Forms Dialog Boxes](http://go.microsoft.com/fwlink/?LinkID=102575) (Windows Forms 對話方塊的基本程式碼) 的＜SaveFileDialog 元件＞一節。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [SaveFileDialog 元件](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
