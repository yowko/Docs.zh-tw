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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966899"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="c134e-102">HOW TO：傳送資料至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="c134e-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="c134e-103">內容中，通常[多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)，您必須將資料傳送至作用中的子視窗，例如當使用者將資料從剪貼簿貼到 MDI 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c134e-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c134e-104">正在驗證哪一個子視窗有焦點，並將其內容傳送到剪貼簿的相關資訊，請參閱[判斷使用中的 MDI 子系](how-to-determine-the-active-mdi-child.md)。</span><span class="sxs-lookup"><span data-stu-id="c134e-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="c134e-105">若要將資料傳送至作用中的 MDI 子視窗中，從剪貼簿</span><span class="sxs-lookup"><span data-stu-id="c134e-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1. <span data-ttu-id="c134e-106">在方法中，將文字複製到剪貼簿上到作用中的子表單的作用中的控制項。</span><span class="sxs-lookup"><span data-stu-id="c134e-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c134e-107">這個範例假設沒有 MDI 父表單 (`Form1`)，其包含的一或多個 MDI 子視窗<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="c134e-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="c134e-108">如需詳細資訊，請參閱 <<c0> [ 建立 MDI 父表單](how-to-create-mdi-parent-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="c134e-108">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c134e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c134e-109">See also</span></span>

- [<span data-ttu-id="c134e-110">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="c134e-110">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="c134e-111">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="c134e-111">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="c134e-112">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="c134e-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="c134e-113">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="c134e-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="c134e-114">如何：排列 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="c134e-114">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
