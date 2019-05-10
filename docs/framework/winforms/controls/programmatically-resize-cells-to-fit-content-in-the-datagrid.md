---
title: HOW TO：以程式設計方式調整儲存格大小使符合 Windows Forms DataGridView 控制項的內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells to fit content
- cells [Windows Forms], resizing to fit contents
- DataGridView control [Windows Forms], resizing cells
- grids [Windows Forms], resizing cells to fit content
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
ms.openlocfilehash: 8c95d60ba36275ec4d0e263f97bc28a559c1f38e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654461"
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a>HOW TO：以程式設計方式調整儲存格大小使符合 Windows Forms DataGridView 控制項的內容
您可以使用 <xref:System.Windows.Forms.DataGridView> 控制項方法來調整資料列、資料行和標頭的大小，讓它們可以顯示完整的值，而不至發生截斷狀況。 您有時可使用這些方法來調整您選擇的 <xref:System.Windows.Forms.DataGridView> 項目大小。 此外，您可以將控制項設定為每當內容變更時，就自動調整這些項目的大小。 不過，在使用大型資料集或資料經常變更時，這樣做可能會沒有效率。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)。  
  
 一般而言，只有在從資料來源載入新資料或當使用者已編輯某個值時，才會以程式設計方式調整 <xref:System.Windows.Forms.DataGridView> 項目，以符合項目的內容大小。 這對於最佳化效能很有用，不過如果想讓使用者使用滑鼠手動調整資料列和資料行的大小，這也非常有用。  
  
 下列程式碼範例示範以程式設計方式調整大小時可使用的選項。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [調整 Windows Forms DataGridView 控制項中資料行和資料列的大小](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)
- [如何：自動調整大小的資料格，當 Windows Form DataGridView 控制項中的內容變更](automatically-resize-cells-when-content-changes-in-the-datagrid.md)
