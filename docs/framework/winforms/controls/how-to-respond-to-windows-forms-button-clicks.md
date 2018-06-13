---
title: 如何：回應 Windows Form Button 按一下動作
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
ms.openlocfilehash: 14a880c34f163dc6fece44c24d377822a741b0f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534247"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="c2874-102">如何：回應 Windows Form Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="c2874-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="c2874-103">Windows Form 的最基本用法<xref:System.Windows.Forms.Button>控制項是在按下按鈕時執行某些程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2874-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="c2874-104">按一下<xref:System.Windows.Forms.Button>控制項也會產生一些其他事件，例如<xref:System.Windows.Forms.Control.MouseEnter>， <xref:System.Windows.Forms.Control.MouseDown>，和<xref:System.Windows.Forms.Control.MouseUp>事件。</span><span class="sxs-lookup"><span data-stu-id="c2874-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="c2874-105">如果您想要附加這些相關事件的事件處理常式，請確定其動作不會產生衝突。</span><span class="sxs-lookup"><span data-stu-id="c2874-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="c2874-106">例如，如果按一下按鈕可清除使用者在文字方塊中輸入的資訊，暫停滑鼠指標停留在按鈕不應該顯示工具提示，其中目前不存在的資訊。</span><span class="sxs-lookup"><span data-stu-id="c2874-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="c2874-107">如果使用者嘗試按兩下<xref:System.Windows.Forms.Button>控制項，將會個別處理每按一下; 也就是控制項不支援按兩下事件。</span><span class="sxs-lookup"><span data-stu-id="c2874-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="c2874-108">若要回應按下按鈕</span><span class="sxs-lookup"><span data-stu-id="c2874-108">To respond to a button click</span></span>  
  
-   <span data-ttu-id="c2874-109">在按鈕的`Click`<xref:System.EventHandler>撰寫程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="c2874-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="c2874-110">`Button1_Click` 必須繫結至控制項。</span><span class="sxs-lookup"><span data-stu-id="c2874-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="c2874-111">如需詳細資訊，請參閱[How to： 建立事件處理常式在執行時間適用於 Windows Form](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="c2874-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2874-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2874-112">See Also</span></span>  
 [<span data-ttu-id="c2874-113">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="c2874-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="c2874-114">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="c2874-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="c2874-115">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="c2874-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
