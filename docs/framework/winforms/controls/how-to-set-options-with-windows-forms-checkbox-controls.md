---
title: 使用 CheckBox 控制項設定選項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
ms.openlocfilehash: 84198eab42aa02b1bb37fa16a3c4247a37f58a10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746773"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="48039-102">如何：使用 Windows Form CheckBox 控制項設定選項</span><span class="sxs-lookup"><span data-stu-id="48039-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="48039-103">Windows Forms 的 <xref:System.Windows.Forms.CheckBox> 控制項可用來為使用者提供 True/False 或 [是] 或 [否] 選項。</span><span class="sxs-lookup"><span data-stu-id="48039-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="48039-104">控制項會在選取時顯示核取記號。</span><span class="sxs-lookup"><span data-stu-id="48039-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="48039-105">使用 CheckBox 控制項設定選項</span><span class="sxs-lookup"><span data-stu-id="48039-105">To set options with CheckBox controls</span></span>  
  
1. <span data-ttu-id="48039-106">檢查 <xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性的值以判斷其狀態，並使用該值來設定選項。</span><span class="sxs-lookup"><span data-stu-id="48039-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="48039-107">在下面的程式碼範例中，當 <xref:System.Windows.Forms.CheckBox> 控制項的 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件引發時，如果核取此核取方塊，則表單的 <xref:System.Windows.Forms.Control.AllowDrop%2A> 屬性會設定為 [`false`]。</span><span class="sxs-lookup"><span data-stu-id="48039-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="48039-108">這適用于您想要限制使用者互動的情況。</span><span class="sxs-lookup"><span data-stu-id="48039-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="48039-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="48039-109">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="48039-110">CheckBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="48039-110">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="48039-111">操作說明：回應 Windows Forms CheckBox 按一下動作</span><span class="sxs-lookup"><span data-stu-id="48039-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [<span data-ttu-id="48039-112">CheckBox 控制項</span><span class="sxs-lookup"><span data-stu-id="48039-112">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
