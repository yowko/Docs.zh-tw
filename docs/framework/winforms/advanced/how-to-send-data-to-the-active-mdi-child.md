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
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="11162-102">如何：傳送資料至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="11162-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="11162-103">通常，在[多文檔介面 （MDI） 應用程式的](multiple-document-interface-mdi-applications.md)上下文中，您需要將資料發送到活動子視窗，例如當使用者將剪貼簿的資料粘貼到 MDI 應用程式中時。</span><span class="sxs-lookup"><span data-stu-id="11162-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11162-104">有關驗證哪個子視窗具有焦點並將其內容發送到剪貼簿的資訊，請參閱[確定活動 MDI 子視窗](how-to-determine-the-active-mdi-child.md)。</span><span class="sxs-lookup"><span data-stu-id="11162-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="11162-105">從剪貼簿將資料發送到活動 MDI 子視窗</span><span class="sxs-lookup"><span data-stu-id="11162-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1. <span data-ttu-id="11162-106">在方法中，將剪貼簿上的文本複製到活動子表單的活動控制項。</span><span class="sxs-lookup"><span data-stu-id="11162-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="11162-107">此示例假定有一個 MDI 父表單`Form1`（ ） 具有一個或多個包含控制項的<xref:System.Windows.Forms.RichTextBox>MDI 子視窗。</span><span class="sxs-lookup"><span data-stu-id="11162-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="11162-108">有關詳細資訊，請參閱創建[MDI 父表單](how-to-create-mdi-parent-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="11162-108">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11162-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11162-109">See also</span></span>

- [<span data-ttu-id="11162-110">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="11162-110">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="11162-111">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="11162-111">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="11162-112">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="11162-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="11162-113">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="11162-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="11162-114">如何：安排 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="11162-114">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
