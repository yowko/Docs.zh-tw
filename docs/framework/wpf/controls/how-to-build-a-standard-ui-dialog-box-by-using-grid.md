---
title: 作法：使用 Grid 建置標準 UI 對話方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923411"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="174af-102">作法：使用 Grid 建置標準 UI 對話方塊</span><span class="sxs-lookup"><span data-stu-id="174af-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="174af-103">這個範例示範如何[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.Controls.Grid>使用專案來建立標準對話方塊。</span><span class="sxs-lookup"><span data-stu-id="174af-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="174af-104">範例</span><span class="sxs-lookup"><span data-stu-id="174af-104">Example</span></span>  
 <span data-ttu-id="174af-105">下列範例會建立對話方塊, 例如 Windows 作業系統中的 [**執行**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="174af-105">The following example creates a dialog box like the **Run** dialog box in the Windows operating system.</span></span>  
  
 <span data-ttu-id="174af-106">此範例會建立<xref:System.Windows.Controls.Grid> , 並<xref:System.Windows.Controls.ColumnDefinition>使用和<xref:System.Windows.Controls.RowDefinition>類別來定義五個數據行和四個數據列。</span><span class="sxs-lookup"><span data-stu-id="174af-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="174af-107">然後, 此範例會新增並<xref:System.Windows.Controls.Image>放置`RunIcon.png`, 以代表在對話方塊中找到的影像。</span><span class="sxs-lookup"><span data-stu-id="174af-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="174af-108">影像會放在<xref:System.Windows.Controls.Grid> (左上角) 的第一個資料行和資料列中。</span><span class="sxs-lookup"><span data-stu-id="174af-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="174af-109">接下來, 此範例會<xref:System.Windows.Controls.TextBlock>將專案加入至第一個資料行, 該資料行會跨越第一個資料列的其餘資料行。</span><span class="sxs-lookup"><span data-stu-id="174af-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="174af-110">它會將<xref:System.Windows.Controls.TextBlock>另一個元素新增至第一個資料行中的第二個數據列, 以代表 [**開啟**] 文字方塊。</span><span class="sxs-lookup"><span data-stu-id="174af-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="174af-111"><xref:System.Windows.Controls.TextBlock>如下所示, 表示資料輸入區域。</span><span class="sxs-lookup"><span data-stu-id="174af-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="174af-112">最後, 此範例會將<xref:System.Windows.Controls.Button>三個元素加入至最後一個資料列, 這表示 [**確定]** 、[**取消** **] 和 [流覽]** 事件。</span><span class="sxs-lookup"><span data-stu-id="174af-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="174af-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="174af-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [<span data-ttu-id="174af-114">面板概觀</span><span class="sxs-lookup"><span data-stu-id="174af-114">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="174af-115">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="174af-115">How-to Topics</span></span>](grid-how-to-topics.md)
