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
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>如何：使用 Windows Form CheckBox 控制項設定選項
Windows 表單<xref:System.Windows.Forms.CheckBox>控制項用於為使用者提供 True/False 或"是"/否選項。 選中控制項時，將顯示一個核取記號。  
  
### <a name="to-set-options-with-checkbox-controls"></a>使用核取方塊控制項設置選項  
  
1. 檢查<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性的值以確定其狀態，並使用該值設置選項。  
  
     在下面的<xref:System.Windows.Forms.CheckBox>代碼示例中，當引發控制項的事件<xref:System.Windows.Forms.CheckBox.CheckedChanged>時，如果選中核取方塊，表單的屬性<xref:System.Windows.Forms.Control.AllowDrop%2A>將設置為。 `false` 這對於要限制使用者交互的情況很有用。  
  
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
- [操作說明：回應 Windows Forms CheckBox 按一下動作](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [核取方塊控制](checkbox-control-windows-forms.md)
