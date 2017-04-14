---
title: "如何：以程式設計方式調整儲存格大小以符合 Windows Form DataGridView 控制項的內容 | Microsoft Docs"
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
  - "儲存格, 調整大小以符合內容"
  - "資料格, 調整儲存格大小以符合內容"
  - "DataGridView 控制項 [Windows Form], 調整儲存格的大小"
  - "方格, 調整儲存格大小以符合內容"
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：以程式設計方式調整儲存格大小以符合 Windows Form DataGridView 控制項的內容
您可以使用 <xref:System.Windows.Forms.DataGridView> 控制項方法來調整資料列、資料行和標頭的大小，讓它們可以顯示完整的值，而不至發生截斷狀況。  您有時可使用這些方法來調整您選擇的 <xref:System.Windows.Forms.DataGridView> 項目大小。  此外，您可以將控制項設定為每當內容變更時，就自動調整這些項目的大小。  不過，在使用大型資料集或資料經常變更時，這樣做可能會沒有效率。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)。  
  
 一般而言，只有在從資料來源載入新資料或當使用者已編輯某個值時，才會以程式設計方式調整 <xref:System.Windows.Forms.DataGridView> 項目，以符合項目的內容大小。  這對於最佳化效能很有用，不過如果想讓使用者使用滑鼠手動調整資料列和資料行的大小，這也非常有用。  
  
 下列程式碼範例示範以程式設計方式調整大小時可使用的選項。  
  
## 範例  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 來編譯與執行完整的 Windows Forms 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>   
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>   
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>   
 [調整 Windows Form DataGridView 控制項中資料行和資料列的大小](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)   
 [如何：在 Windows Form DataGridView 控制項的內容變更時自動調整儲存格大小](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)