---
title: HOW TO：在 Windows Forms ListView 控制項中啟用並排顯示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 14eb21fa0285275e510b865c5cee7d1fc82fd0fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326992"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="0618c-102">HOW TO：在 Windows Forms ListView 控制項中啟用並排顯示</span><span class="sxs-lookup"><span data-stu-id="0618c-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="0618c-103">使用的 <xref:System.Windows.Forms.ListView> 控制項的並排顯示檢視功能，您可以提供圖形和文字資訊之間的視覺化平衡。</span><span class="sxs-lookup"><span data-stu-id="0618c-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="0618c-104">並排顯示檢視中針對項目顯示的文字資訊與詳細資料檢視所定義的資料行資訊相同。</span><span class="sxs-lookup"><span data-stu-id="0618c-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="0618c-105">並排顯示檢視與 <xref:System.Windows.Forms.ListView> 控制項中的群組或插入標記功能相配合。</span><span class="sxs-lookup"><span data-stu-id="0618c-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="0618c-106">並排顯示檢視會使用 32 x 32 像素圖示和數行的文字，如下列影像所示。</span><span class="sxs-lookup"><span data-stu-id="0618c-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="0618c-107">![ListView 控制項中並排](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "圖格的圖示和文字")</span><span class="sxs-lookup"><span data-stu-id="0618c-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  
 
 <span data-ttu-id="0618c-108">若要啟用並排顯示檢視，請將 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 <xref:System.Windows.Forms.View.Tile>。</span><span class="sxs-lookup"><span data-stu-id="0618c-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="0618c-109">您可以藉由設定 <xref:System.Windows.Forms.ListView.TileSize%2A> 屬性調整並排顯示的大小，並藉由調整 <xref:System.Windows.Forms.ListView.Columns%2A> 集合來調整並排顯示中顯示的文字行數。</span><span class="sxs-lookup"><span data-stu-id="0618c-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0618c-110">並排顯示檢視是僅在您的應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法時適用於 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上。</span><span class="sxs-lookup"><span data-stu-id="0618c-110">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0618c-111">在舊版作業系統中，任何與並排顯示檢視相關的程式碼都無效，而且 <xref:System.Windows.Forms.ListView> 控制項會顯示在大圖示檢視中。</span><span class="sxs-lookup"><span data-stu-id="0618c-111">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="0618c-112">如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0618c-112">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="0618c-113">以程式設計方式設定並排顯示檢視</span><span class="sxs-lookup"><span data-stu-id="0618c-113">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="0618c-114">使用 <xref:System.Windows.Forms.ListView> 控制項的 <xref:System.Windows.Forms.View> 的列舉。</span><span class="sxs-lookup"><span data-stu-id="0618c-114">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="0618c-115">範例</span><span class="sxs-lookup"><span data-stu-id="0618c-115">Example</span></span>  
 <span data-ttu-id="0618c-116">下列完整的程式碼範例示範並排顯示檢視，並修改為可顯示三行文字。</span><span class="sxs-lookup"><span data-stu-id="0618c-116">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="0618c-117">已經調整並排顯示大小以避免自動換行。</span><span class="sxs-lookup"><span data-stu-id="0618c-117">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0618c-118">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0618c-118">Compiling the Code</span></span>  
 <span data-ttu-id="0618c-119">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="0618c-119">This example requires:</span></span>  
  
-   <span data-ttu-id="0618c-120">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="0618c-120">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="0618c-121">名為 book.ico 的圖示檔，位於與可執行檔相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="0618c-121">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="0618c-122">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="0618c-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0618c-123">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0618c-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0618c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0618c-124">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="0618c-125">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="0618c-125">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="0618c-126">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="0618c-126">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
