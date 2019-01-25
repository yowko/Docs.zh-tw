---
title: HOW TO：將 Windows Form 按鈕指定為取消按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 74d025677682735fc7f1c68116b2364887f0519c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701465"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="1862c-102">HOW TO：將 Windows Form 按鈕指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="1862c-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="1862c-103">在任何 Windows 表單上，您可以指定<xref:System.Windows.Forms.Button>設為 [取消] 按鈕的控制項。</span><span class="sxs-lookup"><span data-stu-id="1862c-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="1862c-104">每當使用者按下 ESC 鍵，不論哪一個表單上的其他控制項具有焦點時，按一下 [取消] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1862c-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="1862c-105">這類按鈕通常被設計成讓使用者快速結束作業，而不需要認可至任何動作。</span><span class="sxs-lookup"><span data-stu-id="1862c-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="1862c-106">若要指定 [取消] 按鈕</span><span class="sxs-lookup"><span data-stu-id="1862c-106">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="1862c-107">將表單的<xref:System.Windows.Forms.Form.CancelButton%2A>屬性為適當<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="1862c-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1862c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1862c-108">See also</span></span>
- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="1862c-109">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="1862c-109">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)
- [<span data-ttu-id="1862c-110">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="1862c-110">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="1862c-111">如何：回應 Windows Form Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="1862c-111">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="1862c-112">如何：將 Windows Form 按鈕指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="1862c-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="1862c-113">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="1862c-113">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
