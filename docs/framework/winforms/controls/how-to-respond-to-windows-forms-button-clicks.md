---
title: HOW TO：回應 Windows Forms 按鈕的按一下動作
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
ms.openlocfilehash: ebcde2b5e749c5a3621c623a864578b2a654ce63
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638362"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>HOW TO：回應 Windows Forms 按鈕的按一下動作
Windows Form 的最基本用法<xref:System.Windows.Forms.Button>控制項是在按下按鈕時執行某些程式碼。  
  
 按一下 <xref:System.Windows.Forms.Button>控制項也會產生有多個其他事件，例如<xref:System.Windows.Forms.Control.MouseEnter>， <xref:System.Windows.Forms.Control.MouseDown>，和<xref:System.Windows.Forms.Control.MouseUp>事件。 如果您想要將這些相關事件的事件處理常式的連接，請確定其動作不會發生衝突。 比方說，如果按一下按鈕來清除文字方塊中輸入使用者的資訊，將滑鼠指標暫停按鈕應該不顯示工具提示，其中目前不存在的資訊。  
  
 如果使用者試著按兩下<xref:System.Windows.Forms.Button>控制項，將會個別處理每按一下; 也就是說，控制項不支援按兩下事件。  
  
### <a name="to-respond-to-a-button-click"></a>若要回應按下按鈕  
  
- 在按鈕的`Click`<xref:System.EventHandler>撰寫程式碼來執行。 `Button1_Click` 必須繫結至控制項。 如需詳細資訊，請參閱[如何：在執行階段建立 Windows Forms 事件處理常式](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
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
