---
title: 如何：使用設計工具在 Windows Form ListView 控制項中啟用 Tile 檢視
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 836d82930c7ff41e7a4ae64a577baa5f1ba780c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528914"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="71c7f-102">如何：使用設計工具在 Windows Form ListView 控制項中啟用 Tile 檢視</span><span class="sxs-lookup"><span data-stu-id="71c7f-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="71c7f-103">並排顯示檢視功能<xref:System.Windows.Forms.ListView>控制項可讓您提供圖形和文字資訊之間的視覺化平衡。</span><span class="sxs-lookup"><span data-stu-id="71c7f-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="71c7f-104">並排顯示檢視中針對項目顯示的文字資訊與詳細資料檢視所定義的資料行資訊相同。</span><span class="sxs-lookup"><span data-stu-id="71c7f-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="71c7f-105">並排顯示檢視函式結合的群組或插入標記功能<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="71c7f-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="71c7f-106">並排顯示檢視會使用 32 x 32 圖示和數行文字，如下列影像所示。</span><span class="sxs-lookup"><span data-stu-id="71c7f-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>  
  
 <span data-ttu-id="71c7f-107">![ListView 控制項中並排顯示](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="71c7f-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
  
 <span data-ttu-id="71c7f-108">並排顯示檢視屬性和方法讓您指定哪些資料行欄位來顯示每個項目，以及共同控制的大小和並排顯示視窗中的所有項目的外觀。</span><span class="sxs-lookup"><span data-stu-id="71c7f-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="71c7f-109">為了清楚起見，在磚中的第一行一律是文字的項目的名稱;無法變更。</span><span class="sxs-lookup"><span data-stu-id="71c7f-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>  
  
 <span data-ttu-id="71c7f-110">下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="71c7f-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="71c7f-111">設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="71c7f-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71c7f-112">並排顯示檢視是僅在您的應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法時適用於 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上。</span><span class="sxs-lookup"><span data-stu-id="71c7f-112">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="71c7f-113">在舊版作業系統中，任何與並排顯示檢視相關的程式碼都無效，而且 <xref:System.Windows.Forms.ListView> 控制項會顯示在大圖示檢視中。</span><span class="sxs-lookup"><span data-stu-id="71c7f-113">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="71c7f-114">如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="71c7f-114">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="71c7f-115">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="71c7f-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="71c7f-116">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="71c7f-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="71c7f-117">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="71c7f-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="71c7f-118">在設計工具中設定並排顯示檢視</span><span class="sxs-lookup"><span data-stu-id="71c7f-118">To set tile view in the designer</span></span>  
  
1.  <span data-ttu-id="71c7f-119">選取<xref:System.Windows.Forms.ListView>控制項在表單上的。</span><span class="sxs-lookup"><span data-stu-id="71c7f-119">Select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>  
  
2.  <span data-ttu-id="71c7f-120">在**屬性**視窗中，選取<xref:System.Windows.Forms.ListView.View%2A>屬性，然後選擇 **磚**。</span><span class="sxs-lookup"><span data-stu-id="71c7f-120">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c7f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71c7f-121">See Also</span></span>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [<span data-ttu-id="71c7f-122">Windows XP 功能和 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="71c7f-122">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="71c7f-123">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="71c7f-123">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
