---
title: HOW TO：將 Windows Forms 的按鈕指定為接受按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: 8e608bb2cb4635ef1d29fd7a0aff3ac95fcd9af5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309819"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="17590-102">HOW TO：將 Windows Forms 的按鈕指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="17590-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="17590-103">在任何 Windows 表單上，您可以指定<xref:System.Windows.Forms.Button>設為接受按鈕，也就是預設按鈕的控制項。</span><span class="sxs-lookup"><span data-stu-id="17590-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="17590-104">每當使用者按下 ENTER 鍵，不論哪一個表單上的其他控制項具有焦點按一下預設按鈕。</span><span class="sxs-lookup"><span data-stu-id="17590-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17590-105">例外狀況是另一個按鈕具有焦點的控制項時，會被按一下的按鈕，並將焦點放在此情況下，-多行文字方塊中或自訂控制項的設陷 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="17590-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="17590-106">若要指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="17590-106">To designate the accept button</span></span>  
  
1. <span data-ttu-id="17590-107">將表單的<xref:System.Windows.Forms.Form.AcceptButton%2A>屬性為適當<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="17590-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn   
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="17590-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17590-108">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="17590-109">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="17590-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="17590-110">選取 Windows Form Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="17590-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="17590-111">HOW TO：回應 Windows Forms 按鈕的按一下動作</span><span class="sxs-lookup"><span data-stu-id="17590-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="17590-112">HOW TO：將 Windows Forms 的按鈕指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="17590-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="17590-113">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="17590-113">Button Control</span></span>](button-control-windows-forms.md)
