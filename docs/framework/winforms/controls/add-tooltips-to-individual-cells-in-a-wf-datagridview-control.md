---
title: "如何：將工具提示加入至 Windows Form DataGridView 控制項中的個別儲存格"
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
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 73d12bb38e4929582a8317d8ab3d7b23a7d1f603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>如何：將工具提示加入至 Windows Form DataGridView 控制項中的個別儲存格
根據預設，工具提示會用來顯示的值<xref:System.Windows.Forms.DataGridView>太小，無法顯示其全部內容的資料格。 您可以設定個別資料格的工具提示文字值不過，覆寫這個行為。 這是要顯示給使用者的其他資訊的資料格，或儲存格內容的其他描述為使用者提供很有用。 比方說，如果您有顯示狀態圖示的資料列時，您可能要提供使用工具提示的文字說明。  
  
 您也可以停用的資料格層級的工具提示顯示設定<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>屬性`false`。  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>若要加入儲存格的工具提示  
  
-   設定 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> 屬性。  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   這個範例需要：  
  
-   A<xref:System.Windows.Forms.DataGridView>控制項，名為`dataGridView1`，其中包含名為資料行`Rating`顯示四個星號透過其中一個的字串值 ("*") 符號。 <xref:System.Windows.Forms.DataGridView.CellFormatting>控制項事件的範例所示的事件處理常式方法必須有關聯。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="robust-programming"></a>穩固程式設計  
 當您繫結<xref:System.Windows.Forms.DataGridView>控制權傳輸至外部資料來源或提供您自己的資料來源藉由實作虛擬模式，您可能會遇到效能問題。 若要使用大量的資料時，請避免對效能帶來負面影響，處理<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>事件，而不是設定<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>多個儲存格的屬性。 當您處理這個事件，取得儲存格的值<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>屬性引發事件，並傳回值<xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType>屬性設為指定的事件處理常式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>  
 [在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
