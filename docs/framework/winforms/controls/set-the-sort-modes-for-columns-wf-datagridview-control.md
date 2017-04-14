---
title: "如何：設定 Windows Form DataGridView 控制項中的資料行排序模式 | Microsoft Docs"
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
  - "資料格, 排序資料"
  - "DataGridView 控制項 [Windows Form], 排序模式"
  - "排序, 資料格"
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：設定 Windows Form DataGridView 控制項中的資料行排序模式
在 <xref:System.Windows.Forms.DataGridView> 控制項中，文字方塊資料行使用了預設的自動排序，其他資料行型別則沒有自動排序。  您有時候會想要覆寫這些預設值。  例如，您可以顯示影像，以代替文字、數字或列舉型別 \(Enumeration\) 儲存格值。  雖然無法排序影像，但可以排序影像所代表的基礎值。  
  
 在 <xref:System.Windows.Forms.DataGridView> 控制項中，資料行的 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 屬性值會決定其排序行為。  
  
 下列程序顯示出 [如何：自訂 Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)的 `Priority` 資料行。  這個資料行是影像資料行，且預設值為不可排序。  不過它所包含的實際儲存格值是字串，所以可以對其自動排序。  
  
### 若要設定資料行的排序模式  
  
-   設定 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=fullName> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，包含名為 `Priority` 的資料行。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=fullName>   
 [在 Windows Form DataGridView 控制項中排序資料](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的資料行排序模式](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)   
 [如何：自訂 Windows Form DataGridView 控制項的排序](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)