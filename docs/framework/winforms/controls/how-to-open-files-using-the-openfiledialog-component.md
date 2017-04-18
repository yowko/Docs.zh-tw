---
title: "如何：使用 OpenFileDialog 元件開啟檔案 | Microsoft Docs"
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
  - "檔案, 使用 OpenFileDialog 元件開啟"
  - "OpenFile 方法"
  - "OpenFile 方法, OpenFileDialog 元件"
  - "OpenFileDialog 元件, 開啟檔案"
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：使用 OpenFileDialog 元件開啟檔案
<xref:System.Windows.Forms.OpenFileDialog> 元件讓使用者能瀏覽自己電腦上或網路中任何電腦上的資料夾，然後選取一個或多個要開啟的檔案。  對話方塊會傳回使用者在對話方塊選取的檔案名稱與路徑。  
  
 使用者在選取要開啟的檔案後，有兩種開啟檔案機制的方法。  如果您慣用檔案資料流，可建立 <xref:System.IO.StreamReader> 類別的執行個體。  或者，可以使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法開啟選取的檔案。  
  
 下列第一個範例包含 <xref:System.Security.Permissions.FileIOPermission> 使用權限檢查 \(如「安全性提示」中所述\)，但可讓您存取檔案名稱。  您可從本機電腦、內部網路和網際網路區域使用這項技術。  第二個方法也會進行 <xref:System.Security.Permissions.FileIOPermission> 使用權限檢查，但是更適合內部網路或網際網路區域的應用程式。  
  
### 若要使用 OpenFileDialog 元件將檔案開啟為資料流  
  
1.  顯示 \[**開啟檔案**\] 對話方塊，然後呼叫方法開啟使用者選取的檔案。  
  
     一個方法是使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示 \[開啟檔案\] 對話方塊，再使用 <xref:System.IO.StreamReader> 類別的執行個體開啟檔案。  
  
     下列範例使用 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式來開啟 <xref:System.Windows.Forms.OpenFileDialog> 元件的執行個體。  在檔案選定而且使用者按一下 \[**確定**\] 後，對話方塊中選取的檔案就會開啟。  在這個情況中，內容是顯示在訊息方塊中，僅表示檔案資料流已經讀取。  
  
    > [!IMPORTANT]
    >  若要取得或設定 <xref:System.Windows.Forms.FileDialog.FileName%2A> 屬性，組件需要 <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName> 類別授與的權限層級。  如果您正在部分信任的內容中執行動作，則會因權限不足而導致處理序擲回例外狀況。  如需詳細資訊，請參閱[程式碼存取安全性的基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
     此範例假設您的表單具有 <xref:System.Windows.Forms.Button> 控制項和 <xref:System.Windows.Forms.OpenFileDialog> 元件。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  如需從檔案資料流讀取的詳細資訊，請參閱 [FileStream.BeginRead 方法](frlrfSystemIOFileStreamClassBeginReadTopic)和 [FileStream.Read 方法](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx)。  
  
### 若要使用 OpenFileDialog 元件將檔案開啟為檔案  
  
1.  使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示對話方塊，並使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法開啟檔案。  
  
     <xref:System.Windows.Forms.OpenFileDialog> 元件的 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法會傳回撰寫檔案的位元組。  這些位元組能提供讀取的資料流。  在下列範例中，<xref:System.Windows.Forms.OpenFileDialog> 元件是利用其上的 "cursor" 選常式進行具現化的，可讓使用者僅選擇副檔名為 `.cur` 的檔案。  如果選擇 `.cur`  檔案，表單的指標會設定為選取的指標。  
  
    > [!IMPORTANT]
    >  若要呼叫 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法，組件需要 <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName> 類別授與的權限層級。  如果您正在部分信任的內容中執行動作，則會因權限不足而導致處理序擲回例外狀況。  如需詳細資訊，請參閱[程式碼存取安全性的基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
     這個範例假設您的表單具有 <xref:System.Windows.Forms.Button> 控制項。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.OpenFileDialog>   
 [OpenFileDialog 元件](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)