---
title: HOW TO：傳送資料至作用中的 MDI 子系
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
ms.openlocfilehash: f4399d8548eff76aaa4effae6da7239cd3b0284b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343710"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>HOW TO：傳送資料至作用中的 MDI 子系
內容中，通常[多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)，您必須將資料傳送至作用中的子視窗，例如當使用者將資料從剪貼簿貼到 MDI 應用程式。  
  
> [!NOTE]
>  正在驗證哪一個子視窗有焦點，並將其內容傳送到剪貼簿的相關資訊，請參閱[判斷使用中的 MDI 子系](how-to-determine-the-active-mdi-child.md)。  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>若要將資料傳送至作用中的 MDI 子視窗中，從剪貼簿  
  
1. 在方法中，將文字複製到剪貼簿上到作用中的子表單的作用中的控制項。  
  
    > [!NOTE]
    >  這個範例假設沒有 MDI 父表單 (`Form1`)，其包含的一或多個 MDI 子視窗<xref:System.Windows.Forms.RichTextBox>控制項。 如需詳細資訊，請參閱 <<c0> [ 建立 MDI 父表單](how-to-create-mdi-parent-forms.md)。  
  
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
- [HOW TO：建立 MDI 父表單](how-to-create-mdi-parent-forms.md)
- [HOW TO：建立 MDI 子表單](how-to-create-mdi-child-forms.md)
- [HOW TO：決定作用中的 MDI 子系](how-to-determine-the-active-mdi-child.md)
- [HOW TO：排列 MDI 子表單](how-to-arrange-mdi-child-forms.md)
