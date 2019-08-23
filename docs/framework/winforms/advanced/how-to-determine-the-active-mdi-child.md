---
title: HOW TO：決定作用中的 MDI 子系
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
ms.openlocfilehash: 91100b37e4cae9041479b209e40034efe376df5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946225"
---
# <a name="how-to-determine-the-active-mdi-child"></a>作法：決定作用中的 MDI 子系
在某些情況下, 您會想要提供一個命令, 以在焦點放在目前使用中子表單的控制項上操作。 例如, 假設您想要從子表單的文字方塊中, 將選取的文字複製到剪貼簿。 您會建立一個程式, 使用<xref:System.Windows.Forms.Control.Click>標準 [編輯] 功能表上 [複製] 功能表項目的事件, 將選取的文字複製到剪貼簿。  
  
 由於 MDI 應用程式可以有多個相同子表單的實例, 因此程式需要知道要使用哪一個表單。 若要指定正確的格式, 請<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>使用屬性, 它會傳回具有焦點或最近使用中的子表單。  
  
 當您在表單上有數個控制項時, 您也必須指定要使用哪一個控制項。 <xref:System.Windows.Forms.Form.ActiveMdiChild%2A>如同屬性<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> , 屬性會將焦點放在使用中子表單上的控制項。 下列程式說明可從子表單功能表、MDI 表單上的功能表或工具列按鈕呼叫的複製程式。  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>判斷現用 MDI 子系 (將其文字複製到剪貼簿)  
  
1. 在方法內, 將現用子表單的作用中控制項文字複製到剪貼簿。  
  
    > [!NOTE]
    > 這個範例假設有一個 mdi 父表單 (`Form1`), 其中有一個或多個<xref:System.Windows.Forms.RichTextBox>包含控制項的 mdi 子視窗。 如需詳細資訊, 請參閱[建立 MDI 父表單](how-to-create-mdi-parent-forms.md)。  
  
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
  
## <a name="see-also"></a>另請參閱

- [多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)
- [如何：建立 MDI 父表單](how-to-create-mdi-parent-forms.md)
- [如何：建立 MDI 子表單](how-to-create-mdi-child-forms.md)
- [如何：將資料傳送至作用中的 MDI 子系](how-to-send-data-to-the-active-mdi-child.md)
- [如何：排列 MDI 子表單](how-to-arrange-mdi-child-forms.md)
