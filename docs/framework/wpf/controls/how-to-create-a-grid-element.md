---
title: "如何：建立 Grid 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd9614aee6e2bf7085b2fbee77993217439320a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="826c4-102">如何：建立 Grid 項目</span><span class="sxs-lookup"><span data-stu-id="826c4-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="826c4-103">範例</span><span class="sxs-lookup"><span data-stu-id="826c4-103">Example</span></span>  
 <span data-ttu-id="826c4-104">下列範例示範如何建立和使用的執行個體<xref:System.Windows.Controls.Grid>使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或程式碼。</span><span class="sxs-lookup"><span data-stu-id="826c4-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="826c4-105">這個範例會使用三個<xref:System.Windows.Controls.ColumnDefinition>物件和三個<xref:System.Windows.Controls.RowDefinition>物件建立一個方格，其中擁有九個資料格，例如工作表。</span><span class="sxs-lookup"><span data-stu-id="826c4-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="826c4-106">每個資料格包含<xref:System.Windows.Controls.TextBlock>項目，表示資料及上方資料列包含<xref:System.Windows.Controls.TextBlock>與<xref:System.Windows.Controls.Grid.ColumnSpan%2A>套用的屬性。</span><span class="sxs-lookup"><span data-stu-id="826c4-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="826c4-107">若要顯示的界限，每個資料格，<xref:System.Windows.Controls.Grid.ShowGridLines%2A>屬性已啟用。</span><span class="sxs-lookup"><span data-stu-id="826c4-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="826c4-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="826c4-108">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="826c4-109">面板概觀</span><span class="sxs-lookup"><span data-stu-id="826c4-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
