---
title: 判斷在 RichTextBox 控制項中格式化屬性何時變更
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
ms.openlocfilehash: f9b2a1028f79059ec7d4d6bf3683100455bb5dea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746044"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>如何：判斷 Windows Form RichTextBox 控制項中的格式屬性何時變更
Windows Forms <xref:System.Windows.Forms.RichTextBox> 控制項的常見用法是使用字型選項或段落樣式等屬性來格式化文字。 您的應用程式可能需要追蹤文字格式的任何變更，以顯示工具列，如同許多文字處理應用程式一樣。  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>若要回應格式化屬性的變更  
  
1. 在 <xref:System.Windows.Forms.RichTextBox.SelectionChanged> 事件處理常式中撰寫程式碼，以根據屬性的值執行適當的動作。 下列範例會根據 <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> 屬性的值來變更工具列按鈕的外觀。 只有當插入點在控制項中移動時，工具列按鈕才會更新。  
  
     下列範例假設有一個表單具有 <xref:System.Windows.Forms.RichTextBox> 控制項，以及一個包含工具列按鈕的 <xref:System.Windows.Forms.ToolBar> 控制項。 如需工具列和工具列按鈕的詳細資訊，請參閱[如何：將按鈕加入至工具列控制項](how-to-add-buttons-to-a-toolbar-control.md)。  
  
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
