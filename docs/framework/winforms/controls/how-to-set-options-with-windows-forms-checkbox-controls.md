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
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>如何：使用 Windows Form CheckBox 控制項設定選項
Windows Forms 的 <xref:System.Windows.Forms.CheckBox> 控制項可用來為使用者提供 True/False 或 [是] 或 [否] 選項。 控制項會在選取時顯示核取記號。  
  
### <a name="to-set-options-with-checkbox-controls"></a>使用 CheckBox 控制項設定選項  
  
1. 檢查 <xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性的值以判斷其狀態，並使用該值來設定選項。  
  
     在下面的程式碼範例中，當 <xref:System.Windows.Forms.CheckBox> 控制項的 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件引發時，如果核取此核取方塊，則表單的 <xref:System.Windows.Forms.Control.AllowDrop%2A> 屬性會設定為 [`false`]。 這適用于您想要限制使用者互動的情況。  
  
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
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox 控制項概觀](checkbox-control-overview-windows-forms.md)
- [操作說明：回應 Windows Forms CheckBox 按一下動作](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox 控制項](checkbox-control-windows-forms.md)
