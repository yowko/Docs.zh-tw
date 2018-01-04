---
title: "如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀"
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
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61b2a39943dfca412afa4b66265aabbf65b9ccf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ad6b9-102">如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀</span><span class="sxs-lookup"><span data-stu-id="ad6b9-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ad6b9-103">您可以自訂處理的任何資料格的外觀<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CellPainting>事件。</span><span class="sxs-lookup"><span data-stu-id="ad6b9-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="ad6b9-104">您可以擷取<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Drawing.Graphics>從<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A>屬性<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="ad6b9-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="ad6b9-105">與這個<xref:System.Drawing.Graphics>，您可能會影響整個外觀<xref:System.Windows.Forms.DataGridView>控制項，但是您通常會想要影響目前所繪製的儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="ad6b9-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="ad6b9-106"><xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A>屬性<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>可讓您限制您到目前所繪製的儲存格的繪製作業。</span><span class="sxs-lookup"><span data-stu-id="ad6b9-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="ad6b9-107">在下列程式碼範例中，您會繪製中的所有資料格`ContactName`資料行使用<xref:System.Windows.Forms.DataGridView>控制項的色彩配置。</span><span class="sxs-lookup"><span data-stu-id="ad6b9-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="ad6b9-108">每個資料格文字內容中繪製<xref:System.Drawing.Color.Crimson%2A>，而且在相同的色彩繪製內凹矩形<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.GridColor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ad6b9-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad6b9-109">範例</span><span class="sxs-lookup"><span data-stu-id="ad6b9-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ad6b9-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ad6b9-110">Compiling the Code</span></span>  
 <span data-ttu-id="ad6b9-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="ad6b9-111">This example requires:</span></span>  
  
-   <span data-ttu-id="ad6b9-112">A<xref:System.Windows.Forms.DataGridView>控制項，名為`dataGridView1`與`ContactName`例如 Northwind 範例資料庫中的 Customers 資料表中的一個資料行。</span><span class="sxs-lookup"><span data-stu-id="ad6b9-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="ad6b9-113">System、System.Windows.Forms 和 System.Drawing 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="ad6b9-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6b9-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="ad6b9-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellPainting>  
 [<span data-ttu-id="ad6b9-115">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="ad6b9-115">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
