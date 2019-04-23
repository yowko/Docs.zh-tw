---
title: 選取 Windows Form Button 控制項的方法
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: f2881646a05d257044c6461f822a4c35a225f8c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223286"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="6a07b-102">選取 Windows Form Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="6a07b-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="6a07b-103">將 Windows Form 按鈕可以下列方式選取：</span><span class="sxs-lookup"><span data-stu-id="6a07b-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
-   <span data-ttu-id="6a07b-104">使用滑鼠按一下的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6a07b-104">Use a mouse to click the button.</span></span>  
  
-   <span data-ttu-id="6a07b-105">叫用按鈕的<xref:System.Windows.Forms.Control.Click>在程式碼中的事件。</span><span class="sxs-lookup"><span data-stu-id="6a07b-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
-   <span data-ttu-id="6a07b-106">藉由按下 TAB 鍵，將焦點移至 按鈕，然後選擇該按鈕按下空格鍵或 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="6a07b-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
-   <span data-ttu-id="6a07b-107">按下便捷鍵 （ALT + 加底線的字母） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6a07b-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="6a07b-108">如需存取金鑰的詳細資訊，請參閱[How to:建立 Windows form 控制項的便捷鍵](how-to-create-access-keys-for-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="6a07b-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
-   <span data-ttu-id="6a07b-109">如果表單的 接受 按鈕的按鈕，按下 ENTER 鍵會選擇該按鈕，即使另一個控制項有焦點，但如果控制項是另一個按鈕、 多行文字 方塊中或自訂控制項的設陷 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="6a07b-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
-   <span data-ttu-id="6a07b-110">如果按鈕是 「 取消 」 按鈕的表單，按下 esc 鍵會選擇 [] 按鈕，即使另一個控制項有焦點。</span><span class="sxs-lookup"><span data-stu-id="6a07b-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
-   <span data-ttu-id="6a07b-111">呼叫<xref:System.Windows.Forms.Button.PerformClick%2A>方法來以程式設計方式選取的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6a07b-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a07b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a07b-112">See also</span></span>

- [<span data-ttu-id="6a07b-113">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="6a07b-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="6a07b-114">如何：回應 Windows Form Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="6a07b-114">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="6a07b-115">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="6a07b-115">Button Control</span></span>](button-control-windows-forms.md)
