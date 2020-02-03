---
title: 回應按鈕點選
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: dd6cf75a316257c86a23b44a818422336c12aa67
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735724"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>如何：回應 Windows Form Button 按一下動作
Windows Forms <xref:System.Windows.Forms.Button> 控制項的最基本用法，就是在按一下按鈕時執行一些程式碼。  
  
 按一下 <xref:System.Windows.Forms.Button> 控制項也會產生一些其他事件，例如 <xref:System.Windows.Forms.Control.MouseEnter>、<xref:System.Windows.Forms.Control.MouseDown>和 <xref:System.Windows.Forms.Control.MouseUp> 事件。 如果您想要附加這些相關事件的事件處理常式，請確定其動作不會衝突。 例如，如果按一下按鈕會清除使用者在文字方塊中輸入的資訊，則將滑鼠指標暫停在按鈕上時，不應該顯示工具提示，而且現在不存在資訊。  
  
 如果使用者嘗試按兩下 <xref:System.Windows.Forms.Button> 控制項，則每次按一下都會單獨處理;也就是，控制項不支援按兩下事件。  
  
### <a name="to-respond-to-a-button-click"></a>若要回應按鈕按一下  
  
- 在按鈕的 `Click` 中 <xref:System.EventHandler> 撰寫要執行的程式碼。 `Button1_Click` 必須系結至控制項。 如需詳細資訊，請參閱[如何：在執行時間建立事件處理常式以進行 Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a>另請參閱

- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [Button 控制項](button-control-windows-forms.md)
