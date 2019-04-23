---
title: Splitter 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 0477f68aaf67d4b29c491052999ff7784e736669
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176406"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="9895e-102">Splitter 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="9895e-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="9895e-103">雖然<xref:System.Windows.Forms.SplitContainer>取代，並將功能加入至<xref:System.Windows.Forms.Splitter>先前的版本控制<xref:System.Windows.Forms.Splitter>您可以選擇保留回溯相容性以及供未來使用。</span><span class="sxs-lookup"><span data-stu-id="9895e-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="9895e-104">Windows Form<xref:System.Windows.Forms.Splitter>控制項可用來在執行階段調整停駐的控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="9895e-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="9895e-105"><xref:System.Windows.Forms.Splitter>控制項通常用於與各種長度的資料，呈現，例如 Windows 檔案總管中，其資料 窗格包含在不同時間的變動寬度資訊的控制項的表單上。</span><span class="sxs-lookup"><span data-stu-id="9895e-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="9895e-106">使用分隔器控制項</span><span class="sxs-lookup"><span data-stu-id="9895e-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="9895e-107">當使用者將滑鼠指標指向邊緣停駐的可調整大小的分隔器控制項的控制項時，指標會變更其外觀，表示控制項可以調整大小。</span><span class="sxs-lookup"><span data-stu-id="9895e-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="9895e-108">使用分隔器控制項，使用者可以調整大小它前面的停駐的控制項。</span><span class="sxs-lookup"><span data-stu-id="9895e-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="9895e-109">因此，若要啟用使用者調整停駐的控制項大小在執行階段，容器中，邊緣調整大小的控制項停駐，並接著將分隔器控制項停駐容器的同一邊。</span><span class="sxs-lookup"><span data-stu-id="9895e-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9895e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9895e-110">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="9895e-111">如何：停駐在 Windows Forms 上控制項</span><span class="sxs-lookup"><span data-stu-id="9895e-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="9895e-112">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="9895e-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
