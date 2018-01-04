---
title: "如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56909c823beca99d277bfbf7a20d39663bcd44ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="e9dac-102">如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="e9dac-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="e9dac-103"><xref:System.Windows.Forms.TableLayoutPanel> 控制項在其子控制項中支援 <xref:System.Windows.Forms.Control.Anchor%2A> 和 <xref:System.Windows.Forms.Control.Dock%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9dac-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="e9dac-104">若要對齊 TableLayoutPanel 儲存格中的子控制項</span><span class="sxs-lookup"><span data-stu-id="e9dac-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="e9dac-105">請在表單上建立 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="e9dac-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="e9dac-106">值設定<xref:System.Windows.Forms.TableLayoutPanel>控制項的<xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>和<xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>屬性**1**。</span><span class="sxs-lookup"><span data-stu-id="e9dac-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3.  <span data-ttu-id="e9dac-107">在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中建立 <xref:System.Windows.Forms.Button> 控制項。</span><span class="sxs-lookup"><span data-stu-id="e9dac-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="e9dac-108"><xref:System.Windows.Forms.Button> 會佔用儲存格的左上角。</span><span class="sxs-lookup"><span data-stu-id="e9dac-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4.  <span data-ttu-id="e9dac-109">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `Left`。</span><span class="sxs-lookup"><span data-stu-id="e9dac-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="e9dac-110"><xref:System.Windows.Forms.Button> 控制項移到與儲存格左框線對齊。</span><span class="sxs-lookup"><span data-stu-id="e9dac-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e9dac-111">此行為不同於其他容器控制項的行為。</span><span class="sxs-lookup"><span data-stu-id="e9dac-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="e9dac-112">在其他容器控制項中，當 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性被設定時，子控制項不會移動，而且當 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性被設定時，錨定的控制項與父容器界限之間的距離固定。</span><span class="sxs-lookup"><span data-stu-id="e9dac-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5.  <span data-ttu-id="e9dac-113">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `Top, Left`。</span><span class="sxs-lookup"><span data-stu-id="e9dac-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="e9dac-114"><xref:System.Windows.Forms.Button> 控制項移到佔用儲存格左上角。</span><span class="sxs-lookup"><span data-stu-id="e9dac-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6.  <span data-ttu-id="e9dac-115">重複步驟 5 的值的`Top, Right`移動<xref:System.Windows.Forms.Button>儲存格右上角的控制項。</span><span class="sxs-lookup"><span data-stu-id="e9dac-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="e9dac-116">使用 `Bottom, Left` 和 `Bottom, Right` 值重複進行。</span><span class="sxs-lookup"><span data-stu-id="e9dac-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="e9dac-117">若要自動縮放 TableLayoutPanel 儲存格中的子控制項</span><span class="sxs-lookup"><span data-stu-id="e9dac-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="e9dac-118">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `Left, Right`。</span><span class="sxs-lookup"><span data-stu-id="e9dac-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="e9dac-119">會調整 <xref:System.Windows.Forms.Button> 控制項的大小，自動縮放整個儲存格。</span><span class="sxs-lookup"><span data-stu-id="e9dac-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e9dac-120">此行為不同於其他容器控制項的行為。</span><span class="sxs-lookup"><span data-stu-id="e9dac-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="e9dac-121">在其他容器控制項中，子控制項不是調整大小的時機<xref:System.Windows.Forms.Control.Anchor%2A>屬性設定為`Left, Right`或`Top, Bottom`。</span><span class="sxs-lookup"><span data-stu-id="e9dac-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2.  <span data-ttu-id="e9dac-122">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `Top, Bottom`。</span><span class="sxs-lookup"><span data-stu-id="e9dac-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="e9dac-123">會調整 <xref:System.Windows.Forms.Button> 控制項的大小，從頂端到底部自動縮放儲存格。</span><span class="sxs-lookup"><span data-stu-id="e9dac-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3.  <span data-ttu-id="e9dac-124">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `Top, Bottom, Left, Right`。</span><span class="sxs-lookup"><span data-stu-id="e9dac-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="e9dac-125">調整 <xref:System.Windows.Forms.Button> 控制項的大小以填滿儲存格。</span><span class="sxs-lookup"><span data-stu-id="e9dac-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4.  <span data-ttu-id="e9dac-126">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值為 `None`。</span><span class="sxs-lookup"><span data-stu-id="e9dac-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="e9dac-127">調整 <xref:System.Windows.Forms.Button> 控制項的大小，並在儲存格中置中。</span><span class="sxs-lookup"><span data-stu-id="e9dac-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5.  <span data-ttu-id="e9dac-128">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值為 <xref:System.Windows.Forms.DockStyle.Left>。</span><span class="sxs-lookup"><span data-stu-id="e9dac-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="e9dac-129"><xref:System.Windows.Forms.Button> 控制項移到與儲存格左框線對齊。</span><span class="sxs-lookup"><span data-stu-id="e9dac-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="e9dac-130">會保留 <xref:System.Windows.Forms.Button> 控制項寬度，但會調整它高度的大小，以垂直方式填滿儲存格。</span><span class="sxs-lookup"><span data-stu-id="e9dac-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e9dac-131">這與在其他容器控制項中發生的行為相同。</span><span class="sxs-lookup"><span data-stu-id="e9dac-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6.  <span data-ttu-id="e9dac-132">變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="e9dac-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="e9dac-133">調整 <xref:System.Windows.Forms.Button> 控制項的大小以填滿儲存格。</span><span class="sxs-lookup"><span data-stu-id="e9dac-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9dac-134">範例</span><span class="sxs-lookup"><span data-stu-id="e9dac-134">Example</span></span>  
 <span data-ttu-id="e9dac-135">下圖顯示錨定在 5 個不同 <xref:System.Windows.Forms.TableLayoutPanel> 資料格的 5 個按鈕。</span><span class="sxs-lookup"><span data-stu-id="e9dac-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="e9dac-136">![TableLayoutPanel 錨定](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="e9dac-136">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="e9dac-137">下圖顯示錨定在 4 個不同 <xref:System.Windows.Forms.TableLayoutPanel> 儲存格角落的 4 個按鈕。</span><span class="sxs-lookup"><span data-stu-id="e9dac-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="e9dac-138">![TableLayoutPanel 錨定](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="e9dac-138">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="e9dac-139">下圖顯示藉由錨定在 3 個不同 <xref:System.Windows.Forms.TableLayoutPanel> 儲存格來自動縮放 3 個按鈕。</span><span class="sxs-lookup"><span data-stu-id="e9dac-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="e9dac-140">![TableLayoutPanel 錨定](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="e9dac-140">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="e9dac-141">下列程式碼範例示範所有 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中的 <xref:System.Windows.Forms.Button> 控制項之 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值組合。</span><span class="sxs-lookup"><span data-stu-id="e9dac-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e9dac-142">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e9dac-142">Compiling the Code</span></span>  
 <span data-ttu-id="e9dac-143">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e9dac-143">This example requires:</span></span>  
  
-   <span data-ttu-id="e9dac-144">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="e9dac-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e9dac-145">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="e9dac-145">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e9dac-146">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="e9dac-146">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="e9dac-147">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="e9dac-147">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9dac-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9dac-148">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="e9dac-149">TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="e9dac-149">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
