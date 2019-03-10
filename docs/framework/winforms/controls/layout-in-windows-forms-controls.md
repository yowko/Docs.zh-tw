---
title: Windows Form 控制項中的配置
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- sizing [Windows Forms], automatic [Windows Forms]
- Margin property [Windows Forms]
- Padding property [Windows Forms]
ms.assetid: 99400e3a-720e-4f56-b68f-89df911a251c
ms.openlocfilehash: d1a3954c8eda87bdda9fa17df1bd2b3858c43619
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711326"
---
# <a name="layout-in-windows-forms-controls"></a><span data-ttu-id="dd987-102">Windows Form 控制項中的配置</span><span class="sxs-lookup"><span data-stu-id="dd987-102">Layout in Windows Forms Controls</span></span>

<span data-ttu-id="dd987-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="dd987-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="dd987-104"><xref:System.Windows.Forms?displayProperty=nameWithType>命名空間會提供您許多版面配置工具，來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="dd987-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout tools to accomplish this.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="dd987-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="dd987-105">In This Section</span></span>

<span data-ttu-id="dd987-106">[AutoSize 屬性概觀](autosize-property-overview.md)\\</span><span class="sxs-lookup"><span data-stu-id="dd987-106">[AutoSize Property Overview](autosize-property-overview.md)\\</span></span>
<span data-ttu-id="dd987-107">描述<xref:System.Windows.Forms.Control.AutoSize%2A>屬性和它在版面配置的角色。</span><span class="sxs-lookup"><span data-stu-id="dd987-107">Describes the <xref:System.Windows.Forms.Control.AutoSize%2A> property and its role in layout.</span></span>

<span data-ttu-id="dd987-108">[邊界和邊框距離在 Windows Form 控制項](margin-and-padding-in-windows-forms-controls.md)\\</span><span class="sxs-lookup"><span data-stu-id="dd987-108">[Margin and Padding in Windows Forms Controls](margin-and-padding-in-windows-forms-controls.md)\\</span></span>
<span data-ttu-id="dd987-109">描述<xref:System.Windows.Forms.Control.Margin%2A>和<xref:System.Windows.Forms.Control.Padding%2A>屬性和其版面配置中的角色。</span><span class="sxs-lookup"><span data-stu-id="dd987-109">Describes the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties and their roles in layout.</span></span>

<span data-ttu-id="dd987-110">[如何：將控制項和表單邊緣對齊](how-to-align-a-control-to-the-edges-of-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="dd987-110">[How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md)\\</span></span>
<span data-ttu-id="dd987-111">示範如何使用<xref:System.Windows.Forms.Control.Dock%2A>屬性，以符合您的控制項，它會佔用表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="dd987-111">Demonstrates how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="dd987-112">[如何：Windows Form 周圍建立框線控制使用的填補](how-to-create-a-border-around-a-windows-forms-control-using-padding.md)\\</span><span class="sxs-lookup"><span data-stu-id="dd987-112">[How to: Create a Border Around a Windows Forms Control Using Padding](how-to-create-a-border-around-a-windows-forms-control-using-padding.md)\\</span></span>
<span data-ttu-id="dd987-113">示範如何使用<xref:System.Windows.Forms.Control.Padding%2A>概述控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="dd987-113">Demonstrates how to use the <xref:System.Windows.Forms.Control.Padding%2A> property to outline a control.</span></span>

<span data-ttu-id="dd987-114">[如何：實作自訂的版面配置引擎](how-to-implement-a-custom-layout-engine.md)\\</span><span class="sxs-lookup"><span data-stu-id="dd987-114">[How to: Implement a Custom Layout Engine](how-to-implement-a-custom-layout-engine.md)\\</span></span>
<span data-ttu-id="dd987-115">示範如何實作<xref:System.Windows.Forms.Layout.LayoutEngine>排列 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="dd987-115">Demonstrates how to implement a <xref:System.Windows.Forms.Layout.LayoutEngine> for arranging Windows Forms controls.</span></span>

## <a name="reference"></a><span data-ttu-id="dd987-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="dd987-116">Reference</span></span>

<xref:System.Windows.Forms.TableLayoutPanel>\
<span data-ttu-id="dd987-117">提供 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="dd987-117">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

<xref:System.Windows.Forms.FlowLayoutPanel>\
<span data-ttu-id="dd987-118">提供 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="dd987-118">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd987-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd987-119">See also</span></span>

- [<span data-ttu-id="dd987-120">如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="dd987-120">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="dd987-121">如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="dd987-121">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="dd987-122">如何：設計可適當回應當地語系化的 Windows Forms 配置</span><span class="sxs-lookup"><span data-stu-id="dd987-122">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="dd987-123">AutoSize 在 TableLayoutPanel 控制項中的行為</span><span class="sxs-lookup"><span data-stu-id="dd987-123">AutoSize Behavior in the TableLayoutPanel Control</span></span>](autosize-behavior-in-the-tablelayoutpanel-control.md)
