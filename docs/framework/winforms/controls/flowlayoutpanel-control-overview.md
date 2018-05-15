---
title: FlowLayoutPanel 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 58d95c2238687b4822155916177172a34c3abb87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="flowlayoutpanel-control-overview"></a><span data-ttu-id="4d95e-102">FlowLayoutPanel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="4d95e-102">FlowLayoutPanel Control Overview</span></span>
<span data-ttu-id="4d95e-103"><xref:System.Windows.Forms.FlowLayoutPanel> 控制項會以水平或垂直的流動方向來排列其內容。</span><span class="sxs-lookup"><span data-stu-id="4d95e-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control arranges its contents in a horizontal or vertical flow direction.</span></span> <span data-ttu-id="4d95e-104">您可以將控制項的內容從一個資料列包裝至下一個資料列，或從一個資料行包裝至下一個資料行。</span><span class="sxs-lookup"><span data-stu-id="4d95e-104">You can wrap the control's contents from one row to the next, or from one column to the next.</span></span> <span data-ttu-id="4d95e-105">或者，您可以用裁剪的方式，而不是包裝其內容。</span><span class="sxs-lookup"><span data-stu-id="4d95e-105">Alternately, you can clip instead of wrap its contents.</span></span>  
  
 <span data-ttu-id="4d95e-106">您可以設定 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 屬性的值來指定文字方向。</span><span class="sxs-lookup"><span data-stu-id="4d95e-106">You can specify the flow direction by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> property.</span></span> <span data-ttu-id="4d95e-107"><xref:System.Windows.Forms.FlowLayoutPanel> 控制項會在「由右至左 (RTL)」配置中，將其文字方向正確地反轉。</span><span class="sxs-lookup"><span data-stu-id="4d95e-107">The <xref:System.Windows.Forms.FlowLayoutPanel> control correctly reverses its flow direction in Right-to-Left (RTL) layouts.</span></span> <span data-ttu-id="4d95e-108">您也可以設定 <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> 屬性的值，指定要包裝或裁剪 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的內容。</span><span class="sxs-lookup"><span data-stu-id="4d95e-108">You can also specify whether the <xref:System.Windows.Forms.FlowLayoutPanel> control's contents are wrapped or clipped by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> property.</span></span>  
  
 <span data-ttu-id="4d95e-109">當您將 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性設為 `true` 時，<xref:System.Windows.Forms.FlowLayoutPanel> 控制項會根據其內容自動調整大小。</span><span class="sxs-lookup"><span data-stu-id="4d95e-109">The <xref:System.Windows.Forms.FlowLayoutPanel> control automatically sizes to its contents when you set the <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="4d95e-110">它也提供**FlowBreak**屬性給它的子控制項。</span><span class="sxs-lookup"><span data-stu-id="4d95e-110">It also provides a **FlowBreak** property to its child controls.</span></span> <span data-ttu-id="4d95e-111">將 FlowBreak 屬性的值設為 `true` ，會導致 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項停止以目前的文字方向來配置控制項，並包裝至下一個資料列或資料行。</span><span class="sxs-lookup"><span data-stu-id="4d95e-111">Setting the value of the FlowBreak property to `true` causes the <xref:System.Windows.Forms.FlowLayoutPanel> control to stop laying out controls in the current flow direction and wrap to the next row or column.</span></span>  
  
 <span data-ttu-id="4d95e-112">任何 Windows Form 控制項都可以是 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的子系，包括 <xref:System.Windows.Forms.FlowLayoutPanel> 的其他執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d95e-112">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.FlowLayoutPanel> control, including other instances of <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="4d95e-113">使用這項功能，您可以建構複雜的配置，以在執行階段調整為表單的維度。</span><span class="sxs-lookup"><span data-stu-id="4d95e-113">With this capability, you can construct sophisticated layouts that adapt to your form's dimensions at run time.</span></span>  
  
 <span data-ttu-id="4d95e-114">另請參閱[逐步解說： 在 Windows Form 使用 FlowLayoutPanel 排列的控制項](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="4d95e-114">Also see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d95e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d95e-115">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="4d95e-116">FlowLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="4d95e-116">FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
