---
title: "如何：在 Windows Form TextBox 控制項中選取文字 | Microsoft Docs"
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
  - "文字方塊, 以程式設計方式選取文字"
  - "文字, 以程式化的方式在文字方塊中選取"
  - "TextBox 控制項 [Windows Form], 以程式設計方式選取文字"
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 如何：在 Windows Form TextBox 控制項中選取文字
你可以程式設計的方式選取 Windows Form <xref:System.Windows.Forms.TextBox> 控制項中的文字。  例如，如果你建立搜尋特定字串文字的功能，則可選取此文字以視覺地警示找到字串位置的讀取器 \(Reader\)。  
  
### 若要以程式設計的方式選取文字  
  
1.  將 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性設定為要選取的文字的字首。  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性是用來指示文字字串內插入點的數字，其中 0 表示最左的位置。  如果 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性設定成大於或等於文字方塊中的字元數，則會將插入點放置在最後一個字元之後。  
  
2.  將 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 屬性設定為要選取的文字長度。  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 屬性是設定插入點寬度的數值。  將 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 設定為大於 0 的數字時，則會從目前的插入點開始選取相同的字元數。  
  
3.  \(選擇性\) 經由 <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> 屬性存取選取的文字。  
  
     以下的程式碼會在發生控制項的 <xref:System.Windows.Forms.Control.Enter> 事件時，選取文字方塊的內容。  這個範例會檢查文字方塊是否含有非 `null` 或空字串的 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性值。  當文字方塊接收焦點時，會選取文字方塊中的目前文字。  `TextBox1_Enter` 事件處理常式必須繫結至此控制項；如需相關資訊，請參閱 [如何：建立 Windows Form 的執行階段事件處理常式](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
     若要測試這個範例，請按下 TAB 鍵直到文字方塊取得焦點為止。  如果在文字方塊中按一下，就會取消選取文字。  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.TextBox>   
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [如何：控制 Windows Form TextBox 控制項的插入點](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [如何：使用 Windows Form TextBox 控制項建立密碼文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [如何：建立唯讀文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [如何：將引號放入字串中](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [如何：檢視 Windows Form TextBox 控制項中的多行](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)