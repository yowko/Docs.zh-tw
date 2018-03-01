---
title: "如何：使用 Windows Form CheckBox 控制項設定選項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4059e3b4ad4c687234f2bc0c66c680b2c857cfe7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>如何：使用 Windows Form CheckBox 控制項設定選項
Windows Form<xref:System.Windows.Forms.CheckBox>控制項可用來給予使用者 True/False 或 Yes/No 選項。 選取時，控制項就會顯示核取記號。  
  
### <a name="to-set-options-with-checkbox-controls"></a>若要設定選項的核取方塊控制項  
  
1.  檢查值<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性來判斷其狀態，並使用該值來設定的選項。  
  
     在之下，當程式碼範例<xref:System.Windows.Forms.CheckBox>控制項的<xref:System.Windows.Forms.CheckBox.CheckedChanged>引發事件時，表單的<xref:System.Windows.Forms.Control.AllowDrop%2A>屬性設定為`false`如果勾選此核取方塊。 這是您要限制使用者互動的情況下很有用。  
  
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
 <xref:System.Windows.Forms.CheckBox>  
 [CheckBox 控制項概觀](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [操作說明：回應 Windows Forms CheckBox 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [CheckBox 控制項](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
