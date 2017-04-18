---
title: "如何：控制 Windows Form TextBox 控制項的插入點 | Microsoft Docs"
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
  - "插入點, TextBox 控制項"
  - "文字方塊, 控制插入點"
  - "TextBox 控制項 [Windows Form], 插入點"
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：控制 Windows Form TextBox 控制項的插入點
當 Windows Form <xref:System.Windows.Forms.TextBox> 控制項先接收到焦點 \(Focus\) 時，文字方塊中的預設插入點會出現在現存文字的左邊。  使用者可以藉由鍵盤或滑鼠來移動插入點。  如果離開文字方塊，而後再取得焦點時，插入點會出現在最後一次出現的地方。  
  
 在某些情況下，此項行為會讓使用者倉皇失措。  在文書處理應用程式中，使用者也許會預期新的字元會出現在任何現存的文字後。  在資料項目應用程式中，使用者也許會預期新的字元會取代任何現存的項目。  <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 和 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 屬性可修改行為以符合您的需求。  
  
### 若要控制 TextBox 控制項中的插入點  
  
1.  將 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性設定至適當值。  將插入點設為零時，插入點會立即移至第一個字元的左邊。  
  
2.  \(選擇性\) 將 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 屬性設定為所要選取的文字長度。  
  
     以下的程式碼會一直傳回插入點為 0。  `TextBox1_Enter` 事件處理常式必須繫結至此控制項；如需相關資訊，請參閱 [在 Windows Form 中建立事件處理常式](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)。  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## 預設會將此插入點設定為可見的  
 只有當 <xref:System.Windows.Forms.TextBox> 控制項的定位順序是第一個時，新表單中的 <xref:System.Windows.Forms.TextBox> 插入點才會預設為可見的。  否則，插入點只會在您使用鍵盤或滑鼠提供 <xref:System.Windows.Forms.TextBox> 焦點時才會顯示。  
  
#### 若要讓新表單中的文字方塊插入點預設為可見的  
  
-   將 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性設定為 `0`。  
  
## 請參閱  
 <xref:System.Windows.Forms.TextBox>   
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [如何：使用 Windows Form TextBox 控制項建立密碼文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [如何：建立唯讀文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [如何：將引號放入字串中](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [如何：在 Windows Form TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [如何：檢視 Windows Form TextBox 控制項中的多行](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)