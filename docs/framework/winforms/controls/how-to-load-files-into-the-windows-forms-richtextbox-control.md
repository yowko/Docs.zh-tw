---
title: "如何：將檔案載入 Windows Form RichTextBox 控制項 | Microsoft Docs"
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
  - "文字方塊, 顯示檔案"
  - "範例 [Windows Forms], 文字方塊"
  - ".rtf 檔案, 在 RichTextBox 控制項中開啟"
  - "RTF 檔案, 在 RichTextBox 控制項中開啟"
  - "文字檔案, 在 RichTextBox 控制項中顯示"
  - ".rtf 檔案, 在 RichTextBox 控制項中顯示"
  - "RichTextBox 控制項 [Windows Forms], 開啟檔案"
  - "RTF 檔案, 在 RichTextBox 控制項中顯示"
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：將檔案載入 Windows Form RichTextBox 控制項
Windows Forms <xref:System.Windows.Forms.RichTextBox> 控制項可以顯示純文字、Unicode 純文字或 Rich Text 格式 \(RTF\) 檔案。 執行方式是呼叫 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> 方法。 您也可以使用 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> 方法從資料流載入資料。 如需詳細資訊，請參閱<xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>。  
  
### 將檔案載入 RichTextBox 控制項  
  
1.  決定要使用 <xref:System.Windows.Forms.OpenFileDialog> 元件開啟的檔案路徑。 如需概觀說明，請參閱[OpenFileDialog 元件概觀](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).  
  
2.  呼叫 <xref:System.Windows.Forms.RichTextBox> 控制項的 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> 方法，指定要載入的檔案，也可指定檔案類型。 在下例中，要載入的檔案取自 <xref:System.Windows.Forms.OpenFileDialog> 元件的 <xref:System.Windows.Forms.FileDialog.FileName%2A> 屬性。 如果呼叫的方法以檔案名稱為其唯一引數，則檔案類型會假設為 RTF。 若要指定其他檔案類型，請呼叫以 <xref:System.Windows.Forms.RichTextBoxStreamType> 列舉值為其第二個引數的方法。  
  
     在下例中，按一下按鈕即會顯示 <xref:System.Windows.Forms.OpenFileDialog> 元件。 所選檔案會隨即開啟，並顯示在 <xref:System.Windows.Forms.RichTextBox> 控制項中。 本例假設表單有 `btnOpenFile` 按鈕。  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  若要執行此程序，您的組件可能需要由 <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName> 類別授與的權限層級。 若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。 如需詳細資訊，請參閱[Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)