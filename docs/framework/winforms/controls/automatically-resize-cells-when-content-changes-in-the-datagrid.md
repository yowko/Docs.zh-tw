---
title: 如何：在 Windows Form DataGridView 控制項的內容變更時自動調整儲存格大小
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
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells automatically
- cells [Windows Forms], resizing automatically
- DataGridView control [Windows Forms], resizing cells
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 05d4703edd7300c7a051a3017514d76bb7966570
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a>如何：在 Windows Form DataGridView 控制項的內容變更時自動調整儲存格大小
您可以將 <xref:System.Windows.Forms.DataGridView> 控制項設定為每當內容變更就自動調整其資料列、資料行和標頭大小，讓儲存格的大小永遠足以容納並顯示所有的值，不發生內容截斷的情況。  
  
 您有許多選項可限制使用哪些儲存格來決定新的大小。 例如，您可以只根據目前顯示之資料列中的值，將控制項設定為自動調整其資料行的寬度。 如此一來，就可以避免在使用大量的資料列時效率低落，雖然在這種情況下，有時您也可能想要自行使用調整大小方法 (例如 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> ) 來調整大小。  
  
 如需稽核的詳細資訊，請參閱 [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)。  
  
 下列程式碼範例示範可供自動調整大小的選項。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
-   Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [調整 Windows Forms DataGridView 控制項中資料行和資料列的大小](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 [操作說明：以程式設計方式調整儲存格大小以符合 Windows Forms DataGridView 控制項的內容](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
