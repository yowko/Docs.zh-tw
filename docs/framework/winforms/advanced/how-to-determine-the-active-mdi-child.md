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
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="9ac3a-102">作法：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="9ac3a-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="9ac3a-103">在某些情況下, 您會想要提供一個命令, 以在焦點放在目前使用中子表單的控制項上操作。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="9ac3a-104">例如, 假設您想要從子表單的文字方塊中, 將選取的文字複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="9ac3a-105">您會建立一個程式, 使用<xref:System.Windows.Forms.Control.Click>標準 [編輯] 功能表上 [複製] 功能表項目的事件, 將選取的文字複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="9ac3a-106">由於 MDI 應用程式可以有多個相同子表單的實例, 因此程式需要知道要使用哪一個表單。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="9ac3a-107">若要指定正確的格式, 請<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>使用屬性, 它會傳回具有焦點或最近使用中的子表單。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="9ac3a-108">當您在表單上有數個控制項時, 您也必須指定要使用哪一個控制項。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="9ac3a-109"><xref:System.Windows.Forms.Form.ActiveMdiChild%2A>如同屬性<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> , 屬性會將焦點放在使用中子表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="9ac3a-110">下列程式說明可從子表單功能表、MDI 表單上的功能表或工具列按鈕呼叫的複製程式。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="9ac3a-111">判斷現用 MDI 子系 (將其文字複製到剪貼簿)</span><span class="sxs-lookup"><span data-stu-id="9ac3a-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="9ac3a-112">在方法內, 將現用子表單的作用中控制項文字複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9ac3a-113">這個範例假設有一個 mdi 父表單 (`Form1`), 其中有一個或多個<xref:System.Windows.Forms.RichTextBox>包含控制項的 mdi 子視窗。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="9ac3a-114">如需詳細資訊, 請參閱[建立 MDI 父表單](how-to-create-mdi-parent-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="9ac3a-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ac3a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ac3a-115">See also</span></span>

- [<span data-ttu-id="9ac3a-116">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="9ac3a-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="9ac3a-117">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="9ac3a-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="9ac3a-118">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="9ac3a-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="9ac3a-119">如何：將資料傳送至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="9ac3a-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="9ac3a-120">如何：排列 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="9ac3a-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
