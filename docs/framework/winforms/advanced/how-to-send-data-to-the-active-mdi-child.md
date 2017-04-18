---
title: "如何：傳送資料至作用中的 MDI 子系 | Microsoft Docs"
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
  - "剪貼簿, 取得資料"
  - "剪貼簿, 貼上"
  - "MDI, 傳送資料至表單"
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：傳送資料至作用中的 MDI 子系
通常在[多重文件介面 \(MDI\) 應用程式](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)的內容中，必須傳送資料到現用子視窗，例如當使用者將資料從剪貼簿貼到 MDI 應用程式時。  
  
> [!NOTE]
>  如需檢查焦點落在哪個子視窗以及將此子視窗內容傳送到剪貼簿的詳細資訊，請參閱[找出作用中的 MDI 子視窗](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)。  
  
### 若要從剪貼簿傳送資料到作用中的 MDI 子視窗  
  
1.  在一個方法中，將剪貼簿上的文字複製到作用中子表單的作用中控制項。  
  
    > [!NOTE]
    >  本範例假設 MDI 父表單 \(`Form1`\) 具有一或多個包含 <xref:System.Windows.Forms.RichTextBox> 控制項的 MDI 子視窗。  如需詳細資訊，請參閱[建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)。  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the   
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try   
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the   
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();                 
                }  
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
 [如何：決定作用中的 MDI 子系](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)   
 [如何：安排 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)