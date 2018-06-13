---
title: 如何：使用 OpenFileDialog 元件開啟檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d7e1ebb319576aa7a38d55d8cb9f3652626966b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542271"
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a>如何：使用 OpenFileDialog 元件開啟檔案
<xref:System.Windows.Forms.OpenFileDialog>元件可讓使用者瀏覽其電腦或網路上的任何電腦的資料夾，然後選取一或多個要開啟的檔案。 對話方塊會傳回使用者在對話方塊中所選取之檔案的路徑和名稱。  
  
 使用者選取要開啟的檔案之後，開啟檔案的機制有兩種方式。 如果您想要使用的檔案資料流，您可以建立的執行個體<xref:System.IO.StreamReader>類別。 或者，您可以使用<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法，以開啟選取的檔案。  
  
 下列第一個範例牽涉到<xref:System.Security.Permissions.FileIOPermission>權限檢查 （如 「 安全性下方的附註 」 中所述），但可讓您存取的檔名。 您可以從本機電腦、內部網路和網際網路區域使用這項技術。 第二個方法也會執行<xref:System.Security.Permissions.FileIOPermission>權限檢查，但比較適合內部網路或網際網路區域中的應用程式。  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a>使用 OpenFileDialog 元件開啟檔案作為資料流  
  
1.  顯示 [開啟檔案] 對話方塊，並呼叫方法來開啟使用者所選取的檔案。  
  
     其中一個方法是使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法來顯示開啟檔案 對話方塊中，使用的執行個體<xref:System.IO.StreamReader>類別來開啟檔案。  
  
     使用下列範例<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，以開啟的執行個體<xref:System.Windows.Forms.OpenFileDialog>元件。 如果選擇檔案且使用者按一下 [確定]，則會開啟在對話方塊中所選取的檔案。 在此情況下，內容會顯示在訊息方塊中，只是為了顯示已讀取的檔案資料流。  
  
    > [!IMPORTANT]
    >  取得或設定<xref:System.Windows.Forms.FileDialog.FileName%2A>屬性，您的組件需要權限層級授與由<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>類別。 若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。 如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
     這個範例假設您的表單具有<xref:System.Windows.Forms.Button>控制項和<xref:System.Windows.Forms.OpenFileDialog>元件。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
       }  
    ```  
  
     (Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  如需從檔案資料流讀取的詳細資訊，請參閱<xref:System.IO.FileStream.BeginRead%2A>和<xref:System.IO.FileStream.Read%2A>。  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a>使用 OpenFileDialog 元件開啟檔案作為檔案  
  
1.  使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以顯示對話方塊和<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法來開啟檔案。  
  
     <xref:System.Windows.Forms.OpenFileDialog>元件的<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法會傳回撰寫檔案的位元組。 這些位元組提供您可從中讀取的資料流。 在下列範例中，<xref:System.Windows.Forms.OpenFileDialog>元件具現化"cursor"篩選器，讓使用者選擇只具有副檔名的檔案且`.cur`。 如果選擇 `.cur` 檔案，則表單的資料指標會設定為所選取的資料指標。  
  
    > [!IMPORTANT]
    >  若要呼叫<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法，您的組件需要權限層級授與由<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>類別。 若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。 如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
     這個範例假設您的表單具有<xref:System.Windows.Forms.Button>控制項。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
       }  
    ```  
  
     (Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog 元件](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
