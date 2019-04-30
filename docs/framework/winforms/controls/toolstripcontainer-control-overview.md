---
title: ToolStripContainer 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
ms.openlocfilehash: c279316c2a372a1498707b27ec8658813306304b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009470"
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="28380-102">ToolStripContainer 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="28380-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="28380-103">A<xref:System.Windows.Forms.ToolStripContainer>有個面板其左、 右、 上框線和下側邊的定位和浮動定位<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.MenuStrip>，和<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="28380-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="28380-104">如果您將多個 <xref:System.Windows.Forms.ToolStrip> 控制項放在左邊或右邊 <xref:System.Windows.Forms.ToolStripContainer>，它們會垂直堆疊。</span><span class="sxs-lookup"><span data-stu-id="28380-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="28380-105">如果您將它們放在頂端或底端 <xref:System.Windows.Forms.ToolStripContainer>，它們會水平堆疊。</span><span class="sxs-lookup"><span data-stu-id="28380-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="28380-106">您可以使用 <xref:System.Windows.Forms.ToolStripContainer> 的中央 <xref:System.Windows.Forms.ToolStripContentPanel>來定位在表單上的傳統控制項。</span><span class="sxs-lookup"><span data-stu-id="28380-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="28380-107">任何或所有 <xref:System.Windows.Forms.ToolStripContainer> 控制項可直接在設計階段選取，而且可以刪除。</span><span class="sxs-lookup"><span data-stu-id="28380-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="28380-108">每個面板<xref:System.Windows.Forms.ToolStripContainer>是可展開及摺疊，並與它所包含的控制項調整大小。</span><span class="sxs-lookup"><span data-stu-id="28380-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="28380-109">重要 ToolStripContainer 成員</span><span class="sxs-lookup"><span data-stu-id="28380-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="28380-110">名稱</span><span class="sxs-lookup"><span data-stu-id="28380-110">Name</span></span>|<span data-ttu-id="28380-111">描述</span><span class="sxs-lookup"><span data-stu-id="28380-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="28380-112">取得的下方面板<xref:System.Windows.Forms.ToolStripContainer>。</span><span class="sxs-lookup"><span data-stu-id="28380-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="28380-113">取得或設定值，指出是否的下方面板<xref:System.Windows.Forms.ToolStripContainer>為可見。</span><span class="sxs-lookup"><span data-stu-id="28380-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="28380-114">取得的左方的面板<xref:System.Windows.Forms.ToolStripContainer>。</span><span class="sxs-lookup"><span data-stu-id="28380-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="28380-115">取得或設定值，指出是否的左方的面板<xref:System.Windows.Forms.ToolStripContainer>為可見。</span><span class="sxs-lookup"><span data-stu-id="28380-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="28380-116">取得的右方面板<xref:System.Windows.Forms.ToolStripContainer>。</span><span class="sxs-lookup"><span data-stu-id="28380-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="28380-117">取得或設定值，指出是否的右方面板<xref:System.Windows.Forms.ToolStripContainer>為可見。</span><span class="sxs-lookup"><span data-stu-id="28380-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="28380-118">取得的上方面板<xref:System.Windows.Forms.ToolStripContainer>。</span><span class="sxs-lookup"><span data-stu-id="28380-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="28380-119">取得或設定值，指出是否的上方面板<xref:System.Windows.Forms.ToolStripContainer>為可見。</span><span class="sxs-lookup"><span data-stu-id="28380-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28380-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28380-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- <xref:System.Windows.Forms.ToolStripContentPanel>
