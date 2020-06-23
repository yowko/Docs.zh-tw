---
title: 取得 DataGridView 控制項中選取的儲存格、資料列和資料行
description: 瞭解如何使用對應的屬性，從 DataGridView 控制項取得選取的儲存格、資料列或資料行。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 32ddae34104d23b8e5fbc0cce7da79f33fcce1d2
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904165"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="056ab-103">如何：取得 Windows Form DataGridView 控制項中選取的儲存格、資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="056ab-103">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="056ab-104">您可以使用對應的屬性，從控制項取得選取的儲存格、資料列或資料行 <xref:System.Windows.Forms.DataGridView> ： <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 、 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 和 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 。</span><span class="sxs-lookup"><span data-stu-id="056ab-104">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="056ab-105">在下列程式中，您會取得選取的儲存格，並在中顯示其資料列和資料行索引 <xref:System.Windows.Forms.MessageBox> 。</span><span class="sxs-lookup"><span data-stu-id="056ab-105">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="056ab-106">若要取得 DataGridView 控制項中選取的儲存格</span><span class="sxs-lookup"><span data-stu-id="056ab-106">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="056ab-107">請使用 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="056ab-107">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="056ab-108">使用 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> 方法，以避免顯示可能大量的資料格。</span><span class="sxs-lookup"><span data-stu-id="056ab-108">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="056ab-109">若要取得 DataGridView 控制項中選取的資料列</span><span class="sxs-lookup"><span data-stu-id="056ab-109">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="056ab-110">請使用 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="056ab-110">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="056ab-111">若要讓使用者選取資料列，您必須將 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> 。</span><span class="sxs-lookup"><span data-stu-id="056ab-111">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="056ab-112">若要取得 DataGridView 控制項中選取的資料行</span><span class="sxs-lookup"><span data-stu-id="056ab-112">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="056ab-113">請使用 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="056ab-113">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="056ab-114">若要讓使用者能夠選取資料行，您必須將 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect> 。</span><span class="sxs-lookup"><span data-stu-id="056ab-114">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="056ab-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="056ab-115">Compiling the Code</span></span>  
 <span data-ttu-id="056ab-116">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="056ab-116">This example requires:</span></span>  
  
- <span data-ttu-id="056ab-117"><xref:System.Windows.Forms.Button>名為 `selectedCellsButton` 、 `selectedRowsButton` 和 `selectedColumnsButton` 的控制項，每個都有 <xref:System.Windows.Forms.Control.Click> 附加事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="056ab-117"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="056ab-118">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="056ab-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="056ab-119"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Text?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="056ab-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="056ab-120">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="056ab-120">Robust Programming</span></span>  
 <span data-ttu-id="056ab-121">選取大量的資料格、資料列或資料行時，本主題中所述的集合不會有效率地執行。</span><span class="sxs-lookup"><span data-stu-id="056ab-121">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="056ab-122">如需有關使用這些具有大量資料之集合的詳細資訊，請參閱[縮放 Windows Forms DataGridView 控制項的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="056ab-122">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="056ab-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="056ab-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="056ab-124">選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用</span><span class="sxs-lookup"><span data-stu-id="056ab-124">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
