---
title: "TextBox 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TextBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "文字方塊, 加入"
  - "TextBox 控制項 [Windows Form], 關於 TextBox 控制項"
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# TextBox 控制項概觀 (Windows Form)
Windows Form 文字方塊係用於取得使用者輸入或顯示文字。  <xref:System.Windows.Forms.TextBox> 控制項通常使用於可編輯的文字，雖然該控制項也可以是唯讀。  文字方塊可以顯示多行文字、以控制項的大小來將文字換行和加入基本的格式。  <xref:System.Windows.Forms.TextBox> 控制項會為顯示的文字或輸入該控制項的文字提供單一格式樣式。  若要顯示多種類型的格式化文字，請使用 <xref:System.Windows.Forms.RichTextBox> 控制項。  如需詳細資訊，請參閱 [RichTextBox 控制項概觀](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md)。  
  
## 使用文字方塊控制項  
 控制項所顯示的文字會包含在 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性中。  預設情況下，可在文字方塊中輸入最多 2048 個字元。  如果將 <xref:System.Windows.Forms.TextBox.Multiline%2A> 屬性設定為 `true`，您最多可輸入 32KB 的文字。  <xref:System.Windows.Forms.TextBox.Text%2A> 屬性可以在設計階段時使用 \[屬性\] 視窗、在執行階段時使用程式碼，或在執行階段時由使用者輸入來進行設定。  可在執行階段時，藉由讀取 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性來擷取文字方塊目前的內容。  
  
 下列程式碼範例在執行階段時設定控制項中的文字。  這個`InitializeMyControl` 必須經由呼叫才能執行，無法自動執行。  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## 請參閱  
 <xref:System.Windows.Forms.TextBox>   
 [如何：控制 Windows Form TextBox 控制項的插入點](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [如何：使用 Windows Form TextBox 控制項建立密碼文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [如何：建立唯讀文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [如何：將引號放入字串中](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [如何：在 Windows Form TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [如何：檢視 Windows Form TextBox 控制項中的多行](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)