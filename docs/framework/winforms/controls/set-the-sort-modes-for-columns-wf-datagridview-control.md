---
title: "如何：設定 Windows Form DataGridView 控制項中的資料行排序模式"
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
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a1c5b0447895b0ca5c67fff054d88da0d0107c5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1392f-102">如何：設定 Windows Form DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="1392f-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1392f-103">在<xref:System.Windows.Forms.DataGridView>控制項中，文字方塊資料行使用自動排序依預設，而其他資料行類型不會自動排序。</span><span class="sxs-lookup"><span data-stu-id="1392f-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="1392f-104">有時候您會想要覆寫這些預設值。</span><span class="sxs-lookup"><span data-stu-id="1392f-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="1392f-105">例如，您可以顯示影像取代文字、 數字或列舉型別資料格的值。</span><span class="sxs-lookup"><span data-stu-id="1392f-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="1392f-106">雖然無法排序映像，可以進行排序它們代表的基礎值。</span><span class="sxs-lookup"><span data-stu-id="1392f-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="1392f-107">在<xref:System.Windows.Forms.DataGridView>控制項，<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>資料行的屬性值會決定其排序行為。</span><span class="sxs-lookup"><span data-stu-id="1392f-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="1392f-108">下列程序示範`Priority`資料行從[如何： 在 Windows Form DataGridView 控制項中自訂格式化資料](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1392f-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="1392f-109">這個資料行的影像資料行，但不是預設排序。</span><span class="sxs-lookup"><span data-stu-id="1392f-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="1392f-110">它包含實際的資料格的值字串，不過，因此會自動排序。</span><span class="sxs-lookup"><span data-stu-id="1392f-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="1392f-111">若要設定資料行的排序模式</span><span class="sxs-lookup"><span data-stu-id="1392f-111">To set the sort mode for a column</span></span>  
  
-   <span data-ttu-id="1392f-112">設定 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1392f-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1392f-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1392f-113">Compiling the Code</span></span>  
 <span data-ttu-id="1392f-114">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1392f-114">This example requires:</span></span>  
  
-   <span data-ttu-id="1392f-115">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項 ，包含名為 `Priority` 的資料行。</span><span class="sxs-lookup"><span data-stu-id="1392f-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
-   <span data-ttu-id="1392f-116"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1392f-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1392f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1392f-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1392f-118">在 Windows Forms DataGridView 控制項中排序資料</span><span class="sxs-lookup"><span data-stu-id="1392f-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1392f-119">Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="1392f-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1392f-120">操作說明：自訂 Windows Forms DataGridView 控制項中的排序</span><span class="sxs-lookup"><span data-stu-id="1392f-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
