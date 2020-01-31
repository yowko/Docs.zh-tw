---
title: Button 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 4ba7b333e5414efb4814d64ce50c55e08b27f859
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747084"
---
# <a name="button-control-overview-windows-forms"></a><span data-ttu-id="8e981-102">Button 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="8e981-102">Button Control Overview (Windows Forms)</span></span>
<span data-ttu-id="8e981-103">Windows Form <xref:System.Windows.Forms.Button> 控制項可讓使用者按一下以執行動作。</span><span class="sxs-lookup"><span data-stu-id="8e981-103">The Windows Forms <xref:System.Windows.Forms.Button> control allows the user to click it to perform an action.</span></span> <span data-ttu-id="8e981-104">按一下按鈕時，按鈕看起來就像被推入又釋放。</span><span class="sxs-lookup"><span data-stu-id="8e981-104">When the button is clicked, it looks as if it is being pushed in and released.</span></span> <span data-ttu-id="8e981-105">每當使用者按一下按鈕時，就會叫用 <xref:System.Windows.Forms.Control.Click> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e981-105">Whenever the user clicks a button, the <xref:System.Windows.Forms.Control.Click> event handler is invoked.</span></span> <span data-ttu-id="8e981-106">您會將程式碼放在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中，以執行您所選擇的任何動作。</span><span class="sxs-lookup"><span data-stu-id="8e981-106">You place code in the <xref:System.Windows.Forms.Control.Click> event handler to perform any action you choose.</span></span>  
  
 <span data-ttu-id="8e981-107">顯示在按鈕上的文字會包含在 [<xref:System.Windows.Forms.Control.Text%2A>] 屬性中。</span><span class="sxs-lookup"><span data-stu-id="8e981-107">The text displayed on the button is contained in the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="8e981-108">如果您的文字超過按鈕的寬度，則會換行至下一行。</span><span class="sxs-lookup"><span data-stu-id="8e981-108">If your text exceeds the width of the button, it will wrap to the next line.</span></span> <span data-ttu-id="8e981-109">不過，如果控制項無法容納其整體高度，則會加以裁剪。</span><span class="sxs-lookup"><span data-stu-id="8e981-109">However, it will be clipped if the control cannot accommodate its overall height.</span></span> <span data-ttu-id="8e981-110">如需詳細資訊，請參閱[如何：設定 Windows Forms 控制項所顯示的文字](how-to-set-the-text-displayed-by-a-windows-forms-control.md)。</span><span class="sxs-lookup"><span data-stu-id="8e981-110">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span> <span data-ttu-id="8e981-111"><xref:System.Windows.Forms.Control.Text%2A> 屬性可以包含存取金鑰，這可讓使用者按下 ALT 鍵與存取金鑰以「按一下」控制項。</span><span class="sxs-lookup"><span data-stu-id="8e981-111">The <xref:System.Windows.Forms.Control.Text%2A> property can contain an access key, which allows a user to "click" the control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="8e981-112">如需詳細資訊，請參閱[如何：建立 Windows Forms 控制項的存取金鑰](how-to-create-access-keys-for-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="8e981-112">For details, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span> <span data-ttu-id="8e981-113">文字的外觀是由 [<xref:System.Windows.Forms.Control.Font%2A>] 屬性和 [<xref:System.Windows.Forms.ButtonBase.TextAlign%2A>] 屬性所控制。</span><span class="sxs-lookup"><span data-stu-id="8e981-113">The appearance of the text is controlled by the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> property.</span></span>  
  
 <span data-ttu-id="8e981-114"><xref:System.Windows.Forms.Button> 控制項也可以使用 <xref:System.Windows.Forms.ButtonBase.Image%2A> 和 <xref:System.Windows.Forms.ButtonBase.ImageList%2A> 屬性來顯示影像。</span><span class="sxs-lookup"><span data-stu-id="8e981-114">The <xref:System.Windows.Forms.Button> control can also display images using the <xref:System.Windows.Forms.ButtonBase.Image%2A> and <xref:System.Windows.Forms.ButtonBase.ImageList%2A> properties.</span></span> <span data-ttu-id="8e981-115">如需詳細資訊，請參閱[如何：設定 Windows Forms 控制項所顯示的影像](how-to-set-the-image-displayed-by-a-windows-forms-control.md)。</span><span class="sxs-lookup"><span data-stu-id="8e981-115">For more information, see [How to: Set the Image Displayed by a Windows Forms Control](how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e981-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="8e981-116">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="8e981-117">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="8e981-117">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="8e981-118">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="8e981-118">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="8e981-119">如何：使用設計工具將 Windows Forms 按鈕指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="8e981-119">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [<span data-ttu-id="8e981-120">如何：使用設計工具將 Windows Forms 按鈕指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="8e981-120">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [<span data-ttu-id="8e981-121">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="8e981-121">Button Control</span></span>](button-control-windows-forms.md)
