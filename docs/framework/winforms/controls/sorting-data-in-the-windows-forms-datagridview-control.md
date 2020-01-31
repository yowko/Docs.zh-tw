---
title: 排序 DataGridView 控制項中的資料
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1fcd5a5f5c6d690c573c4c2c5fa7c32aa0292441
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742941"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="91dee-102">排序 Windows Forms DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="91dee-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="91dee-103">根據預設，使用者可以按一下文字方塊資料行的標頭來排序 <xref:System.Windows.Forms.DataGridView> 控制項中的資料（或在文字方塊儲存格著重于 .NET Framework 4.7.2 和更新版本時按 F3）。</span><span class="sxs-lookup"><span data-stu-id="91dee-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="91dee-104">您可以修改特定資料行的 <xref:System.Windows.Forms.DataGridViewColumn.SortMode> 屬性，以允許使用者在執行這項操作時，依其他資料行類型排序。</span><span class="sxs-lookup"><span data-stu-id="91dee-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="91dee-105">您也可以用程式設計方式，依據任何資料行或多個資料行來排序資料。</span><span class="sxs-lookup"><span data-stu-id="91dee-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="91dee-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="91dee-106">In this section</span></span>

[<span data-ttu-id="91dee-107">Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="91dee-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="91dee-108">描述在控制項中排序資料的選項。</span><span class="sxs-lookup"><span data-stu-id="91dee-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="91dee-109">如何：設定 Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="91dee-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="91dee-110">描述如何讓使用者依預設不可排序的資料行排序。</span><span class="sxs-lookup"><span data-stu-id="91dee-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="91dee-111">操作說明：自訂 Windows Forms DataGridView 控制項中的排序</span><span class="sxs-lookup"><span data-stu-id="91dee-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="91dee-112">描述如何以程式設計方式排序資料，以及如何使用 <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> 事件或藉由執行 <xref:System.Collections.IComparer> 介面來自訂排序。</span><span class="sxs-lookup"><span data-stu-id="91dee-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="91dee-113">參考資料</span><span class="sxs-lookup"><span data-stu-id="91dee-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="91dee-114">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="91dee-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="91dee-115">提供 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的參考檔。</span><span class="sxs-lookup"><span data-stu-id="91dee-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="91dee-116">提供 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 屬性的參考檔。</span><span class="sxs-lookup"><span data-stu-id="91dee-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="91dee-117">提供 <xref:System.Windows.Forms.DataGridViewColumnSortMode> 列舉的參考檔。</span><span class="sxs-lookup"><span data-stu-id="91dee-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="91dee-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="91dee-118">See also</span></span>

- [<span data-ttu-id="91dee-119">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="91dee-119">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="91dee-120">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="91dee-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
