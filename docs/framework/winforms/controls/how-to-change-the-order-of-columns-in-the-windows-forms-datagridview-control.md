---
title: HOW TO：變更 Windows Form DataGridView 控制項中的資料行的順序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 0e49107193d546e590582ca6bab798149d7064a7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711261"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f11a5-102">HOW TO：變更 Windows Form DataGridView 控制項中的資料行的順序</span><span class="sxs-lookup"><span data-stu-id="f11a5-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f11a5-103">當您使用 <xref:System.Windows.Forms.DataGridView> 顯示來自資料來源的資料時，資料來源結構描述中的資料行有時不會以您想要的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="f11a5-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="f11a5-104">您可以使用 <xref:System.Windows.Forms.DataGridViewColumn> 類別的 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> 屬性來變更資料行的顯示順序。</span><span class="sxs-lookup"><span data-stu-id="f11a5-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="f11a5-105">下列程式碼範例會重新調整繫結至 Northwind 範例資料庫中的 Customers 資料表時，所自動產生之一些資料行的位置。</span><span class="sxs-lookup"><span data-stu-id="f11a5-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="f11a5-106">如需有關如何將繫結<xref:System.Windows.Forms.DataGridView>控制資料庫資料表，請參閱[How to:資料繫結至 Windows Form DataGridView 控制項](how-to-bind-data-to-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="f11a5-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="f11a5-107">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="f11a5-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="f11a5-108">另請參閱[How to:變更 Windows Form DataGridView 控制項中使用設計工具中的資料行順序](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="f11a5-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f11a5-109">範例</span><span class="sxs-lookup"><span data-stu-id="f11a5-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f11a5-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f11a5-110">Compiling the Code</span></span>  
 <span data-ttu-id="f11a5-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f11a5-111">This example requires:</span></span>  
  
-   <span data-ttu-id="f11a5-112">名為 `customersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控制項，這個控制項會繫結至具有指定資料行名稱的資料表，例如 Northwind 範例資料庫中的 `Customers` 資料表。</span><span class="sxs-lookup"><span data-stu-id="f11a5-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="f11a5-113">
  <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、<xref:System.Data?displayProperty=nameWithType> 和 <xref:System.Xml?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="f11a5-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f11a5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f11a5-114">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f11a5-115">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="f11a5-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f11a5-116">如何：將資料繫結至 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="f11a5-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
