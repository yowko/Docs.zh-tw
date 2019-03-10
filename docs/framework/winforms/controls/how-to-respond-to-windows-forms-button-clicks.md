---
title: HOW TO：回應 Windows Form Button 按一下動作
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
ms.openlocfilehash: e6e6d041422a79171ec4b6159f0789b8aa6a50d5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724982"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="89430-102">HOW TO：回應 Windows Form Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="89430-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="89430-103">Windows Form 的最基本用法<xref:System.Windows.Forms.Button>控制項是在按下按鈕時執行某些程式碼。</span><span class="sxs-lookup"><span data-stu-id="89430-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="89430-104">按一下 <xref:System.Windows.Forms.Button>控制項也會產生有多個其他事件，例如<xref:System.Windows.Forms.Control.MouseEnter>， <xref:System.Windows.Forms.Control.MouseDown>，和<xref:System.Windows.Forms.Control.MouseUp>事件。</span><span class="sxs-lookup"><span data-stu-id="89430-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="89430-105">如果您想要將這些相關事件的事件處理常式的連接，請確定其動作不會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="89430-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="89430-106">比方說，如果按一下按鈕來清除文字方塊中輸入使用者的資訊，將滑鼠指標暫停按鈕應該不顯示工具提示，其中目前不存在的資訊。</span><span class="sxs-lookup"><span data-stu-id="89430-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="89430-107">如果使用者試著按兩下<xref:System.Windows.Forms.Button>控制項，將會個別處理每按一下; 也就是說，控制項不支援按兩下事件。</span><span class="sxs-lookup"><span data-stu-id="89430-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="89430-108">若要回應按下按鈕</span><span class="sxs-lookup"><span data-stu-id="89430-108">To respond to a button click</span></span>  
  
-   <span data-ttu-id="89430-109">在按鈕的`Click`<xref:System.EventHandler>撰寫程式碼來執行。</span><span class="sxs-lookup"><span data-stu-id="89430-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="89430-110">`Button1_Click` 必須繫結至控制項。</span><span class="sxs-lookup"><span data-stu-id="89430-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="89430-111">如需詳細資訊，請參閱[如何：在執行階段建立 Windows Forms 事件處理常式](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="89430-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89430-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89430-112">See also</span></span>
- [<span data-ttu-id="89430-113">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="89430-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="89430-114">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="89430-114">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="89430-115">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="89430-115">Button Control</span></span>](button-control-windows-forms.md)
