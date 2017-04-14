---
title: "如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式 | Microsoft Docs"
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
  - "儲存格, 樣式"
  - "資料格, 儲存格樣式"
  - "DataGridView 控制項 [Windows Form], 儲存格樣式"
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式
您可以使用 <xref:System.Windows.Forms.DataGridView> 控制項為整個控制項，以及為特定資料行和資料列，指定預設儲存格樣式。  這些預設值會從控制項層級往下篩選至資料行層級，接著至資料列層級，然後至儲存格層級。  如果在儲存格層級未設定特定 <xref:System.Windows.Forms.DataGridViewCellStyle> 屬性，則會使用資料列層級的預設屬性設定。  如果在資料列層級也未設定這個屬性，則會使用預設資料行設定。  最後，如果在資料行層級還是未設定這個屬性，則會使用預設 <xref:System.Windows.Forms.DataGridView> 設定。  您可以利用這項設定，避免必須在多個層級重複設定屬性。  您只需要在每個層級指定不同於上一層級的樣式。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
 在 Visual Studio 中對這項工作有廣泛的支援。  另請參閱[如何：使用設計工具設定 Windows Form DataGridView 控制項的預設儲存格樣式和資料格式](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\))。  
  
### 以程式設計方式設定預設儲存格樣式  
  
1.  設定透過 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> 屬性擷取之 <xref:System.Windows.Forms.DataGridViewCellStyle> 的屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  建立並初始化新的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，以供多個資料列和資料行使用。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  設定特定資料列和資料行的 `DefaultCellStyle` 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Drawing?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 穩固程式設計  
 若要在您使用非常大量的資料集時達到最大延展性，您應該共用使用相同樣式的多個資料列、資料行或儲存格之間的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，而不是分別設定每個項目的樣式屬性。  此外，您應該建立共用資料列，並使用 <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=fullName> 屬性來加以存取。  如需詳細資訊，請參閱[縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [如何：設定 Windows Form DataGridView 控制項的替代資料列樣式](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)