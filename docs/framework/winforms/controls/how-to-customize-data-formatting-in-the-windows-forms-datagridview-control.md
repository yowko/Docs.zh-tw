---
title: "如何：自訂 Windows Form DataGridView 控制項中的資料格式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "儲存格, 在 DataGridView 控制項中變更色彩 [Windows Form]"
  - "色彩, 在 DataGridView 控制項中變更 [Windows Form]"
  - "資料 [Windows Form], 在 DataGridView 控制項中格式化"
  - "資料格, 格式化資料"
  - "DataGridView 控制項 [Windows Form], 儲存格自訂"
  - "DataGridView 控制項 [Windows Form], 儲存格樣式"
  - "DataGridView 控制項 [Windows Form], 變更儲存格色彩"
  - "DataGridView 控制項 [Windows Form], 格式化資料"
  - "DataGridView 控制項 [Windows Form], 替代要顯示的儲存格值"
  - "Windows Form, 變更 DataGridView 儲存格的色彩"
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 如何：自訂 Windows Form DataGridView 控制項中的資料格式
下列程式碼範例示範如何實作 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName> 事件的處理常式，這會根據其資料行和值變更儲存格的顯示方式。  
  
 包含負數之資料行中的 `Balance` 儲存格已指定為紅色背景。  您也可以格式化這些儲存格為貨幣，在負值周圍顯示括號。  如需詳細資訊，請參閱[如何：格式化 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)。  
  
 `Priority` 資料行中的儲存格會顯示影像取代對應的文字儲存格的值。  <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> 的 <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> 屬性用來取得文字儲存格的值，並設定對應的影像顯示值。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
-   名為 `highPri.bmp`、`mediumPri.bmp` 和 `lowPri.bmp` 的 <xref:System.Drawing.Bitmap> 影像位於與可執行檔相同的目錄中。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Drawing.Bitmap>   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [如何：格式化 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)