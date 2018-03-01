---
title: "Splitter 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32d8829e7303ce23a22d0a01f2428a889ce4ae0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="2a412-102">Splitter 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="2a412-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="2a412-103">雖然<xref:System.Windows.Forms.SplitContainer>取代，並將功能加入<xref:System.Windows.Forms.Splitter>的較舊的版本控制<xref:System.Windows.Forms.Splitter>如果您選擇保留以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="2a412-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="2a412-104">Windows Form<xref:System.Windows.Forms.Splitter>控制項可用來在執行階段調整停駐的控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="2a412-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="2a412-105"><xref:System.Windows.Forms.Splitter>控制項通常用於與各種長度的資料來呈現，如 Windows 檔案總管，其資料窗格會包含在不同時間資訊的變動寬度的控制項的表單上。</span><span class="sxs-lookup"><span data-stu-id="2a412-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="2a412-106">使用分隔器控制項</span><span class="sxs-lookup"><span data-stu-id="2a412-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="2a412-107">當使用者將滑鼠指標指向未停駐控制項可以調整大小的分隔器控制項的邊緣時，指標會變更其外觀，表示控制項可以調整大小。</span><span class="sxs-lookup"><span data-stu-id="2a412-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="2a412-108">使用分隔器控制項，使用者可以調整大小它前面的停駐的控制項。</span><span class="sxs-lookup"><span data-stu-id="2a412-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="2a412-109">因此，若要讓使用者在執行階段調整停駐的控制項的大小，停駐控制項的容器，邊緣所能調整並接著將分隔器控制項停駐容器的同一邊。</span><span class="sxs-lookup"><span data-stu-id="2a412-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a412-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a412-110">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="2a412-111">操作說明：將控制項停駐在 Windows Forms 上</span><span class="sxs-lookup"><span data-stu-id="2a412-111">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="2a412-112">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="2a412-112">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
