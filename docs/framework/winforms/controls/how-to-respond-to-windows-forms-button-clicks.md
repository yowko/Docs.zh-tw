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
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="53e7a-102">如何：回應 Windows Form Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="53e7a-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="53e7a-103">Windows Forms <xref:System.Windows.Forms.Button> 控制項的最基本用法，就是在按一下按鈕時執行一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="53e7a-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="53e7a-104">按一下 <xref:System.Windows.Forms.Button> 控制項也會產生一些其他事件，例如 <xref:System.Windows.Forms.Control.MouseEnter>、<xref:System.Windows.Forms.Control.MouseDown>和 <xref:System.Windows.Forms.Control.MouseUp> 事件。</span><span class="sxs-lookup"><span data-stu-id="53e7a-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="53e7a-105">如果您想要附加這些相關事件的事件處理常式，請確定其動作不會衝突。</span><span class="sxs-lookup"><span data-stu-id="53e7a-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="53e7a-106">例如，如果按一下按鈕會清除使用者在文字方塊中輸入的資訊，則將滑鼠指標暫停在按鈕上時，不應該顯示工具提示，而且現在不存在資訊。</span><span class="sxs-lookup"><span data-stu-id="53e7a-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="53e7a-107">如果使用者嘗試按兩下 <xref:System.Windows.Forms.Button> 控制項，則每次按一下都會單獨處理;也就是，控制項不支援按兩下事件。</span><span class="sxs-lookup"><span data-stu-id="53e7a-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="53e7a-108">若要回應按鈕按一下</span><span class="sxs-lookup"><span data-stu-id="53e7a-108">To respond to a button click</span></span>  
  
- <span data-ttu-id="53e7a-109">在按鈕的 `Click` 中 <xref:System.EventHandler> 撰寫要執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="53e7a-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="53e7a-110">`Button1_Click` 必須系結至控制項。</span><span class="sxs-lookup"><span data-stu-id="53e7a-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="53e7a-111">如需詳細資訊，請參閱[如何：在執行時間建立事件處理常式以進行 Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="53e7a-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53e7a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53e7a-112">See also</span></span>

- [<span data-ttu-id="53e7a-113">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="53e7a-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="53e7a-114">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="53e7a-114">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="53e7a-115">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="53e7a-115">Button Control</span></span>](button-control-windows-forms.md)
