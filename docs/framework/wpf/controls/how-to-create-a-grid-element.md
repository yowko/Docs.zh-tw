---
title: 如何：建立 Grid 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: 9fc70b8f15c4ecb4844c9c2ff4f7eeab94e7b906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551162"
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="b2379-102">如何：建立 Grid 項目</span><span class="sxs-lookup"><span data-stu-id="b2379-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="b2379-103">範例</span><span class="sxs-lookup"><span data-stu-id="b2379-103">Example</span></span>  
 <span data-ttu-id="b2379-104">下列範例示範如何建立和使用的執行個體<xref:System.Windows.Controls.Grid>使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2379-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="b2379-105">這個範例會使用三個<xref:System.Windows.Controls.ColumnDefinition>物件和三個<xref:System.Windows.Controls.RowDefinition>物件建立一個方格，其中擁有九個資料格，例如工作表。</span><span class="sxs-lookup"><span data-stu-id="b2379-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="b2379-106">每個資料格包含<xref:System.Windows.Controls.TextBlock>項目，表示資料及上方資料列包含<xref:System.Windows.Controls.TextBlock>與<xref:System.Windows.Controls.Grid.ColumnSpan%2A>套用的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2379-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="b2379-107">若要顯示的界限，每個資料格，<xref:System.Windows.Controls.Grid.ShowGridLines%2A>屬性已啟用。</span><span class="sxs-lookup"><span data-stu-id="b2379-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b2379-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2379-108">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="b2379-109">面板概觀</span><span class="sxs-lookup"><span data-stu-id="b2379-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
