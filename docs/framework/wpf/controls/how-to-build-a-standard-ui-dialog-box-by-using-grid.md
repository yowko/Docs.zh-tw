---
title: "如何：使用 Grid 建置標準 UI 對話方塊"
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
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 641e74d8c9f8db1afde19c008de08f0029b0bf90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="c34a4-102">如何：使用 Grid 建置標準 UI 對話方塊</span><span class="sxs-lookup"><span data-stu-id="c34a4-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="c34a4-103">這個範例示範如何建立標準[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]對話方塊使用<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="c34a4-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c34a4-104">範例</span><span class="sxs-lookup"><span data-stu-id="c34a4-104">Example</span></span>  
 <span data-ttu-id="c34a4-105">下列範例會建立與類似的對話方塊**執行**對話方塊[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]作業系統。</span><span class="sxs-lookup"><span data-stu-id="c34a4-105">The following example creates a dialog box like the **Run** dialog box in the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="c34a4-106">此範例會建立<xref:System.Windows.Controls.Grid>並用<xref:System.Windows.Controls.ColumnDefinition>和<xref:System.Windows.Controls.RowDefinition>類別定義五個資料行和四個資料列。</span><span class="sxs-lookup"><span data-stu-id="c34a4-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="c34a4-107">此範例會將加入並放置<xref:System.Windows.Controls.Image>， `RunIcon.png`，以代表對話方塊中找到的映像。</span><span class="sxs-lookup"><span data-stu-id="c34a4-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="c34a4-108">影像會放在第一個資料行和資料列的<xref:System.Windows.Controls.Grid>（左上角）。</span><span class="sxs-lookup"><span data-stu-id="c34a4-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="c34a4-109">接下來，此範例會將<xref:System.Windows.Controls.TextBlock>第一個資料行，其涵蓋其餘的資料行的第一個資料列的項目。</span><span class="sxs-lookup"><span data-stu-id="c34a4-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="c34a4-110">它會加入另一個<xref:System.Windows.Controls.TextBlock>中第一個資料行中，以代表第二個資料列的項目**開啟**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c34a4-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="c34a4-111">A<xref:System.Windows.Controls.TextBlock>如下所示，它代表資料輸入區域。</span><span class="sxs-lookup"><span data-stu-id="c34a4-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="c34a4-112">最後，範例會加入三個<xref:System.Windows.Controls.Button>元素到最後一個資料列，代表**確定**，**取消**，和**瀏覽**事件。</span><span class="sxs-lookup"><span data-stu-id="c34a4-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c34a4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c34a4-113">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.GridUnitType>  
 [<span data-ttu-id="c34a4-114">面板概觀</span><span class="sxs-lookup"><span data-stu-id="c34a4-114">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="c34a4-115">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="c34a4-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
