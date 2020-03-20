---
title: 確定"格式設置屬性在富文本盒"控制項中何時更改
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], determining font changes
- text boxes [Windows Forms], determining font changes
- SelChange event
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
ms.openlocfilehash: a190c3479b58464763e0eefdd32d14e88a1f05e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142260"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>如何：判斷 Windows Form RichTextBox 控制項中的格式屬性何時變更
Windows 表單<xref:System.Windows.Forms.RichTextBox>控制項的常見用途是使用字體選項或段落樣式等屬性設置文本格式。 應用程式可能需要跟蹤文本格式的任何更改，以便顯示工具列，如許多文字處理應用程式中。  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>回應格式屬性的更改  
  
1. 在事件處理常式中<xref:System.Windows.Forms.RichTextBox.SelectionChanged>編寫代碼以執行適當的操作，具體取決於屬性的值。 下面的示例根據屬性的值更改工具列按鈕的外觀<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>。 僅當插入點在控制項中移動時，才會更新工具列按鈕。  
  
     下面的示例假定表單具有<xref:System.Windows.Forms.RichTextBox>控制項和包含工具列按鈕的<xref:System.Windows.Forms.ToolBar>控制項。 有關工具列和工具列按鈕的詳細資訊，請參閱[如何：將按鈕添加到工具列控制項](how-to-add-buttons-to-a-toolbar-control.md)。  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](richtextbox-control-windows-forms.md)
- [在 Windows Form 上使用的控制項](controls-to-use-on-windows-forms.md)
