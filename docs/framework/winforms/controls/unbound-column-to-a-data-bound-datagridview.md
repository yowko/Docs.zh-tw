---
title: "如何：將未繫結的資料行加入至已資料繫結的 Windows Form DataGridView 控制項"
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
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cd6a1494a98d912469f7e45c7751a0a9741ff17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="1c91d-102">如何：將未繫結的資料行加入至已資料繫結的 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="1c91d-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1c91d-103">您在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示的資料，通常來自於某種的資料來源，但您可能想要顯示不是來自資料來源之資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="1c91d-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="1c91d-104">這種資料行稱為未繫結資料行。</span><span class="sxs-lookup"><span data-stu-id="1c91d-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="1c91d-105">未繫結資料行可以有許多形式。</span><span class="sxs-lookup"><span data-stu-id="1c91d-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="1c91d-106">通常，它們用來提供資料列詳細資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="1c91d-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="1c91d-107">下列程式碼範例示範如何建立未繫結資料行的**詳細資料**實作主要/詳細資料案例時，按鈕以顯示子資料表相關父資料表中的特定資料列。</span><span class="sxs-lookup"><span data-stu-id="1c91d-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="1c91d-108">若要回應按下按鈕後，實作 <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> 事件處理常式，其顯示包含子資料表的表單。</span><span class="sxs-lookup"><span data-stu-id="1c91d-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="1c91d-109">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="1c91d-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="1c91d-110">另請參閱[如何： 加入和移除資料行中使用 Windows Form DataGridView 控制項設計工具](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1c91d-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c91d-111">範例</span><span class="sxs-lookup"><span data-stu-id="1c91d-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c91d-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1c91d-112">Compiling the Code</span></span>  
 <span data-ttu-id="1c91d-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1c91d-113">This example requires:</span></span>  
  
-   <span data-ttu-id="1c91d-114">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1c91d-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="1c91d-115"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1c91d-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c91d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c91d-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="1c91d-117">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="1c91d-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1c91d-118">Windows Forms DataGridView 控制項的資料顯示模式</span><span class="sxs-lookup"><span data-stu-id="1c91d-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
