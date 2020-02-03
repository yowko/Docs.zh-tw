---
title: 使用設計工具在 ListView 控制項中啟用並排顯示
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: a0429efaab14995ab1e3f3b0dfd91db61de72fbf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745812"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="66e3d-102">如何：使用設計工具在 Windows Form ListView 控制項中啟用 Tile 檢視</span><span class="sxs-lookup"><span data-stu-id="66e3d-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="66e3d-103"><xref:System.Windows.Forms.ListView> 控制項的 [並排顯示] 功能可讓您在圖形和文字資訊之間提供視覺化平衡。</span><span class="sxs-lookup"><span data-stu-id="66e3d-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="66e3d-104">並排顯示檢視中針對項目顯示的文字資訊與詳細資料檢視所定義的資料行資訊相同。</span><span class="sxs-lookup"><span data-stu-id="66e3d-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="66e3d-105">並排顯示函數與 <xref:System.Windows.Forms.ListView> 控制項中的群組或插入標記功能組合。</span><span class="sxs-lookup"><span data-stu-id="66e3d-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>

 <span data-ttu-id="66e3d-106">磚視圖使用 32 x 32 圖示和數行文字，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="66e3d-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>

 <span data-ttu-id="66e3d-107">![在 ListView 控制項中並排顯示](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "並排顯示的圖示和文字")</span><span class="sxs-lookup"><span data-stu-id="66e3d-107">![Tile View in a ListView Control](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>

 <span data-ttu-id="66e3d-108">磚視圖屬性和方法可讓您指定要針對每個專案顯示的資料列欄位，以及共同控制磚視圖視窗內所有專案的大小和外觀。</span><span class="sxs-lookup"><span data-stu-id="66e3d-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="66e3d-109">為了清楚起見，磚中的第一行文字一律是專案的名稱;無法變更。</span><span class="sxs-lookup"><span data-stu-id="66e3d-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>

 <span data-ttu-id="66e3d-110">下列程式需要具有包含 <xref:System.Windows.Forms.ListView> 控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="66e3d-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="66e3d-111">如需設定這類專案的相關資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="66e3d-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="66e3d-112">在設計工具中設定磚視圖</span><span class="sxs-lookup"><span data-stu-id="66e3d-112">To set tile view in the designer</span></span>

1. <span data-ttu-id="66e3d-113">在 Visual Studio 中，選取表單上的 <xref:System.Windows.Forms.ListView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="66e3d-113">In Visual Studio, select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>

2. <span data-ttu-id="66e3d-114">在 [**屬性**] 視窗中，選取 [<xref:System.Windows.Forms.ListView.View%2A>] 屬性，然後選擇 [**磚**]。</span><span class="sxs-lookup"><span data-stu-id="66e3d-114">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>

## <a name="see-also"></a><span data-ttu-id="66e3d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66e3d-115">See also</span></span>

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="66e3d-116">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="66e3d-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
