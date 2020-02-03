---
title: 控制項的版面配置
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- sizing [Windows Forms], automatic [Windows Forms]
- Margin property [Windows Forms]
- Padding property [Windows Forms]
ms.assetid: 99400e3a-720e-4f56-b68f-89df911a251c
ms.openlocfilehash: ed8603e997e7d0c1ed7a2ebda6dc960726d32f45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745242"
---
# <a name="layout-in-windows-forms-controls"></a><span data-ttu-id="90dc6-102">Windows Form 控制項中的配置</span><span class="sxs-lookup"><span data-stu-id="90dc6-102">Layout in Windows Forms Controls</span></span>

<span data-ttu-id="90dc6-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="90dc6-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="90dc6-104"><xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間提供您許多版面組態工具來完成此動作。</span><span class="sxs-lookup"><span data-stu-id="90dc6-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout tools to accomplish this.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="90dc6-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="90dc6-105">In This Section</span></span>

<span data-ttu-id="90dc6-106">[AutoSize 屬性總覽](autosize-property-overview.md)</span><span class="sxs-lookup"><span data-stu-id="90dc6-106">[AutoSize Property Overview](autosize-property-overview.md)</span></span>\
<span data-ttu-id="90dc6-107">描述 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性及其在版面配置中的角色。</span><span class="sxs-lookup"><span data-stu-id="90dc6-107">Describes the <xref:System.Windows.Forms.Control.AutoSize%2A> property and its role in layout.</span></span>

<span data-ttu-id="90dc6-108">[Windows Forms 控制項中的邊界和填補](margin-and-padding-in-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="90dc6-108">[Margin and Padding in Windows Forms Controls](margin-and-padding-in-windows-forms-controls.md)</span></span>\
<span data-ttu-id="90dc6-109">描述 <xref:System.Windows.Forms.Control.Margin%2A> 和 <xref:System.Windows.Forms.Control.Padding%2A> 屬性及其在版面配置中的角色。</span><span class="sxs-lookup"><span data-stu-id="90dc6-109">Describes the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties and their roles in layout.</span></span>

<span data-ttu-id="90dc6-110">[如何：將控制項對齊表單的邊緣](how-to-align-a-control-to-the-edges-of-forms.md)</span><span class="sxs-lookup"><span data-stu-id="90dc6-110">[How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md)</span></span>\
<span data-ttu-id="90dc6-111">示範如何使用 [<xref:System.Windows.Forms.Control.Dock%2A>] 屬性，將您的控制項對齊它所佔用表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="90dc6-111">Demonstrates how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="90dc6-112">[如何：使用填補\ 在 Windows Forms 控制項周圍建立框線](how-to-create-a-border-around-a-windows-forms-control-using-padding.md)</span><span class="sxs-lookup"><span data-stu-id="90dc6-112">[How to: Create a Border Around a Windows Forms Control Using Padding](how-to-create-a-border-around-a-windows-forms-control-using-padding.md)\</span></span>
<span data-ttu-id="90dc6-113">示範如何使用 <xref:System.Windows.Forms.Control.Padding%2A> 屬性來概述控制項。</span><span class="sxs-lookup"><span data-stu-id="90dc6-113">Demonstrates how to use the <xref:System.Windows.Forms.Control.Padding%2A> property to outline a control.</span></span>

<span data-ttu-id="90dc6-114">[如何：執行自訂配置引擎](how-to-implement-a-custom-layout-engine.md)</span><span class="sxs-lookup"><span data-stu-id="90dc6-114">[How to: Implement a Custom Layout Engine](how-to-implement-a-custom-layout-engine.md)</span></span>\
<span data-ttu-id="90dc6-115">示範如何執行用來排列 Windows Forms 控制項的 <xref:System.Windows.Forms.Layout.LayoutEngine>。</span><span class="sxs-lookup"><span data-stu-id="90dc6-115">Demonstrates how to implement a <xref:System.Windows.Forms.Layout.LayoutEngine> for arranging Windows Forms controls.</span></span>

## <a name="reference"></a><span data-ttu-id="90dc6-116">參考</span><span class="sxs-lookup"><span data-stu-id="90dc6-116">Reference</span></span>

<xref:System.Windows.Forms.TableLayoutPanel>\
<span data-ttu-id="90dc6-117">提供 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="90dc6-117">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

<xref:System.Windows.Forms.FlowLayoutPanel>\
<span data-ttu-id="90dc6-118">提供 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="90dc6-118">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="90dc6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90dc6-119">See also</span></span>

- [<span data-ttu-id="90dc6-120">操作說明：錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="90dc6-120">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="90dc6-121">操作說明：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="90dc6-121">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="90dc6-122">操作說明：設計可適當回應當地語系化的 Windows Forms 配置</span><span class="sxs-lookup"><span data-stu-id="90dc6-122">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="90dc6-123">AutoSize 在 TableLayoutPanel 控制項中的行為</span><span class="sxs-lookup"><span data-stu-id="90dc6-123">AutoSize Behavior in the TableLayoutPanel Control</span></span>](autosize-behavior-in-the-tablelayoutpanel-control.md)
