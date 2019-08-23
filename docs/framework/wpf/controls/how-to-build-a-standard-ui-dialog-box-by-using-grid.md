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
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>作法：使用 Grid 建置標準 UI 對話方塊
這個範例示範如何[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.Controls.Grid>使用專案來建立標準對話方塊。  
  
## <a name="example"></a>範例  
 下列範例會建立對話方塊, 例如 Windows 作業系統中的 [**執行**] 對話方塊。  
  
 此範例會建立<xref:System.Windows.Controls.Grid> , 並<xref:System.Windows.Controls.ColumnDefinition>使用和<xref:System.Windows.Controls.RowDefinition>類別來定義五個數據行和四個數據列。  
  
 然後, 此範例會新增並<xref:System.Windows.Controls.Image>放置`RunIcon.png`, 以代表在對話方塊中找到的影像。 影像會放在<xref:System.Windows.Controls.Grid> (左上角) 的第一個資料行和資料列中。  
  
 接下來, 此範例會<xref:System.Windows.Controls.TextBlock>將專案加入至第一個資料行, 該資料行會跨越第一個資料列的其餘資料行。 它會將<xref:System.Windows.Controls.TextBlock>另一個元素新增至第一個資料行中的第二個數據列, 以代表 [**開啟**] 文字方塊。 <xref:System.Windows.Controls.TextBlock>如下所示, 表示資料輸入區域。  
  
 最後, 此範例會將<xref:System.Windows.Controls.Button>三個元素加入至最後一個資料列, 這表示 [**確定]** 、[**取消** **] 和 [流覽]** 事件。  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [面板概觀](panels-overview.md)
- [HOW-TO 主題](grid-how-to-topics.md)
