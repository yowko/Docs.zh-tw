---
title: "如何：使用 Windows Form TextBox 控制項建立密碼文字方塊 | Microsoft Docs"
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
  - "密碼方塊, 建立"
  - "文字方塊中的 PasswordChar 屬性"
  - "密碼, 輸入遮罩"
  - "密碼, 密碼文字方塊"
  - "TextBox 控制項 [Windows Form], 輸入密碼"
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用 Windows Form TextBox 控制項建立密碼文字方塊
密碼方塊屬於 Windows Form 文字方塊，當使用者輸入字串時會出現替代符號。  
  
### 若要建立密碼文字方塊  
  
1.  將 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.TextBox.PasswordChar%2A> 屬性設定為特定字元。  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A> 屬性指定文字方塊中出現的字元。  例如，如果您希望密碼方塊中出現星號，請將 \[屬性\] 視窗中的 <xref:System.Windows.Forms.TextBox.PasswordChar%2A> 屬性指定為 \*。  然後，無論使用者在文字方塊中輸入什麼字元時，都會顯示星號。  
  
2.  \(選擇性的\) 設定 <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> 屬性。  此項屬性定義可在文字方塊中輸入的字元數。  如果超過長度限制，系統會發出嗶聲並且不再接受字元輸入。  請注意，您可能不想進行這項作業，因為想要破解密碼的駭客可能會利用密碼的最大長度來猜測密碼。  
  
     以下的程式碼範例顯示如何初始化最多可接受 14 個字元長度的文字方塊，並且以星號取代字串。  這個`InitializeMyControl` 必須經由呼叫才能執行，無法自動執行。  
  
    > [!IMPORTANT]
    >  在文字方塊上使用 <xref:System.Windows.Forms.TextBox.PasswordChar%2A> 屬性，有助於確保看到使用者輸入密碼的他人，無法判定使用者的密碼。  這個安全性措施並不涵蓋由於應用程式邏輯的緣故，而發生的任何種類之密碼儲存或傳送。  因為輸入的文字並沒有以任何方式加密，所以您應該將其視為機密資料處理。  即使看起來不是這樣，該密碼仍然會被視為純文字字串處理 \(除非您已實作其他安全性措施\)。  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.TextBox>   
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [如何：控制 Windows Form TextBox 控制項的插入點](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [如何：建立唯讀文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [如何：將引號放入字串中](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [如何：在 Windows Form TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [如何：檢視 Windows Form TextBox 控制項中的多行](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)