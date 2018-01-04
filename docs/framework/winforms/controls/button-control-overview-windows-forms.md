---
title: "Button 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e04b99c9d85ae92ad4d013abc01c5b16914fe1c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="button-control-overview-windows-forms"></a><span data-ttu-id="22f8c-102">Button 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="22f8c-102">Button Control Overview (Windows Forms)</span></span>
<span data-ttu-id="22f8c-103">Windows Form <xref:System.Windows.Forms.Button> 控制項可讓使用者按一下以執行動作。</span><span class="sxs-lookup"><span data-stu-id="22f8c-103">The Windows Forms <xref:System.Windows.Forms.Button> control allows the user to click it to perform an action.</span></span> <span data-ttu-id="22f8c-104">按一下按鈕時，按鈕看起來就像被推入又釋放。</span><span class="sxs-lookup"><span data-stu-id="22f8c-104">When the button is clicked, it looks as if it is being pushed in and released.</span></span> <span data-ttu-id="22f8c-105">每當使用者按一下按鈕，<xref:System.Windows.Forms.Control.Click>叫用事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="22f8c-105">Whenever the user clicks a button, the <xref:System.Windows.Forms.Control.Click> event handler is invoked.</span></span> <span data-ttu-id="22f8c-106">您將程式碼放入<xref:System.Windows.Forms.Control.Click>事件處理常式來執行您所選擇的任何動作。</span><span class="sxs-lookup"><span data-stu-id="22f8c-106">You place code in the <xref:System.Windows.Forms.Control.Click> event handler to perform any action you choose.</span></span>  
  
 <span data-ttu-id="22f8c-107">在按鈕上顯示的文字包含於<xref:System.Windows.Forms.Control.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="22f8c-107">The text displayed on the button is contained in the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="22f8c-108">如果您的文字超過按鈕的寬度，它會自動換行至下一行。</span><span class="sxs-lookup"><span data-stu-id="22f8c-108">If your text exceeds the width of the button, it will wrap to the next line.</span></span> <span data-ttu-id="22f8c-109">不過，它會裁剪若控制項無法容納的整個高度。</span><span class="sxs-lookup"><span data-stu-id="22f8c-109">However, it will be clipped if the control cannot accommodate its overall height.</span></span> <span data-ttu-id="22f8c-110">如需詳細資訊，請參閱[How to： 設定 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)。</span><span class="sxs-lookup"><span data-stu-id="22f8c-110">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span> <span data-ttu-id="22f8c-111"><xref:System.Windows.Forms.Control.Text%2A>屬性可以包含便捷鍵可讓使用者控制 「 按一下 」 藉由按下 ALT 鍵及存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="22f8c-111">The <xref:System.Windows.Forms.Control.Text%2A> property can contain an access key, which allows a user to "click" the control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="22f8c-112">如需詳細資訊，請參閱[How to： 建立存取金鑰的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="22f8c-112">For details, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span> <span data-ttu-id="22f8c-113">文字的外觀由<xref:System.Windows.Forms.Control.Font%2A>屬性和<xref:System.Windows.Forms.ButtonBase.TextAlign%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="22f8c-113">The appearance of the text is controlled by the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> property.</span></span>  
  
 <span data-ttu-id="22f8c-114"><xref:System.Windows.Forms.Button>控制項也可以顯示使用的影像<xref:System.Windows.Forms.ButtonBase.Image%2A>和<xref:System.Windows.Forms.ButtonBase.ImageList%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="22f8c-114">The <xref:System.Windows.Forms.Button> control can also display images using the <xref:System.Windows.Forms.ButtonBase.Image%2A> and <xref:System.Windows.Forms.ButtonBase.ImageList%2A> properties.</span></span> <span data-ttu-id="22f8c-115">如需詳細資訊，請參閱[How to： 設定 Windows Form 控制項所顯示的影像](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)。</span><span class="sxs-lookup"><span data-stu-id="22f8c-115">For more information, see [How to: Set the Image Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f8c-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="22f8c-116">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="22f8c-117">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="22f8c-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="22f8c-118">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="22f8c-118">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="22f8c-119">操作說明：使用設計工具將 Windows Forms 按鈕指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="22f8c-119">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="22f8c-120">操作說明：使用設計工具將 Windows Forms 按鈕指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="22f8c-120">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="22f8c-121">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="22f8c-121">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
