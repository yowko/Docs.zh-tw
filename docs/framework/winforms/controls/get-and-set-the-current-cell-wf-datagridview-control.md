---
title: HOW TO：在 Windows Forms DataGridView 控制項中取得和設定目前的儲存格
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: fb71a6e3259d3007e11f528377c95a9c4cbeb023
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096975"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>HOW TO：在 Windows Forms DataGridView 控制項中取得和設定目前的儲存格
互動<xref:System.Windows.Forms.DataGridView>通常會要求您以程式設計方式探索哪些儲存格是目前作用中。 此外，您可能也需要變更目前的儲存格。 您可以執行這些工作與<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性。  
  
> [!NOTE]
>  您無法設定目前的儲存格的資料列或資料行中其<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>屬性設定為`false`。  
  
 取決於<xref:System.Windows.Forms.DataGridView>控制項的選取模式中，變更目前的儲存格可以變更選取項目。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的選取模式](selection-modes-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="to-get-the-current-cell-programmatically"></a>若要以程式設計方式取得目前的儲存格  
  
-   使用<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>以程式設計方式設定目前的儲存格  
  
-   設定<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性<xref:System.Windows.Forms.DataGridView>控制項。 在下列程式碼範例中，目前儲存格是設定為 0，資料行 1 的資料列。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   <xref:System.Windows.Forms.Button> 名為的控制項`getCurrentCellButton`和`setCurrentCellButton`。 在視覺效果C#，您必須將附加<xref:System.Windows.Forms.Control.Click>相關聯的事件處理常式的範例程式碼中的每個按鈕的事件。  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的選取模式](selection-modes-in-the-windows-forms-datagridview-control.md)
