---
title: "如何：自訂 Windows Form DataGridView 控制項的排序 | Microsoft Docs"
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
  - "資料格, 自訂排序"
  - "DataGridView 控制項 [Windows Form], 排序"
  - "排序, DataGridView 控制項"
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：自訂 Windows Form DataGridView 控制項的排序
<xref:System.Windows.Forms.DataGridView> 控制項提供自動排序，但是根據您的需求，您可能需要自訂排序作業。  例如，您可以使用程式設計排序建立替代的使用者介面 \(UI\)。  或者為了在排序時獲得更大的彈性，您可以處理 <xref:System.Windows.Forms.DataGridView.SortCompare> 事件或呼叫 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(IComparer)` 多載，例如排序多個資料行。  
  
 下列程式碼範例示範自訂排序的三種方法。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的資料行排序模式](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)。  
  
## 程式設計排序  
 下列程式碼範例示範使用 <xref:System.Windows.Forms.DataGridView.SortOrder%2A> 和 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> 屬性的程式設計排序，以決定排序的方向和 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> 屬性來手動設定排序圖像。  <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(DataGridViewColumn,ListSortDirection)` 多載只用於在單一資料行排序資料。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## 使用 SortCompare 事件的自訂排序  
 下列程式碼範例示範使用 <xref:System.Windows.Forms.DataGridView.SortCompare> 事件處理常式自訂排序 。  所選 <xref:System.Windows.Forms.DataGridViewColumn> 已排序，若資料行中有重複的值，則 ID 資料行會用於決定最終的順序。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## 使用 IComparer 介面的自訂排序  
 下列程式碼範例示範使用 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(IComparer)` 多載自訂排序，這會採用 <xref:System.Collections.IComparer> 介面的實作來執行多個資料行排序。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## 編譯程式碼  
 這些範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [在 Windows Form DataGridView 控制項中排序資料](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的資料行排序模式](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)   
 [如何：設定 Windows Form DataGridView 控制項中的資料行排序模式](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)