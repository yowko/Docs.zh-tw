---
title: "如何：依據 Windows Form DataGridView 控制項儲存格的變更執行自訂動作"
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
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1b34881b86d9962603118b93c9dc5d866794397
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a><span data-ttu-id="18749-102">如何：依據 Windows Form DataGridView 控制項儲存格的變更執行自訂動作</span><span class="sxs-lookup"><span data-stu-id="18749-102">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="18749-103"><xref:System.Windows.Forms.DataGridView>控制項有一些可用來偵測的狀態變更事件<xref:System.Windows.Forms.DataGridView>資料格。</span><span class="sxs-lookup"><span data-stu-id="18749-103">The <xref:System.Windows.Forms.DataGridView> control has a number of events you can use to detect changes in the state of <xref:System.Windows.Forms.DataGridView> cells.</span></span> <span data-ttu-id="18749-104">兩個最常使用的是<xref:System.Windows.Forms.DataGridView.CellValueChanged>和<xref:System.Windows.Forms.DataGridView.CellStateChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="18749-104">Two of the most commonly used are the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a><span data-ttu-id="18749-105">若要偵測 DataGridView 儲存格的值中的變更</span><span class="sxs-lookup"><span data-stu-id="18749-105">To detect changes in the values of DataGridView cells</span></span>  
  
-   <span data-ttu-id="18749-106">寫入的處理常式<xref:System.Windows.Forms.DataGridView.CellValueChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="18749-106">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellValueChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a><span data-ttu-id="18749-107">在 DataGridView 儲存格的狀態偵測變更</span><span class="sxs-lookup"><span data-stu-id="18749-107">To detect changes in the states of DataGridView cells</span></span>  
  
-   <span data-ttu-id="18749-108">寫入的處理常式<xref:System.Windows.Forms.DataGridView.CellStateChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="18749-108">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellStateChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="18749-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="18749-109">Compiling the Code</span></span>  
 <span data-ttu-id="18749-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="18749-110">This example requires:</span></span>  
  
-   <span data-ttu-id="18749-111">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="18749-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span> <span data-ttu-id="18749-112">C# 中，事件處理常式必須連接至對應的事件。</span><span class="sxs-lookup"><span data-stu-id="18749-112">For C#, the event handlers must be connected to the corresponding events.</span></span>  
  
-   <span data-ttu-id="18749-113"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="18749-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18749-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="18749-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>  
 [<span data-ttu-id="18749-115">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="18749-115">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 [<span data-ttu-id="18749-116">逐步解說：驗證 Windows Forms DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="18749-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
