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
ms.openlocfilehash: 00b467836d8e60aeee51a010a6384abf7dd73c56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141844"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="3be34-102">如何：使用 Windows Form CheckBox 控制項設定選項</span><span class="sxs-lookup"><span data-stu-id="3be34-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="3be34-103">Windows 表單<xref:System.Windows.Forms.CheckBox>控制項用於為使用者提供 True/False 或"是"/否選項。</span><span class="sxs-lookup"><span data-stu-id="3be34-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="3be34-104">選中控制項時，將顯示一個核取記號。</span><span class="sxs-lookup"><span data-stu-id="3be34-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="3be34-105">使用核取方塊控制項設置選項</span><span class="sxs-lookup"><span data-stu-id="3be34-105">To set options with CheckBox controls</span></span>  
  
1. <span data-ttu-id="3be34-106">檢查<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性的值以確定其狀態，並使用該值設置選項。</span><span class="sxs-lookup"><span data-stu-id="3be34-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="3be34-107">在下面的<xref:System.Windows.Forms.CheckBox>代碼示例中，當引發控制項的事件<xref:System.Windows.Forms.CheckBox.CheckedChanged>時，如果選中核取方塊，表單的屬性<xref:System.Windows.Forms.Control.AllowDrop%2A>將設置為。 `false`</span><span class="sxs-lookup"><span data-stu-id="3be34-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="3be34-108">這對於要限制使用者交互的情況很有用。</span><span class="sxs-lookup"><span data-stu-id="3be34-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3be34-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3be34-109">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="3be34-110">CheckBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="3be34-110">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="3be34-111">操作說明：回應 Windows Forms CheckBox 按一下動作</span><span class="sxs-lookup"><span data-stu-id="3be34-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [<span data-ttu-id="3be34-112">核取方塊控制</span><span class="sxs-lookup"><span data-stu-id="3be34-112">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
