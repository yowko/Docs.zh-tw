---
title: 在 Windows Form DataGridView 控制項中排序資料
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1cbfb4a19e9bb0db5cbb595a91a254a3a8e3f309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536009"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="36447-102">在 Windows Form DataGridView 控制項中排序資料</span><span class="sxs-lookup"><span data-stu-id="36447-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="36447-103">根據預設，使用者可以排序中的資料<xref:System.Windows.Forms.DataGridView>控制項，依序按一下 文字 方塊中的資料行的標頭 （或按 F3 時文字 方塊中的資料格會著重於.NET Framework 4.7.2 及更新版本）。</span><span class="sxs-lookup"><span data-stu-id="36447-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="36447-104">您可以修改<xref:System.Windows.Forms.DataGridViewColumn.SortMode>允許使用者排序其他資料行型別時要執行這項操作的特定資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="36447-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="36447-105">您也以程式設計的方式排序資料，依任何資料行，或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="36447-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="36447-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="36447-106">In this section</span></span>

[<span data-ttu-id="36447-107">Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="36447-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="36447-108">描述在控制項中排序資料的選項。</span><span class="sxs-lookup"><span data-stu-id="36447-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="36447-109">操作說明：設定 Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="36447-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="36447-110">描述如何讓使用者不是預設可排序的資料欄來排序。</span><span class="sxs-lookup"><span data-stu-id="36447-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="36447-111">操作說明：自訂 Windows Forms DataGridView 控制項中的排序</span><span class="sxs-lookup"><span data-stu-id="36447-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="36447-112">描述如何以程式設計的方式排序資料，以及如何自訂排序使用<xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType>事件或藉由實作<xref:System.Collections.IComparer>介面。</span><span class="sxs-lookup"><span data-stu-id="36447-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="36447-113">參考資料</span><span class="sxs-lookup"><span data-stu-id="36447-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="36447-114">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="36447-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="36447-115">提供參考文件<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="36447-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="36447-116">提供參考文件<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="36447-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="36447-117">提供參考文件<xref:System.Windows.Forms.DataGridViewColumnSortMode>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="36447-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="36447-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36447-118">See also</span></span>

[<span data-ttu-id="36447-119">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="36447-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
[<span data-ttu-id="36447-120">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="36447-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  