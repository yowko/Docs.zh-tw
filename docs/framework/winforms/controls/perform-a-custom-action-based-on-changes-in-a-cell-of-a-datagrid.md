---
title: 根據 DataGridView 控制項儲存格的變更執行自訂動作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: a809134b0a79bc9685c5b84acce58b4c61b5c526
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744290"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a><span data-ttu-id="62069-102">如何：依據 Windows Form DataGridView 控制項儲存格的變更執行自訂動作</span><span class="sxs-lookup"><span data-stu-id="62069-102">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="62069-103"><xref:System.Windows.Forms.DataGridView> 控制項有一些事件，可供您用來偵測 <xref:System.Windows.Forms.DataGridView> 儲存格狀態中的變更。</span><span class="sxs-lookup"><span data-stu-id="62069-103">The <xref:System.Windows.Forms.DataGridView> control has a number of events you can use to detect changes in the state of <xref:System.Windows.Forms.DataGridView> cells.</span></span> <span data-ttu-id="62069-104">其中兩個最常使用的是 <xref:System.Windows.Forms.DataGridView.CellValueChanged> 和 <xref:System.Windows.Forms.DataGridView.CellStateChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="62069-104">Two of the most commonly used are the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a><span data-ttu-id="62069-105">若要偵測 DataGridView 資料格值的變更</span><span class="sxs-lookup"><span data-stu-id="62069-105">To detect changes in the values of DataGridView cells</span></span>  
  
- <span data-ttu-id="62069-106">撰寫 <xref:System.Windows.Forms.DataGridView.CellValueChanged> 事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="62069-106">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellValueChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a><span data-ttu-id="62069-107">偵測 DataGridView 儲存格狀態中的變更</span><span class="sxs-lookup"><span data-stu-id="62069-107">To detect changes in the states of DataGridView cells</span></span>  
  
- <span data-ttu-id="62069-108">撰寫 <xref:System.Windows.Forms.DataGridView.CellStateChanged> 事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="62069-108">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellStateChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62069-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="62069-109">Compiling the Code</span></span>  
 <span data-ttu-id="62069-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="62069-110">This example requires:</span></span>  
  
- <span data-ttu-id="62069-111">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="62069-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span> <span data-ttu-id="62069-112">若C#為，事件處理常式必須連接到對應的事件。</span><span class="sxs-lookup"><span data-stu-id="62069-112">For C#, the event handlers must be connected to the corresponding events.</span></span>  
  
- <span data-ttu-id="62069-113"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="62069-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62069-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="62069-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [<span data-ttu-id="62069-115">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="62069-115">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [<span data-ttu-id="62069-116">逐步解說：驗證 Windows Forms DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="62069-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
