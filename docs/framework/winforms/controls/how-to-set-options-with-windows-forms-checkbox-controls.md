---
title: 如何：使用 Windows Form CheckBox 控制項設定選項
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
ms.openlocfilehash: dc9e7b1aea74874c66bf9eb96a5b919ed9b4b73b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534082"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="588e4-102">如何：使用 Windows Form CheckBox 控制項設定選項</span><span class="sxs-lookup"><span data-stu-id="588e4-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="588e4-103">Windows Form<xref:System.Windows.Forms.CheckBox>控制項可用來給予使用者 True/False 或 Yes/No 選項。</span><span class="sxs-lookup"><span data-stu-id="588e4-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="588e4-104">選取時，控制項就會顯示核取記號。</span><span class="sxs-lookup"><span data-stu-id="588e4-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="588e4-105">若要設定選項的核取方塊控制項</span><span class="sxs-lookup"><span data-stu-id="588e4-105">To set options with CheckBox controls</span></span>  
  
1.  <span data-ttu-id="588e4-106">檢查值<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性來判斷其狀態，並使用該值來設定的選項。</span><span class="sxs-lookup"><span data-stu-id="588e4-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="588e4-107">在之下，當程式碼範例<xref:System.Windows.Forms.CheckBox>控制項的<xref:System.Windows.Forms.CheckBox.CheckedChanged>引發事件時，表單的<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性設定為`false`如果勾選此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="588e4-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="588e4-108">這是您要限制使用者互動的情況下很有用。</span><span class="sxs-lookup"><span data-stu-id="588e4-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="588e4-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="588e4-109">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="588e4-110">CheckBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="588e4-110">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="588e4-111">操作說明：回應 Windows Forms CheckBox 按一下動作</span><span class="sxs-lookup"><span data-stu-id="588e4-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [<span data-ttu-id="588e4-112">CheckBox 控制項</span><span class="sxs-lookup"><span data-stu-id="588e4-112">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
