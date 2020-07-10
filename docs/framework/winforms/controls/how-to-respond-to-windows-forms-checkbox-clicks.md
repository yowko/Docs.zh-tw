---
title: 回應 CheckBox 點選
description: 瞭解如何根據核取方塊的狀態，將您的 Windows Forms 應用程式設計成執行某些動作。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
ms.openlocfilehash: 58944bc421f990343b6c58484aaab3d79c8bda5e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174493"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>如何：回應 Windows Form CheckBox 按一下動作
每當使用者按一下 Windows Forms 控制項時 <xref:System.Windows.Forms.CheckBox> ， <xref:System.Windows.Forms.Control.Click> 就會發生此事件。 您可以根據核取方塊的狀態，將您的應用程式設計成執行某些動作。  
  
### <a name="to-respond-to-checkbox-clicks"></a>若要回應核取方塊按一下  
  
1. 在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中，使用 <xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性來判斷控制項的狀態，並執行任何必要的動作。  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    > 如果使用者嘗試按兩下 <xref:System.Windows.Forms.CheckBox> 控制項，則每次按一下都會單獨處理，也就是說， <xref:System.Windows.Forms.CheckBox> 控制項不支援按兩下事件。  
  
    > [!NOTE]
    > 當 <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> 屬性 `true` (預設) 時，會在 <xref:System.Windows.Forms.CheckBox> 按一下時自動選取或清除。 否則， <xref:System.Windows.Forms.CheckBox.Checked%2A> 當事件發生時，您必須手動設定屬性 <xref:System.Windows.Forms.Control.Click> 。  
  
     您也可以使用 <xref:System.Windows.Forms.CheckBox> 控制項來判斷動作的執行過程。  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>若要判斷按一下核取方塊時的動作課程  
  
1. 使用 case 語句來查詢屬性的值 <xref:System.Windows.Forms.CheckBox.CheckState%2A> ，以判斷動作的執行過程。 當 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 屬性設定為時 `true` ， <xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性可能會傳回三個可能的值，分別代表要檢查的方塊、未核取的方塊，或第三個不定狀態，其中方塊會以暗灰色的外觀顯示，表示無法使用此選項。  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    > 當 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 屬性設定為時 `true` ，屬性會傳回 <xref:System.Windows.Forms.CheckBox.Checked%2A> `true` 和的 <xref:System.Windows.Forms.CheckState.Checked> <xref:System.Windows.Forms.CheckState.Indeterminate> 。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox 控制項概觀](checkbox-control-overview-windows-forms.md)
- [如何：使用 Windows Form CheckBox 控制項設定選項](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox 控制項](checkbox-control-windows-forms.md)
