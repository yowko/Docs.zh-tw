---
title: 隱藏 DataGridView 控制項中的資料行
description: 瞭解如何藉由將 DataGridViewColumn 屬性設定為 false，以程式設計方式隱藏在 Windows Forms DataGridView 控制項中的資料行。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 27e9f331151acd68d76233bc7dbb09c2d870afde
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618047"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="311cc-103">如何：隱藏 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="311cc-103">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="311cc-104">有時候您會想要只顯示 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項中某些可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="311cc-104">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="311cc-105">例如，您可能會想要對具有管理認證的使用者顯示員工薪資資料行，而對其他使用者隱藏該資料行。</span><span class="sxs-lookup"><span data-stu-id="311cc-105">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="311cc-106">或者，您可能會想要將控制項繫結至包含許多資料行的資料來源，但您只想要顯示其中部分資料行。</span><span class="sxs-lookup"><span data-stu-id="311cc-106">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="311cc-107">在此情況下，您通常會移除不想顯示的資料行，而不是加以隱藏。</span><span class="sxs-lookup"><span data-stu-id="311cc-107">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="311cc-108">在 <xref:System.Windows.Forms.DataGridView> 控制項中，資料行的 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> 屬性值會決定是否要顯示該資料行。</span><span class="sxs-lookup"><span data-stu-id="311cc-108">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="311cc-109">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="311cc-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="311cc-110">另請參閱[如何：使用設計工具隱藏 Windows Forms DataGridView 控制項中的資料行](hide-columns-in-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="311cc-110">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](hide-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="311cc-111">以程式設計方式隱藏資料行</span><span class="sxs-lookup"><span data-stu-id="311cc-111">To hide a column programmatically</span></span>  
  
- <span data-ttu-id="311cc-112">將 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> 屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="311cc-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="311cc-113">若要隱藏在資料繫結期間自動產生的 `CustomerID` 資料行，請將下列程式碼範例放在 <xref:System.Windows.Forms.DataGridView.DataBindingComplete> 事件處理常式中。</span><span class="sxs-lookup"><span data-stu-id="311cc-113">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="311cc-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="311cc-114">Compiling the Code</span></span>  
 <span data-ttu-id="311cc-115">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="311cc-115">This example requires:</span></span>  
  
- <span data-ttu-id="311cc-116">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項 ，包含名為 `CustomerID` 的資料行。</span><span class="sxs-lookup"><span data-stu-id="311cc-116">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
- <span data-ttu-id="311cc-117"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="311cc-117">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311cc-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="311cc-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="311cc-119">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="311cc-119">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="311cc-120">如何：移除 Windows Form DataGridView 控制項中自動產生的資料行</span><span class="sxs-lookup"><span data-stu-id="311cc-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
- [<span data-ttu-id="311cc-121">如何：變更 Windows Form DataGridView 控制項資料行的順序</span><span class="sxs-lookup"><span data-stu-id="311cc-121">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
