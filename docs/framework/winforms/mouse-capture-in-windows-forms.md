---
title: 滑鼠捕捉
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 10583f074831b16dce3c713b4ac9a76c7005c9f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741027"
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="e2461-102">Windows Form 中的滑鼠捕捉</span><span class="sxs-lookup"><span data-stu-id="e2461-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="e2461-103">*滑鼠捕捉*是指控制項取得所有滑鼠輸入的命令時。</span><span class="sxs-lookup"><span data-stu-id="e2461-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="e2461-104">當控制項捕捉到滑鼠時，不論指標是否在其框線內，它都會收到滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="e2461-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="e2461-105">設定滑鼠捕捉</span><span class="sxs-lookup"><span data-stu-id="e2461-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="e2461-106">在 Windows Forms 當使用者在控制項上按下滑鼠按鍵時，控制項會捕捉滑鼠，而當使用者放開滑鼠按鍵時，控制項就會放開滑鼠。</span><span class="sxs-lookup"><span data-stu-id="e2461-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="e2461-107"><xref:System.Windows.Forms.Control> 類別的 <xref:System.Windows.Forms.Control.Capture%2A> 屬性會指定控制項是否已捕捉滑鼠。</span><span class="sxs-lookup"><span data-stu-id="e2461-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="e2461-108">若要判斷控制項何時失去滑鼠捕捉，請處理 <xref:System.Windows.Forms.Control.MouseCaptureChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="e2461-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="e2461-109">只有前景視窗可以捕捉滑鼠。</span><span class="sxs-lookup"><span data-stu-id="e2461-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="e2461-110">當背景視窗嘗試捕獲滑鼠時，只有當滑鼠指標位於視窗的可見部分內時，視窗才會收到滑鼠事件的訊息。</span><span class="sxs-lookup"><span data-stu-id="e2461-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="e2461-111">此外，即使前景視窗已捕捉過滑鼠，使用者仍然可以按一下另一個視窗，將其移至前景。</span><span class="sxs-lookup"><span data-stu-id="e2461-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="e2461-112">當您捕捉到滑鼠時，快速鍵無法正常執行。</span><span class="sxs-lookup"><span data-stu-id="e2461-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2461-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2461-113">See also</span></span>

- [<span data-ttu-id="e2461-114">Windows Forms 應用程式中的滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="e2461-114">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
