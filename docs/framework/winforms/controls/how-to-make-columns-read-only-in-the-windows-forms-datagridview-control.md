---
title: "如何：使 Windows Form DataGridView 控制項中的資料行成為唯讀"
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
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a3b6a72a3dac2e7957f73ee466ded0282988923
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f14e2-102">如何：使 Windows Form DataGridView 控制項中的資料行成為唯讀</span><span class="sxs-lookup"><span data-stu-id="f14e2-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f14e2-103">並非所有資料都是可編輯的。</span><span class="sxs-lookup"><span data-stu-id="f14e2-103">Not all data is meant for editing.</span></span> <span data-ttu-id="f14e2-104">在 <xref:System.Windows.Forms.DataGridView> 控制項中，資料行 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> 屬性值會決定使用者是否能編輯該資料行中的儲存格。</span><span class="sxs-lookup"><span data-stu-id="f14e2-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="f14e2-105">如需如何使控制項為完全唯讀資訊，請參閱[如何： 防止資料列新增和刪除 Windows Form DataGridView 控制項中的](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)。</span><span class="sxs-lookup"><span data-stu-id="f14e2-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="f14e2-106">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="f14e2-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="f14e2-107">另請參閱[How to: 使用 Windows Form DataGridView 控制項設計工具中進行資料行唯讀](http://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="f14e2-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="f14e2-108">以程式設計方式將資料行設為唯讀</span><span class="sxs-lookup"><span data-stu-id="f14e2-108">To make a column read-only programmatically</span></span>  
  
-   <span data-ttu-id="f14e2-109">將 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f14e2-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f14e2-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f14e2-110">Compiling the Code</span></span>  
 <span data-ttu-id="f14e2-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f14e2-111">This example requires:</span></span>  
  
-   <span data-ttu-id="f14e2-112">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，包含名為 `CompanyName` 的資料行。</span><span class="sxs-lookup"><span data-stu-id="f14e2-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
-   <span data-ttu-id="f14e2-113"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="f14e2-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f14e2-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="f14e2-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f14e2-115">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="f14e2-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="f14e2-116">操作說明：防止在 Windows Forms DataGridView 控制項中新增和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="f14e2-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
