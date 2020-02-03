---
title: 設定 DataGridView 控制項中的資料行排序模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 45ee1e7d82f826cddbd3492fed0f63e7a9c2cf1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742992"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="09951-102">如何：設定 Windows Form DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="09951-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="09951-103">在 <xref:System.Windows.Forms.DataGridView> 控制項中，文字方塊資料行預設會使用自動排序，而其他資料行類型則不會自動排序。</span><span class="sxs-lookup"><span data-stu-id="09951-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="09951-104">有時候您會想要覆寫這些預設值。</span><span class="sxs-lookup"><span data-stu-id="09951-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="09951-105">例如，您可以顯示影像來取代文字、數位或列舉資料格值。</span><span class="sxs-lookup"><span data-stu-id="09951-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="09951-106">雖然無法排序影像，但它們所代表的基礎值可以進行排序。</span><span class="sxs-lookup"><span data-stu-id="09951-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="09951-107">在 <xref:System.Windows.Forms.DataGridView> 控制項中，資料行的 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 屬性值會決定其排序行為。</span><span class="sxs-lookup"><span data-stu-id="09951-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="09951-108">下列程式顯示[如何：在 Windows Forms DataGridView 控制項中自訂資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)的 `Priority` 欄。</span><span class="sxs-lookup"><span data-stu-id="09951-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="09951-109">此資料行是影像資料行，預設為不可排序。</span><span class="sxs-lookup"><span data-stu-id="09951-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="09951-110">不過，它包含實際的資料格值，這些都是字串，所以可以自動排序。</span><span class="sxs-lookup"><span data-stu-id="09951-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="09951-111">若要設定資料行的排序模式</span><span class="sxs-lookup"><span data-stu-id="09951-111">To set the sort mode for a column</span></span>  
  
- <span data-ttu-id="09951-112">設定 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="09951-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09951-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="09951-113">Compiling the Code</span></span>  
 <span data-ttu-id="09951-114">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="09951-114">This example requires:</span></span>  
  
- <span data-ttu-id="09951-115">名為 <xref:System.Windows.Forms.DataGridView> 的 `dataGridView1` 控制項 ，包含名為 `Priority` 的資料行。</span><span class="sxs-lookup"><span data-stu-id="09951-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
- <span data-ttu-id="09951-116"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="09951-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09951-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09951-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="09951-118">在 Windows Forms DataGridView 控制項中排序資料</span><span class="sxs-lookup"><span data-stu-id="09951-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="09951-119">Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="09951-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="09951-120">操作說明：自訂 Windows Forms DataGridView 控制項中的排序</span><span class="sxs-lookup"><span data-stu-id="09951-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
