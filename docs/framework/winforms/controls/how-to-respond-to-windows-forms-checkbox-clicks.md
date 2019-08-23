---
title: 作法：回應 Windows Forms 核取方塊的按一下動作
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
ms.openlocfilehash: 7ff6b2aad9ef0775547af57f11af28839e69637c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914986"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>HOW TO：回應 Windows Forms 核取方塊的按一下動作
每當使用者按一下 Windows Forms <xref:System.Windows.Forms.CheckBox>控制項時, 就會發生此<xref:System.Windows.Forms.Control.Click>事件。 您可以根據核取方塊的狀態, 將您的應用程式設計成執行某些動作。  
  
### <a name="to-respond-to-checkbox-clicks"></a>若要回應核取方塊按一下  
  
1. 在事件處理常式中, <xref:System.Windows.Forms.CheckBox.Checked%2A>使用屬性來判斷控制項的狀態, 並執行任何必要的動作。 <xref:System.Windows.Forms.Control.Click>  
  
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
    > 如果使用者嘗試按兩下<xref:System.Windows.Forms.CheckBox>控制項, 則每次按一下都會單獨處理, 也就是說<xref:System.Windows.Forms.CheckBox> , 控制項不支援按兩下事件。  
  
    > [!NOTE]
    > 當屬性為`true` (預設值) 時, <xref:System.Windows.Forms.CheckBox>會在按一下時自動選取或清除。 <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> 否則, <xref:System.Windows.Forms.CheckBox.Checked%2A> <xref:System.Windows.Forms.Control.Click>當事件發生時, 您必須手動設定屬性。  
  
     您也可以使用<xref:System.Windows.Forms.CheckBox>控制項來判斷動作的執行過程。  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>若要判斷按一下核取方塊時的動作課程  
  
1. 使用 case 語句來查詢<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性的值, 以判斷動作的執行過程。 當屬性設定為`true`時, <xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性可能會傳回三個可能的值, 這代表要檢查的方塊、未核取的方塊, 或是以暗灰色顯示方塊的第三個不定狀態<xref:System.Windows.Forms.CheckBox.ThreeState%2A>指出無法使用選項的外觀。  
  
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
    > `true` <xref:System.Windows.Forms.CheckBox.Checked%2A> `true` <xref:System.Windows.Forms.CheckState.Checked>當屬性設定為時, 屬性會傳回和<xref:System.Windows.Forms.CheckState.Indeterminate>的。 <xref:System.Windows.Forms.CheckBox.ThreeState%2A>  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox 控制項概觀](checkbox-control-overview-windows-forms.md)
- [如何：使用 Windows Forms CheckBox 控制項設定選項](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox 控制項](checkbox-control-windows-forms.md)
