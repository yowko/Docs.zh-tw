---
title: 如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項
description: 瞭解如何以程式設計方式錨定和停駐 Windows Forms FlowLayoutPanel 控制項中的子控制項。
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: b4fb3bf6d148a526a75926bd67c1f967286332bf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174532"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="dd014-103">如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="dd014-103">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>

<span data-ttu-id="dd014-104"><xref:System.Windows.Forms.FlowLayoutPanel> 控制項在其子控制項中支援 <xref:System.Windows.Forms.Control.Anchor%2A> 和 <xref:System.Windows.Forms.Control.Dock%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="dd014-104">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="dd014-105">錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="dd014-105">To anchor and dock child controls in a FlowLayoutPanel control</span></span>

1. <span data-ttu-id="dd014-106">請在表單上建立 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="dd014-106">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>

2. <span data-ttu-id="dd014-107">將 <xref:System.Windows.Forms.Control.Width%2A> 控制項的設定 <xref:System.Windows.Forms.FlowLayoutPanel> 為**300**，並將其設定 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 為 <xref:System.Windows.Forms.FlowDirection.TopDown> 。</span><span class="sxs-lookup"><span data-stu-id="dd014-107">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

3. <span data-ttu-id="dd014-108">建立兩個 <xref:System.Windows.Forms.Button> 控制項，並置入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="dd014-108">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

4. <span data-ttu-id="dd014-109">將 <xref:System.Windows.Forms.Control.Width%2A> 第一個按鈕的設為**200**。</span><span class="sxs-lookup"><span data-stu-id="dd014-109">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>

5. <span data-ttu-id="dd014-110">將第二個按鈕的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="dd014-110">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="dd014-111">第二個按鈕會假設與第一個按鈕的寬度相同。</span><span class="sxs-lookup"><span data-stu-id="dd014-111">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="dd014-112">它不會自動縮放 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的寬度。</span><span class="sxs-lookup"><span data-stu-id="dd014-112">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="dd014-113">將第二個按鈕的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="dd014-113">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="dd014-114">這會使按鈕假設為原始的寬度。</span><span class="sxs-lookup"><span data-stu-id="dd014-114">This causes the button to assume its original width.</span></span>

7. <span data-ttu-id="dd014-115">將第二個按鈕的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設為 `Left, Right`。</span><span class="sxs-lookup"><span data-stu-id="dd014-115">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="dd014-116">第二個按鈕會假設與第一個按鈕的寬度相同。</span><span class="sxs-lookup"><span data-stu-id="dd014-116">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="dd014-117">它不會自動縮放 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的寬度。</span><span class="sxs-lookup"><span data-stu-id="dd014-117">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="dd014-118">這是在 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項錨定和停駐的一般規則：對於垂直流動方向，<xref:System.Windows.Forms.FlowLayoutPanel> 控制項會計算資料行中最寬子控制項的隱含資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="dd014-118">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="dd014-119">此資料行中具有 <xref:System.Windows.Forms.Control.Anchor%2A> 或 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的所有其他控制項會配合隱含資料行對齊或自動縮放。</span><span class="sxs-lookup"><span data-stu-id="dd014-119">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="dd014-120">此行為的運作方式類似水平流動方向。</span><span class="sxs-lookup"><span data-stu-id="dd014-120">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="dd014-121"><xref:System.Windows.Forms.FlowLayoutPanel> 控制項由此資料列中最高子控制項的高度計算隱含資料列的高度，在此資料列中所有停駐或錨定的子控制項會配合隱含資料列對齊或調整大小。</span><span class="sxs-lookup"><span data-stu-id="dd014-121">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>

## <a name="example"></a><span data-ttu-id="dd014-122">範例</span><span class="sxs-lookup"><span data-stu-id="dd014-122">Example</span></span>

<span data-ttu-id="dd014-123">下圖顯示四個按鈕，相對於藍色按鈕錨定和停駐在 <xref:System.Windows.Forms.FlowLayoutPanel>。</span><span class="sxs-lookup"><span data-stu-id="dd014-123">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="dd014-124"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 為 <xref:System.Windows.Forms.FlowDirection.LeftToRight>。</span><span class="sxs-lookup"><span data-stu-id="dd014-124">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>

<span data-ttu-id="dd014-125">![FlowLayoutPanel 錨定](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="dd014-125">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>

<span data-ttu-id="dd014-126">下圖顯示四個按鈕，相對於藍色按鈕錨定和停駐在 <xref:System.Windows.Forms.FlowLayoutPanel>。</span><span class="sxs-lookup"><span data-stu-id="dd014-126">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="dd014-127"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 為 <xref:System.Windows.Forms.FlowDirection.TopDown>。</span><span class="sxs-lookup"><span data-stu-id="dd014-127">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

<span data-ttu-id="dd014-128">![FlowLayoutPanel 錨定](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="dd014-128">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>

<span data-ttu-id="dd014-129">下列程式碼範例示範 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中的 <xref:System.Windows.Forms.Button> 控制項之不同的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="dd014-129">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a><span data-ttu-id="dd014-130">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="dd014-130">Compiling the Code</span></span>

<span data-ttu-id="dd014-131">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="dd014-131">This example requires:</span></span>

- <span data-ttu-id="dd014-132">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="dd014-132">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd014-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd014-133">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="dd014-134">FlowLayoutPanel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="dd014-134">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
