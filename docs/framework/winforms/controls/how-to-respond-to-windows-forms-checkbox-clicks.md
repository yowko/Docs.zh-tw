---
title: 回應 CheckBox 點選
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
ms.openlocfilehash: 6ff20c443519446d3804b325924cb3c5cbedea97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141922"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>如何：回應 Windows Form CheckBox 按一下動作
每當使用者按一下 Windows 表單<xref:System.Windows.Forms.CheckBox>控制項時，都會<xref:System.Windows.Forms.Control.Click>發生該事件。 您可以根據核取方塊的狀態對應用程式進行程式設計以執行某些操作。  
  
### <a name="to-respond-to-checkbox-clicks"></a>回應核取方塊點擊  
  
1. 在事件<xref:System.Windows.Forms.Control.Click>處理常式中，使用<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性確定控制項的狀態，並執行任何必要的操作。  
  
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
    > 如果使用者嘗試按兩下<xref:System.Windows.Forms.CheckBox>控制項，則每次按一下將單獨處理;如果使用者嘗試按兩下控制項，則每次按一下都將單獨處理。也就是說，<xref:System.Windows.Forms.CheckBox>控制項不支援按兩下事件。  
  
    > [!NOTE]
    > 當<xref:System.Windows.Forms.CheckBox.AutoCheck%2A>屬性為`true`（預設值）時，<xref:System.Windows.Forms.CheckBox>按一下時會自動選擇或清除 該屬性。 否則，在<xref:System.Windows.Forms.Control.Click>事件發生時必須手動設置<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性。  
  
     您還可以使用控制項<xref:System.Windows.Forms.CheckBox>來確定操作過程。  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>在按一下核取方塊時確定操作過程  
  
1. 使用 case 語句查詢<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性的值以確定操作過程。 當<xref:System.Windows.Forms.CheckBox.ThreeState%2A>屬性設置為`true`時，<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性可能會返回三個可能的值，表示要選中的框、未選中的框或顯示具有灰色外觀的框以指示該選項不可用的第三個不確定狀態。  
  
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
    > 當屬性<xref:System.Windows.Forms.CheckBox.ThreeState%2A>`true`設置為<xref:System.Windows.Forms.CheckBox.Checked%2A>時，屬性將返回`true`和<xref:System.Windows.Forms.CheckState.Checked><xref:System.Windows.Forms.CheckState.Indeterminate>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox 控制項概觀](checkbox-control-overview-windows-forms.md)
- [如何：使用 Windows Form CheckBox 控制項設定選項](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [核取方塊控制](checkbox-control-windows-forms.md)
