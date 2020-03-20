---
title: 如何：決定作用中的 MDI 子系
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
ms.openlocfilehash: 57491faa10c182630d41565ba236d65e393929b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182551"
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="9cbb2-102">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="9cbb2-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="9cbb2-103">有時，您需要提供一個命令，該命令對側重于當前活動子表單的控制項進行操作。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="9cbb2-104">例如，假設您要將所選文本從子表單的文字方塊複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="9cbb2-105">您將創建一個過程，使用標準"編輯"功能表上的"複製<xref:System.Windows.Forms.Control.Click>"功能表項目事件將所選文本複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="9cbb2-106">由於 MDI 應用程式可以具有同一子表單的許多實例，因此該過程需要知道要使用的表單。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="9cbb2-107">要指定正確的表單，請使用 屬性<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>，該屬性返回具有焦點或最近處于活動狀態的子表單。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="9cbb2-108">當表單上有多個控制項時，還需要指定哪個控制項處於活動狀態。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="9cbb2-109">與<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>屬性一樣<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A>，屬性返回控制項，重點放在活動子表單上。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="9cbb2-110">下面的過程演示了可以從子表單功能表、MDI 表單上的功能表或工具列按鈕調用的複製過程。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="9cbb2-111">確定活動 MDI 子級（將其文本複製到剪貼簿）</span><span class="sxs-lookup"><span data-stu-id="9cbb2-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="9cbb2-112">在方法中，將活動子表單的活動控制項的文本複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9cbb2-113">此示例假定有一個 MDI 父表單`Form1`（ ） 具有一個或多個包含控制項的<xref:System.Windows.Forms.RichTextBox>MDI 子視窗。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="9cbb2-114">有關詳細資訊，請參閱創建[MDI 父表單](how-to-create-mdi-parent-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="9cbb2-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9cbb2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cbb2-115">See also</span></span>

- [<span data-ttu-id="9cbb2-116">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="9cbb2-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="9cbb2-117">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="9cbb2-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="9cbb2-118">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="9cbb2-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="9cbb2-119">如何：傳送資料至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="9cbb2-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="9cbb2-120">如何：安排 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="9cbb2-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
