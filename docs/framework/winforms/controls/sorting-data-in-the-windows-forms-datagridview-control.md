---
title: 在 Windows Form DataGridView 控制項中排序資料
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 606ffc7bd6136b775adaaaa79cf5042cf1e2dd70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012143"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="23591-102">在 Windows Form DataGridView 控制項中排序資料</span><span class="sxs-lookup"><span data-stu-id="23591-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="23591-103">根據預設，使用者可以排序資料<xref:System.Windows.Forms.DataGridView>控制項依序按一下 文字 方塊中的資料行的標頭 （或按 F3 時文字 方塊中資料格著重於.NET Framework 4.7.2 和更新版本）。</span><span class="sxs-lookup"><span data-stu-id="23591-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="23591-104">您可以修改<xref:System.Windows.Forms.DataGridViewColumn.SortMode>特定的資料行，讓使用者得有意義，若要這樣做時，由其他資料行類型排序的屬性。</span><span class="sxs-lookup"><span data-stu-id="23591-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="23591-105">您也以程式設計的方式排序資料，依任何資料行，或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="23591-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="23591-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="23591-106">In this section</span></span>

[<span data-ttu-id="23591-107">Windows Forms DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="23591-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="23591-108">描述在控制項中排序資料的選項。</span><span class="sxs-lookup"><span data-stu-id="23591-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="23591-109">如何：設定 Windows Form DataGridView 控制項中的資料行排序模式</span><span class="sxs-lookup"><span data-stu-id="23591-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="23591-110">描述如何讓使用者不是預設可排序的資料欄來排序。</span><span class="sxs-lookup"><span data-stu-id="23591-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="23591-111">如何：自訂 Windows Form DataGridView 控制項中排序</span><span class="sxs-lookup"><span data-stu-id="23591-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="23591-112">說明如何以程式設計的方式排序資料以及如何自訂所使用的排序<xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType>事件或實作<xref:System.Collections.IComparer>介面。</span><span class="sxs-lookup"><span data-stu-id="23591-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="23591-113">參考資料</span><span class="sxs-lookup"><span data-stu-id="23591-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="23591-114">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="23591-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="23591-115">提供參考文件<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="23591-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="23591-116">提供參考文件<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="23591-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="23591-117">提供參考文件<xref:System.Windows.Forms.DataGridViewColumnSortMode>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="23591-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="23591-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23591-118">See also</span></span>

- [<span data-ttu-id="23591-119">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="23591-119">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="23591-120">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="23591-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
