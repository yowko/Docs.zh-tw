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
ms.openlocfilehash: 81cb9b55f53c152e755ada1803e4ba5731498627
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229468"
---
# <a name="how-to-determine-the-active-mdi-child"></a>HOW TO：決定作用中的 MDI 子系
在某些情況下，您要在目前作用中的子表單具有焦點的控制項上提供作業的命令。 例如，假設您想要選取的文字複製到剪貼簿的子表單的文字方塊。 您會建立一個程序，將選取的文字複製到剪貼簿使用<xref:System.Windows.Forms.Control.Click>的複製功能表項目，標準的 [編輯] 功能表上的事件。  
  
 由於 MDI 應用程式有許多相同的子表單的執行個體，程序，就必須知道要使用哪個表單。 若要指定正確的格式，請使用<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>屬性，會傳回具有焦點，或所最近使用的子表單。  
  
 當您有數個控制項在表單上的時，您也需要指定哪一個控制項處於現用狀態。 像是<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>屬性，<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A>屬性會傳回具有焦點的控制項作用中的子表單上。 下列程序會說明可以從 子表單功能表、 MDI 表單或工具列按鈕上的功能表中呼叫的複製程序。  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>若要判斷使用中的 MDI 子系 （若要將它的文字複製到剪貼簿）  
  
1.  在方法中，將作用中的子表單的作用中控制項的文字複製到剪貼簿。  
  
    > [!NOTE]
    >  這個範例假設沒有 MDI 父表單 (`Form1`)，其包含的一或多個 MDI 子視窗<xref:System.Windows.Forms.RichTextBox>控制項。 如需詳細資訊，請參閱 <<c0> [ 建立 MDI 父表單](how-to-create-mdi-parent-forms.md)。  
  
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
- [HOW TO：建立 MDI 父表單](how-to-create-mdi-parent-forms.md)
- [HOW TO：建立 MDI 子表單](how-to-create-mdi-child-forms.md)
- [HOW TO：傳送資料至作用中的 MDI 子系](how-to-send-data-to-the-active-mdi-child.md)
- [HOW TO：排列 MDI 子表單](how-to-arrange-mdi-child-forms.md)
