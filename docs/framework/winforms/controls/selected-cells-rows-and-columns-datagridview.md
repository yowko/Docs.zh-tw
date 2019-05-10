---
title: HOW TO：取得 Windows Forms DataGridView 控制項中已選取的儲存格、資料列和資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: c250fa52251cbd54d457c8228d4a1d8f23ce5923
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614650"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1a237-102">HOW TO：取得 Windows Forms DataGridView 控制項中已選取的儲存格、資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="1a237-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1a237-103">您可以取得所選儲存格、 資料列或從資料行<xref:System.Windows.Forms.DataGridView>控制項使用對應的屬性： <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>， <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>，和<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>。</span><span class="sxs-lookup"><span data-stu-id="1a237-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="1a237-104">在下列程序中，您會取得所選儲存格，並顯示其資料列和資料行索引中的<xref:System.Windows.Forms.MessageBox>。</span><span class="sxs-lookup"><span data-stu-id="1a237-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="1a237-105">若要取得在 DataGridView 控制項中選取的資料格</span><span class="sxs-lookup"><span data-stu-id="1a237-105">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="1a237-106">請使用 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1a237-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1a237-107">使用<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>方法，以避免僅顯示大量的資料格。</span><span class="sxs-lookup"><span data-stu-id="1a237-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="1a237-108">若要取得選取的資料列，DataGridView 控制項中</span><span class="sxs-lookup"><span data-stu-id="1a237-108">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="1a237-109">請使用 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1a237-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="1a237-110">若要讓使用者可以選取資料列，您必須設定<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>屬性，以<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>。</span><span class="sxs-lookup"><span data-stu-id="1a237-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="1a237-111">在 DataGridView 控制項中取得所選資料行</span><span class="sxs-lookup"><span data-stu-id="1a237-111">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="1a237-112">請使用 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1a237-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="1a237-113">若要讓使用者可以選取資料行，您必須設定<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>屬性，以<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>。</span><span class="sxs-lookup"><span data-stu-id="1a237-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1a237-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1a237-114">Compiling the Code</span></span>  
 <span data-ttu-id="1a237-115">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1a237-115">This example requires:</span></span>  
  
- <span data-ttu-id="1a237-116"><xref:System.Windows.Forms.Button> 名為的控制項`selectedCellsButton`， `selectedRowsButton`，並`selectedColumnsButton`，每個處理常式的<xref:System.Windows.Forms.Control.Click>附加事件。</span><span class="sxs-lookup"><span data-stu-id="1a237-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="1a237-117">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1a237-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="1a237-118"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Text?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1a237-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1a237-119">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="1a237-119">Robust Programming</span></span>  
 <span data-ttu-id="1a237-120">本主題中所描述的集合不會執行有效率地大量的資料格、 資料列或資料行中選取時。</span><span class="sxs-lookup"><span data-stu-id="1a237-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="1a237-121">如需大量的資料搭配使用這些集合的詳細資訊，請參閱[縮放 Windows Form DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1a237-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a237-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a237-122">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="1a237-123">選取範圍和剪貼簿與 Windows Forms DataGridView 控制項搭配使用</span><span class="sxs-lookup"><span data-stu-id="1a237-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
