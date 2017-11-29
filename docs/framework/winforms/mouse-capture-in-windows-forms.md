---
title: "Windows Form 中的滑鼠捕捉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8004b05ea25341a142bfcfd9ae812ee3bebd6d5b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="fd05c-102">Windows Form 中的滑鼠捕捉</span><span class="sxs-lookup"><span data-stu-id="fd05c-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="fd05c-103">*將滑鼠擷取*指的是當控制項接受所有的滑鼠輸入的命令。</span><span class="sxs-lookup"><span data-stu-id="fd05c-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="fd05c-104">當控制項捕捉住滑鼠時，不論是否在指標位於其框線內接收滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="fd05c-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="fd05c-105">設定滑鼠捕捉</span><span class="sxs-lookup"><span data-stu-id="fd05c-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="fd05c-106">在 Windows Form 中將滑鼠擷取控制項時，使用者按下滑鼠按鈕控制項，以及當使用者放開滑鼠按鈕控制項放開滑鼠。</span><span class="sxs-lookup"><span data-stu-id="fd05c-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="fd05c-107"><xref:System.Windows.Forms.Control.Capture%2A>屬性<xref:System.Windows.Forms.Control>類別可讓您指定控制項是否捕捉住滑鼠。</span><span class="sxs-lookup"><span data-stu-id="fd05c-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="fd05c-108">若要判斷當控制項失去滑鼠擷取，請處理<xref:System.Windows.Forms.Control.MouseCaptureChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="fd05c-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="fd05c-109">前景視窗可以捕捉滑鼠。</span><span class="sxs-lookup"><span data-stu-id="fd05c-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="fd05c-110">當背景視窗嘗試捕捉滑鼠時，視窗會收到滑鼠指標位於視窗的可見部分時發生的滑鼠事件的訊息。</span><span class="sxs-lookup"><span data-stu-id="fd05c-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="fd05c-111">此外，即使前景視窗已捕捉滑鼠，使用者仍然可以按一下另一個視窗中，將其帶至前景。</span><span class="sxs-lookup"><span data-stu-id="fd05c-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="fd05c-112">當滑鼠捕捉時，快速鍵無法運作。</span><span class="sxs-lookup"><span data-stu-id="fd05c-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd05c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd05c-113">See Also</span></span>  
 [<span data-ttu-id="fd05c-114">Windows Forms 應用程式中的滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="fd05c-114">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
