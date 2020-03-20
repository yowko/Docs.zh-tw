---
title: 如何：傳送資料至作用中的 MDI 子系
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
ms.openlocfilehash: 563be8494cb84dc74b45985d3ba74e4b6a07eb8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182488"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>如何：傳送資料至作用中的 MDI 子系
通常，在[多文檔介面 （MDI） 應用程式的](multiple-document-interface-mdi-applications.md)上下文中，您需要將資料發送到活動子視窗，例如當使用者將剪貼簿的資料粘貼到 MDI 應用程式中時。  
  
> [!NOTE]
> 有關驗證哪個子視窗具有焦點並將其內容發送到剪貼簿的資訊，請參閱[確定活動 MDI 子視窗](how-to-determine-the-active-mdi-child.md)。  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>從剪貼簿將資料發送到活動 MDI 子視窗  
  
1. 在方法中，將剪貼簿上的文本複製到活動子表單的活動控制項。  
  
    > [!NOTE]
    > 此示例假定有一個 MDI 父表單`Form1`（ ） 具有一個或多個包含控制項的<xref:System.Windows.Forms.RichTextBox>MDI 子視窗。 有關詳細資訊，請參閱創建[MDI 父表單](how-to-create-mdi-parent-forms.md)。  
  
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
  
## <a name="see-also"></a>另請參閱

- [多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)
- [如何：建立 MDI 父表單](how-to-create-mdi-parent-forms.md)
- [如何：建立 MDI 子表單](how-to-create-mdi-child-forms.md)
- [如何：決定作用中的 MDI 子系](how-to-determine-the-active-mdi-child.md)
- [如何：安排 MDI 子表單](how-to-arrange-mdi-child-forms.md)
