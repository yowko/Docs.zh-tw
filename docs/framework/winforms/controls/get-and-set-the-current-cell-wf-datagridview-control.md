---
title: 如何：取得和設定 Windows Form DataGridView 控制項中目前的儲存格
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b53d135a1d019ce20dfc8c5c2c1ba59e5968306e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>如何：取得和設定 Windows Form DataGridView 控制項中目前的儲存格
互動<xref:System.Windows.Forms.DataGridView>通常會要求您以程式設計方式探索哪些儲存格是目前作用中。 您也可能需要變更目前的儲存格。 您可以執行這些工作與<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性。  
  
> [!NOTE]
>  您無法設定目前的儲存格的資料列或資料行具有其<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>屬性設定為`false`。  
  
 取決於<xref:System.Windows.Forms.DataGridView>控制項的選取模式，變更目前的儲存格可以變更選取項目。 如需詳細資訊，請參閱[Windows Form DataGridView 控制項中的選取模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="to-get-the-current-cell-programmatically"></a>若要以程式設計方式取得目前儲存格  
  
-   使用<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>若要以程式設計方式設定的目前儲存格  
  
-   設定<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性<xref:System.Windows.Forms.DataGridView>控制項。 在下列程式碼範例中，目前儲存格設定 0，資料行 1 的資料列。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   <xref:System.Windows.Forms.Button> 控制項名為`getCurrentCellButton`和`setCurrentCellButton`。 在 Visual C# 中，您必須將附加<xref:System.Windows.Forms.Control.Click>至相關聯的事件處理常式，範例程式碼中的每個按鈕的事件。  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的選取模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
