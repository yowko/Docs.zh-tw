---
title: 如何：使 Windows Form DataGridView 控制項中的資料行成為唯讀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 1ea4fdb6d38464993672c9aa98d8866812d21972
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a>如何：使 Windows Form DataGridView 控制項中的資料行成為唯讀
並非所有資料都是可編輯的。 在 <xref:System.Windows.Forms.DataGridView> 控制項中，資料行 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> 屬性值會決定使用者是否能編輯該資料行中的儲存格。 如需如何使控制項為完全唯讀資訊，請參閱[如何： 防止資料列新增和刪除 Windows Form DataGridView 控制項中的](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)。  
  
 在 Visual Studio 中會支援這項工作。  另請參閱[How to: 使用 Windows Form DataGridView 控制項設計工具中進行資料行唯讀](http://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\))。  
  
### <a name="to-make-a-column-read-only-programmatically"></a>以程式設計方式將資料行設為唯讀  
  
-   將 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> 屬性設定為 `true`。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，包含名為 `CompanyName` 的資料行。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [操作說明：防止在 Windows Forms DataGridView 控制項中新增和刪除資料列](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
