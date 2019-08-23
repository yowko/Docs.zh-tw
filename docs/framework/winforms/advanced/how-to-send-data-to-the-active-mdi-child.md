---
title: 作法：傳送資料至作用中的 MDI 子系
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
ms.openlocfilehash: 0a7a2475891488d1fdd60f0db4a483c144a73f0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947849"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="b24ac-102">HOW TO：傳送資料至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="b24ac-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="b24ac-103">通常, 在[多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)的內容中, 您必須將資料傳送至使用中的子視窗, 例如當使用者將資料從剪貼簿貼入 MDI 應用程式時。</span><span class="sxs-lookup"><span data-stu-id="b24ac-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b24ac-104">如需驗證哪個子視窗具有焦點並將其內容傳送至剪貼簿的詳細資訊, 請參閱判斷作用中[的 MDI 子](how-to-determine-the-active-mdi-child.md)系。</span><span class="sxs-lookup"><span data-stu-id="b24ac-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="b24ac-105">若要從剪貼簿將資料傳送至作用中的 MDI 子視窗</span><span class="sxs-lookup"><span data-stu-id="b24ac-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1. <span data-ttu-id="b24ac-106">在方法內, 將剪貼簿上的文字複製到現用子表單的作用中控制項。</span><span class="sxs-lookup"><span data-stu-id="b24ac-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b24ac-107">這個範例假設有一個 mdi 父表單 (`Form1`), 其中有一個或多個<xref:System.Windows.Forms.RichTextBox>包含控制項的 mdi 子視窗。</span><span class="sxs-lookup"><span data-stu-id="b24ac-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="b24ac-108">如需詳細資訊, 請參閱[建立 MDI 父表單](how-to-create-mdi-parent-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="b24ac-108">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b24ac-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b24ac-109">See also</span></span>

- [<span data-ttu-id="b24ac-110">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="b24ac-110">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="b24ac-111">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="b24ac-111">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="b24ac-112">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="b24ac-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="b24ac-113">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="b24ac-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="b24ac-114">如何：排列 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="b24ac-114">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
