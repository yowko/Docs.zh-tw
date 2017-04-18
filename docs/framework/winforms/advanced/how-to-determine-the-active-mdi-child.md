---
title: "如何：決定作用中的 MDI 子系 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "子表單"
  - "剪貼簿, 複製資料至"
  - "MDI, 啟動表單"
  - "MDI, 子視窗"
  - "MDI, 找出焦點"
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：決定作用中的 MDI 子系
有時，您會想要提供一個在控制項執行的命令，而此控制項在目前作用中的子表單上取得焦點 \(Focus\)。  例如，假設您想要從子表單的文字方塊複製選取文字到剪貼簿。  您將會建立一個程序，使用標準 \[編輯\] 功能表中 \[複製\] 功能表項目的 <xref:System.Windows.Forms.Control.Click> 事件，將選取文字複製到剪貼簿。  
  
 由於 MDI 應用程式對於同一子表單可以有許多執行個體，因此程序需要知道應使用的表單是哪一個。  若要指定正確的表單，請使用 <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> 屬性，傳回取得焦點或最近變成作用中的子表單。  
  
 如果表單上有數個控制項，您也需要指定作用中的控制項是哪一個。  <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> 屬性與 <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> 屬性類似，都會傳回在作用中子表單上取得焦點的控制項。  下列程序說明可從子表單功能表、MDI 表單中的功能表或工具列按鈕呼叫的複製程序。  
  
### 若要決定作用中的 MDI 子系 \(複製其文字至剪貼簿\)  
  
1.  在一個方法中，將作用中子表單的作用中控制項文字複製到剪貼簿。  
  
    > [!NOTE]
    >  本範例假設 MDI 父表單 \(`Form1`\) 具有一或多個包含 <xref:System.Windows.Forms.RichTextBox> 控制項的 MDI 子視窗。  如需詳細資訊，請參閱[建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)。  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
             }  
          }  
          catch  
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
  
    ```  
  
## 請參閱  
 [多重文件介面 \(MDI\) 應用程式](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)   
 [如何：建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [如何：建立 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [如何：傳送資料至作用中的 MDI 子系](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)   
 [如何：安排 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)