---
title: 選取按鈕控制項的方式
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740012"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="3b801-102">選取 Windows Form Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="3b801-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="3b801-103">您可以透過下列方式選取 [Windows Forms] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="3b801-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
- <span data-ttu-id="3b801-104">使用滑鼠按一下按鈕。</span><span class="sxs-lookup"><span data-stu-id="3b801-104">Use a mouse to click the button.</span></span>  
  
- <span data-ttu-id="3b801-105">在程式碼中叫用按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="3b801-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
- <span data-ttu-id="3b801-106">按下 TAB 鍵將焦點移至按鈕，然後按空格鍵或 ENTER 以選擇按鈕。</span><span class="sxs-lookup"><span data-stu-id="3b801-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
- <span data-ttu-id="3b801-107">按下按鈕的存取金鑰（ALT + 加底線的字母）。</span><span class="sxs-lookup"><span data-stu-id="3b801-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="3b801-108">如需存取金鑰的詳細資訊，請參閱[如何：建立 Windows Forms 控制項的存取金鑰](how-to-create-access-keys-for-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="3b801-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
- <span data-ttu-id="3b801-109">如果按鈕是表單的 [接受] 按鈕，按 ENTER 鍵會選擇按鈕，即使另一個控制項有焦點也一樣，除非該其他控制項是另一個按鈕、多行文字方塊或自訂控制項，它會陷印 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="3b801-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
- <span data-ttu-id="3b801-110">如果按鈕是表單的 [取消] 按鈕，按 ESC 鍵會選擇按鈕，即使另一個控制項有焦點也一樣。</span><span class="sxs-lookup"><span data-stu-id="3b801-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
- <span data-ttu-id="3b801-111">呼叫 <xref:System.Windows.Forms.Button.PerformClick%2A> 方法，以程式設計方式選取按鈕。</span><span class="sxs-lookup"><span data-stu-id="3b801-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b801-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="3b801-112">See also</span></span>

- [<span data-ttu-id="3b801-113">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="3b801-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="3b801-114">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="3b801-114">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="3b801-115">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="3b801-115">Button Control</span></span>](button-control-windows-forms.md)
