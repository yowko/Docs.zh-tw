---
title: 如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 183e9ea4a8451b3d1ed59aa5200dd4da22e50cf1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="af4c4-102">如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="af4c4-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="af4c4-103"><xref:System.Windows.Forms.FlowLayoutPanel> 控制項在其子控制項中支援 <xref:System.Windows.Forms.Control.Anchor%2A> 和 <xref:System.Windows.Forms.Control.Dock%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="af4c4-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="af4c4-104">錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="af4c4-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1.  <span data-ttu-id="af4c4-105">請在表單上建立 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="af4c4-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="af4c4-106">設定<xref:System.Windows.Forms.Control.Width%2A>的<xref:System.Windows.Forms.FlowLayoutPanel>控制權傳輸至**300**，並設定其<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>至<xref:System.Windows.Forms.FlowDirection.TopDown>。</span><span class="sxs-lookup"><span data-stu-id="af4c4-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3.  <span data-ttu-id="af4c4-107">建立兩個 <xref:System.Windows.Forms.Button> 控制項，並置入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="af4c4-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="af4c4-108">設定<xref:System.Windows.Forms.Control.Width%2A>的第一個按鈕**200**。</span><span class="sxs-lookup"><span data-stu-id="af4c4-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5.  <span data-ttu-id="af4c4-109">將第二個按鈕的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="af4c4-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="af4c4-110">第二個按鈕會假設與第一個按鈕的寬度相同。</span><span class="sxs-lookup"><span data-stu-id="af4c4-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="af4c4-111">它不會自動縮放 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的寬度。</span><span class="sxs-lookup"><span data-stu-id="af4c4-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="af4c4-112">將第二個按鈕的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="af4c4-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="af4c4-113">這會使按鈕假設為原始的寬度。</span><span class="sxs-lookup"><span data-stu-id="af4c4-113">This causes the button to assume its original width.</span></span>  
  
7.  <span data-ttu-id="af4c4-114">將第二個按鈕的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設為 `Left, Right`。</span><span class="sxs-lookup"><span data-stu-id="af4c4-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="af4c4-115">第二個按鈕會假設與第一個按鈕的寬度相同。</span><span class="sxs-lookup"><span data-stu-id="af4c4-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="af4c4-116">它不會自動縮放 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的寬度。</span><span class="sxs-lookup"><span data-stu-id="af4c4-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="af4c4-117">這是在 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項錨定和停駐的一般規則：對於垂直流動方向，<xref:System.Windows.Forms.FlowLayoutPanel> 控制項會計算資料行中最寬子控制項的隱含資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="af4c4-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="af4c4-118">此資料行中具有 <xref:System.Windows.Forms.Control.Anchor%2A> 或 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的所有其他控制項會配合隱含資料行對齊或自動縮放。</span><span class="sxs-lookup"><span data-stu-id="af4c4-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="af4c4-119">此行為的運作方式類似水平流動方向。</span><span class="sxs-lookup"><span data-stu-id="af4c4-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="af4c4-120"><xref:System.Windows.Forms.FlowLayoutPanel> 控制項由此資料列中最高子控制項的高度計算隱含資料列的高度，在此資料列中所有停駐或錨定的子控制項會配合隱含資料列對齊或調整大小。</span><span class="sxs-lookup"><span data-stu-id="af4c4-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af4c4-121">範例</span><span class="sxs-lookup"><span data-stu-id="af4c4-121">Example</span></span>  
 <span data-ttu-id="af4c4-122">下圖顯示四個按鈕，相對於藍色按鈕錨定和停駐在 <xref:System.Windows.Forms.FlowLayoutPanel>。</span><span class="sxs-lookup"><span data-stu-id="af4c4-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="af4c4-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 為 <xref:System.Windows.Forms.FlowDirection.LeftToRight>。</span><span class="sxs-lookup"><span data-stu-id="af4c4-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="af4c4-124">![FlowLayoutPanel 錨定](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="af4c4-124">![FlowLayoutPanel anchoring](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="af4c4-125">下圖顯示四個按鈕，相對於藍色按鈕錨定和停駐在 <xref:System.Windows.Forms.FlowLayoutPanel>。</span><span class="sxs-lookup"><span data-stu-id="af4c4-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="af4c4-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 為 <xref:System.Windows.Forms.FlowDirection.TopDown>。</span><span class="sxs-lookup"><span data-stu-id="af4c4-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="af4c4-127">![FlowLayoutPanel 錨定](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="af4c4-127">![FlowLayoutPanel anchoring](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="af4c4-128">下列程式碼範例示範 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中的 <xref:System.Windows.Forms.Button> 控制項之不同的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="af4c4-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="af4c4-129">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="af4c4-129">Compiling the Code</span></span>  
 <span data-ttu-id="af4c4-130">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="af4c4-130">This example requires:</span></span>  
  
-   <span data-ttu-id="af4c4-131">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="af4c4-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="af4c4-132">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="af4c4-132">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="af4c4-133">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="af4c4-133">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="af4c4-134">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="af4c4-134">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af4c4-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af4c4-135">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [<span data-ttu-id="af4c4-136">FlowLayoutPanel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="af4c4-136">FlowLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)
