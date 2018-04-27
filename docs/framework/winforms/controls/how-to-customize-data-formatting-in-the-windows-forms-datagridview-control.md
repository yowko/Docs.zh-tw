---
title: 如何：自訂 Windows Form DataGridView 控制項中的資料格式
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
- DataGridView control [Windows Forms], formatting data
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], changing colors in DataGridView control [Windows Forms]
- colors [Windows Forms], changing in DataGridView control [Windows Forms]
- data [Windows Forms], formatting in DataGridView control
- DataGridView control [Windows Forms], cell customization
- DataGridView control [Windows Forms], changing cell colors
- Windows Forms, changing colors of DataGridView cells
- DataGridView control [Windows Forms], substituting cell values for display
- data grids [Windows Forms], formatting data
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: da016bf659f9eef06074f52e5b716e73d514e48b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a>如何：自訂 Windows Form DataGridView 控制項中的資料格式
下列程式碼範例示範如何實作 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> 事件的處理常式，這會根據其資料行和值變更儲存格的顯示方式。  
  
 包含負數之資料行中的 `Balance` 儲存格已指定為紅色背景。 您也可以格式化這些儲存格為貨幣，在負值周圍顯示括號。 如需詳細資訊，請參閱[如何：格式化 Windows Forms DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)。  
  
 `Priority` 資料行中的儲存格會顯示影像取代對應的文字儲存格的值。 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> 的 <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> 屬性用來取得文字儲存格的值，並設定對應的影像顯示值。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
-   名為 `highPri.bmp`、`mediumPri.bmp` 和 `lowPri.bmp` 的 <xref:System.Drawing.Bitmap> 影像位於與可執行檔相同的目錄中。  
  
 Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Drawing.Bitmap>  
 [在 Windows Forms DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [操作說明：格式化 Windows Forms DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
