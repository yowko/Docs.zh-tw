---
title: HOW TO：啟用並排顯示檢視中使用設計工具將 Windows Forms ListView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 0acd235fe015b3f93364482b83008b388c1b86d9
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303968"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="e9203-102">HOW TO：啟用並排顯示檢視中使用設計工具將 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="e9203-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="e9203-103">並排顯示檢視功能<xref:System.Windows.Forms.ListView>控制項可讓您提供圖形和文字資訊之間的視覺化平衡。</span><span class="sxs-lookup"><span data-stu-id="e9203-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="e9203-104">並排顯示檢視中針對項目顯示的文字資訊與詳細資料檢視所定義的資料行資訊相同。</span><span class="sxs-lookup"><span data-stu-id="e9203-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="e9203-105">並排顯示檢視函式搭配的群組 」 或 「 插入標記功能<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="e9203-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="e9203-106">並排顯示檢視會使用 32x32 圖示和數行文字，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e9203-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>  
  
 <span data-ttu-id="e9203-107">![ListView 控制項中並排](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="e9203-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
  
 <span data-ttu-id="e9203-108">並排顯示屬性和方法可讓您指定的資料行欄位，顯示針對每個項目，以及共同控制的大小和並排顯示檢視 視窗中的所有項目的外觀。</span><span class="sxs-lookup"><span data-stu-id="e9203-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="e9203-109">為了清楚起見，在圖格中的第一行一律是文字的項目的名稱;無法變更。</span><span class="sxs-lookup"><span data-stu-id="e9203-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>  
  
 <span data-ttu-id="e9203-110">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="e9203-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="e9203-111">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e9203-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9203-112">並排顯示檢視是僅在您的應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法時適用於 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上。</span><span class="sxs-lookup"><span data-stu-id="e9203-112">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e9203-113">在舊版作業系統中，任何與並排顯示檢視相關的程式碼都無效，而且 <xref:System.Windows.Forms.ListView> 控制項會顯示在大圖示檢視中。</span><span class="sxs-lookup"><span data-stu-id="e9203-113">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="e9203-114">如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e9203-114">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="e9203-115">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="e9203-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e9203-116">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="e9203-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e9203-117">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="e9203-117">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="e9203-118">若要在設計師中設定並排顯示檢視</span><span class="sxs-lookup"><span data-stu-id="e9203-118">To set tile view in the designer</span></span>  
  
1.  <span data-ttu-id="e9203-119">選取<xref:System.Windows.Forms.ListView>您表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="e9203-119">Select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>  
  
2.  <span data-ttu-id="e9203-120">在 **屬性**視窗中，選取<xref:System.Windows.Forms.ListView.View%2A>屬性，然後選擇**圖格**。</span><span class="sxs-lookup"><span data-stu-id="e9203-120">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9203-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9203-121">See also</span></span>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="e9203-122">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e9203-122">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
