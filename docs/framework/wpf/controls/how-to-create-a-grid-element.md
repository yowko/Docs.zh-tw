---
title: HOW TO：建立 Grid 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: ebb9369da73bd595338e5b6ef42bda639bde6ed4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134533"
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="db23f-102">HOW TO：建立 Grid 元素</span><span class="sxs-lookup"><span data-stu-id="db23f-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="db23f-103">範例</span><span class="sxs-lookup"><span data-stu-id="db23f-103">Example</span></span>  
 <span data-ttu-id="db23f-104">下列範例示範如何建立和使用的執行個體<xref:System.Windows.Controls.Grid>使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或程式碼。</span><span class="sxs-lookup"><span data-stu-id="db23f-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="db23f-105">這個範例會使用三個<xref:System.Windows.Controls.ColumnDefinition>物件和三個<xref:System.Windows.Controls.RowDefinition>物件來建立一個方格，其中擁有九個資料格，例如工作表。</span><span class="sxs-lookup"><span data-stu-id="db23f-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="db23f-106">每個資料格都包含<xref:System.Windows.Controls.TextBlock>項目，表示資料及上方資料列包含<xref:System.Windows.Controls.TextBlock>使用<xref:System.Windows.Controls.Grid.ColumnSpan%2A>套用的屬性。</span><span class="sxs-lookup"><span data-stu-id="db23f-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="db23f-107">若要顯示的界限，每個資料格，<xref:System.Windows.Controls.Grid.ShowGridLines%2A>屬性處於啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="db23f-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](~/samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](~/samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  <span data-ttu-id="db23f-108">兩種方法會產生看起來相同，類似下面這個使用者介面。</span><span class="sxs-lookup"><span data-stu-id="db23f-108">Either approach will generate a user interface that looks much the same, like the one below.</span></span>

  ![螢幕擷取畫面說明包含分成三個資料行的方格的 WPF 使用者介面。](././media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a><span data-ttu-id="db23f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db23f-112">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="db23f-113">面板概觀</span><span class="sxs-lookup"><span data-stu-id="db23f-113">Panels Overview</span></span>](panels-overview.md)
