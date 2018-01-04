---
title: "如何：變更 Windows Form DataGridView 控制項資料行的順序"
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
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04a2048025bbd582d812d0748cc2d1521f44f140
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="963dc-102">如何：變更 Windows Form DataGridView 控制項資料行的順序</span><span class="sxs-lookup"><span data-stu-id="963dc-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="963dc-103">當您使用 <xref:System.Windows.Forms.DataGridView> 顯示來自資料來源的資料時，資料來源結構描述中的資料行有時不會以您想要的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="963dc-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="963dc-104">您可以使用 <xref:System.Windows.Forms.DataGridViewColumn> 類別的 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> 屬性來變更資料行的顯示順序。</span><span class="sxs-lookup"><span data-stu-id="963dc-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="963dc-105">下列程式碼範例會重新調整繫結至 Northwind 範例資料庫中的 Customers 資料表時，所自動產生之一些資料行的位置。</span><span class="sxs-lookup"><span data-stu-id="963dc-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="963dc-106">如需有關如何將繫結<xref:System.Windows.Forms.DataGridView>控制權傳輸至資料庫資料表，請參閱[How to： 將資料繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="963dc-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="963dc-107">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="963dc-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="963dc-108">另請參閱[如何： 變更 Windows Form DataGridView 控制項使用設計工具中的資料行順序](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="963dc-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="963dc-109">範例</span><span class="sxs-lookup"><span data-stu-id="963dc-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="963dc-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="963dc-110">Compiling the Code</span></span>  
 <span data-ttu-id="963dc-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="963dc-111">This example requires:</span></span>  
  
-   <span data-ttu-id="963dc-112">名為 `customersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控制項，這個控制項會繫結至具有指定資料行名稱的資料表，例如 Northwind 範例資料庫中的 `Customers` 資料表。</span><span class="sxs-lookup"><span data-stu-id="963dc-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="963dc-113"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、<xref:System.Data?displayProperty=nameWithType> 和 <xref:System.Xml?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="963dc-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963dc-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="963dc-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="963dc-115">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="963dc-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="963dc-116">操作說明：將資料繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="963dc-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
