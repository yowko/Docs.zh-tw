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
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>如何：使用 Grid 建置標準 UI 對話方塊
這個範例示範如何建立標準[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]對話方塊使用<xref:System.Windows.Controls.Grid>項目。  
  
## <a name="example"></a>範例  
 下列範例會建立與類似的對話方塊**執行**對話方塊[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]作業系統。  
  
 此範例會建立<xref:System.Windows.Controls.Grid>並用<xref:System.Windows.Controls.ColumnDefinition>和<xref:System.Windows.Controls.RowDefinition>類別定義五個資料行和四個資料列。  
  
 此範例會將加入並放置<xref:System.Windows.Controls.Image>， `RunIcon.png`，以代表對話方塊中找到的映像。 影像會放在第一個資料行和資料列的<xref:System.Windows.Controls.Grid>（左上角）。  
  
 接下來，此範例會將<xref:System.Windows.Controls.TextBlock>第一個資料行，其涵蓋其餘的資料行的第一個資料列的項目。 它會加入另一個<xref:System.Windows.Controls.TextBlock>中第一個資料行中，以代表第二個資料列的項目**開啟**文字方塊。 A<xref:System.Windows.Controls.TextBlock>如下所示，它代表資料輸入區域。  
  
 最後，範例會加入三個<xref:System.Windows.Controls.Button>元素到最後一個資料列，代表**確定**，**取消**，和**瀏覽**事件。  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.GridUnitType>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
