---
title: HOW TO：決定何時變更 Windows Forms RichTextBox 控制項的格式屬性
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
ms.openlocfilehash: a90affde9de36f1c83d5b7c21b40580cdf53402e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972285"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>HOW TO：決定何時變更 Windows Forms RichTextBox 控制項的格式屬性
Windows Form 的常見用法<xref:System.Windows.Forms.RichTextBox>控制項正在格式化文字的字型選項或段落樣式等屬性。 您的應用程式可能需要追蹤的文字格式設定用來顯示工具列，就像許多文書處理應用程式中的任何變更。  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>若要回應的格式屬性變更  
  
1. 在撰寫程式碼<xref:System.Windows.Forms.RichTextBox.SelectionChanged>事件處理常式來執行屬性的值而定的適當動作。 下列範例會變更的值而定的工具列按鈕的外觀<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>屬性。 當插入點移入控制項時，才會更新工具列按鈕。  
  
     下列範例假設使用的表單<xref:System.Windows.Forms.RichTextBox>控制項和<xref:System.Windows.Forms.ToolBar>控制項，其中包含工具列按鈕。 如需有關工具列和工具列按鈕的詳細資訊，請參閱[How to:將按鈕加入至 ToolBar 控制項](how-to-add-buttons-to-a-toolbar-control.md)。  
  
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
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
