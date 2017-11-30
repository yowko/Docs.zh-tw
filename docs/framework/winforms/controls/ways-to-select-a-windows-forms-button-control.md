---
title: "選取 Windows Form Button 控制項的方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08b5359446a80da257f5afec07cc70e3d4aad46b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="0fdab-102">選取 Windows Form Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="0fdab-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="0fdab-103">以下列方式，可以選取 Windows Form 按鈕：</span><span class="sxs-lookup"><span data-stu-id="0fdab-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
-   <span data-ttu-id="0fdab-104">按一下按鈕，使用滑鼠。</span><span class="sxs-lookup"><span data-stu-id="0fdab-104">Use a mouse to click the button.</span></span>  
  
-   <span data-ttu-id="0fdab-105">叫用按鈕的<xref:System.Windows.Forms.Control.Click>程式碼中的事件。</span><span class="sxs-lookup"><span data-stu-id="0fdab-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
-   <span data-ttu-id="0fdab-106">按下 TAB 鍵，將焦點移至按鈕，然後選擇該按鈕按下空格鍵或 ENTER。</span><span class="sxs-lookup"><span data-stu-id="0fdab-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
-   <span data-ttu-id="0fdab-107">按下便捷鍵 （ALT + 加底線的字母） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0fdab-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="0fdab-108">如需存取金鑰的詳細資訊，請參閱[How to： 建立存取金鑰的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="0fdab-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
-   <span data-ttu-id="0fdab-109">如果按鈕是 [接受] 按鈕的形式，按下 ENTER 鍵會選擇該按鈕，即使另一個控制項有焦點，除非控制項是另一個按鈕、 多行文字方塊中或自訂控制項的 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="0fdab-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
-   <span data-ttu-id="0fdab-110">如果按鈕是表單的 「 取消 」 按鈕，按下 esc 鍵選擇該按鈕，即使另一個控制項有焦點。</span><span class="sxs-lookup"><span data-stu-id="0fdab-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
-   <span data-ttu-id="0fdab-111">呼叫<xref:System.Windows.Forms.Button.PerformClick%2A>方法來以程式設計方式選取按鈕。</span><span class="sxs-lookup"><span data-stu-id="0fdab-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fdab-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fdab-112">See Also</span></span>  
 [<span data-ttu-id="0fdab-113">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="0fdab-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="0fdab-114">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="0fdab-114">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="0fdab-115">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="0fdab-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
