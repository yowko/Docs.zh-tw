---
title: "如何：決定作用中的 MDI 子系"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c026df631c2ac033594ea86887bb8440a6aa240a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="a8b10-102">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="a8b10-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="a8b10-103">在某些情況下，您會想要提供目前使用中的子表單具有焦點在控制項上作業的命令。</span><span class="sxs-lookup"><span data-stu-id="a8b10-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="a8b10-104">例如，假設您想要選取的文字複製到剪貼簿的子表單的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a8b10-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="a8b10-105">您將建立的程序，將選取的文字複製到剪貼簿使用<xref:System.Windows.Forms.Control.Click>複製功能表項目，標準的 [編輯] 功能表上的事件。</span><span class="sxs-lookup"><span data-stu-id="a8b10-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="a8b10-106">由於 MDI 應用程式可以有相同的子表單的許多執行個體，則需要知道要使用哪個表單程序。</span><span class="sxs-lookup"><span data-stu-id="a8b10-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="a8b10-107">若要指定正確的格式，請使用<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>屬性，它會傳回具有焦點，或所最近使用的子表單。</span><span class="sxs-lookup"><span data-stu-id="a8b10-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="a8b10-108">當您有數個控制項在表單上時，您也需要指定哪一個控制項是使用中。</span><span class="sxs-lookup"><span data-stu-id="a8b10-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="a8b10-109">像<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>屬性，<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A>屬性會傳回具有焦點的控制項作用中的子表單上。</span><span class="sxs-lookup"><span data-stu-id="a8b10-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="a8b10-110">下列程序將說明可從子表單功能表、 功能表 MDI 表單或工具列按鈕呼叫的複製程序。</span><span class="sxs-lookup"><span data-stu-id="a8b10-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="a8b10-111">若要判斷使用中的 MDI 子系 （若要將它的文字複製到剪貼簿）</span><span class="sxs-lookup"><span data-stu-id="a8b10-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1.  <span data-ttu-id="a8b10-112">在方法中，將作用中子表單的作用中控制項的文字複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="a8b10-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8b10-113">這個範例假設有 MDI 父表單 (`Form1`) 具有一個或多個 MDI 子視窗包含<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a8b10-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="a8b10-114">如需詳細資訊，請參閱[建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="a8b10-114">For more information, see [Creating MDI Parent Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8b10-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="a8b10-115">See Also</span></span>  
 [<span data-ttu-id="a8b10-116">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="a8b10-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="a8b10-117">操作說明：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="a8b10-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="a8b10-118">操作說明：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="a8b10-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="a8b10-119">操作說明：傳送資料至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="a8b10-119">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="a8b10-120">操作說明：安排 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="a8b10-120">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
