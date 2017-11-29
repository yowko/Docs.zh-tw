---
title: "在 Windows Form DataGridView 控制項中排序資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b4027f3ae604f2a3ff4996855fa6dd34d4de8ea2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b2e62-102">在 Windows Form DataGridView 控制項中排序資料</span><span class="sxs-lookup"><span data-stu-id="b2e62-102">Sorting Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b2e62-103">根據預設，使用者可以排序中的資料`DataGridView`依序按一下 [文字] 方塊中的資料行的標頭的控制項。</span><span class="sxs-lookup"><span data-stu-id="b2e62-103">By default, users can sort the data in a `DataGridView` control by clicking the header of a text box column.</span></span> <span data-ttu-id="b2e62-104">您可以修改`SortMode`允許使用者排序其他資料行型別時要執行這項操作的特定資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e62-104">You can modify the `SortMode` property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="b2e62-105">您也以程式設計的方式排序資料，依任何資料行，或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="b2e62-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2e62-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="b2e62-106">In This Section</span></span>  
 [<span data-ttu-id="b2e62-107">Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="b2e62-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b2e62-108">描述在控制項中排序資料的選項。</span><span class="sxs-lookup"><span data-stu-id="b2e62-108">Describes the options for sorting data in the control.</span></span>  
  
 [<span data-ttu-id="b2e62-109">操作說明：設定 Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="b2e62-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 <span data-ttu-id="b2e62-110">描述如何讓使用者不是預設可排序的資料欄來排序。</span><span class="sxs-lookup"><span data-stu-id="b2e62-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>  
  
 [<span data-ttu-id="b2e62-111">操作說明：自訂 Windows Forms DataGridView 控制項中的排序</span><span class="sxs-lookup"><span data-stu-id="b2e62-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b2e62-112">描述如何以程式設計的方式排序資料，以及如何自訂排序使用<xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType>事件或藉由實作<xref:System.Collections.IComparer>介面。</span><span class="sxs-lookup"><span data-stu-id="b2e62-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b2e62-113">參考資料</span><span class="sxs-lookup"><span data-stu-id="b2e62-113">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b2e62-114">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="b2e62-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <span data-ttu-id="b2e62-115">提供參考文件<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b2e62-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="b2e62-116">提供參考文件<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e62-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumnSortMode>  
 <span data-ttu-id="b2e62-117">提供參考文件<xref:System.Windows.Forms.DataGridViewColumnSortMode>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="b2e62-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e62-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2e62-118">See Also</span></span>  
 [<span data-ttu-id="b2e62-119">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="b2e62-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="b2e62-120">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="b2e62-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
