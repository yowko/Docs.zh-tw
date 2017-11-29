---
title: "如何：回應 Windows Form Button 按一下動作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 923eb7d1b1b5b442ce897619253a958019b239a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>如何：回應 Windows Form Button 按一下動作
Windows Form 的最基本用法<xref:System.Windows.Forms.Button>控制項是在按下按鈕時執行某些程式碼。  
  
 按一下<xref:System.Windows.Forms.Button>控制項也會產生一些其他事件，例如<xref:System.Windows.Forms.Control.MouseEnter>， <xref:System.Windows.Forms.Control.MouseDown>，和<xref:System.Windows.Forms.Control.MouseUp>事件。 如果您想要附加這些相關事件的事件處理常式，請確定其動作不會產生衝突。 例如，如果按一下按鈕可清除使用者在文字方塊中輸入的資訊，暫停滑鼠指標停留在按鈕不應該顯示工具提示，其中目前不存在的資訊。  
  
 如果使用者嘗試按兩下<xref:System.Windows.Forms.Button>控制項，將會個別處理每按一下; 也就是控制項不支援按兩下事件。  
  
### <a name="to-respond-to-a-button-click"></a>若要回應按下按鈕  
  
-   在按鈕的`Click`<xref:System.EventHandler>撰寫程式碼執行。 `Button1_Click`必須繫結至控制項。 如需詳細資訊，請參閱[How to： 建立事件處理常式在執行時間適用於 Windows Form](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
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
 [Button 控制項概觀](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [選取 Windows Forms Button 控制項的方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
