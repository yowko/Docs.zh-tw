---
title: HOW TO：設定使用 Windows Form 核取方塊控制項的選項
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
ms.openlocfilehash: 3eb68d76d936f13e78d13629455c6ac7fb537b40
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714784"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>HOW TO：設定使用 Windows Form 核取方塊控制項的選項
Windows Form<xref:System.Windows.Forms.CheckBox>控制項用來授權使用者 True/False 或 Yes/No 選項。 選取時，控制項就會顯示核取記號。  
  
### <a name="to-set-options-with-checkbox-controls"></a>若要設定與核取方塊控制項的選項  
  
1.  檢查的值<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性來判斷其狀態，並使用該值來設定選項。  
  
     在如下，當程式碼範例<xref:System.Windows.Forms.CheckBox>控制項的<xref:System.Windows.Forms.CheckBox.CheckedChanged>引發事件時，表單的<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性設定為`false`如果勾選此核取方塊。 這是您想要用來限制使用者互動的情況下很有用。  
  
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
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.CheckBox>
- [CheckBox 控制項概觀](checkbox-control-overview-windows-forms.md)
- [如何：回應 Windows Form CheckBox 按一下動作](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox 控制項](checkbox-control-windows-forms.md)
