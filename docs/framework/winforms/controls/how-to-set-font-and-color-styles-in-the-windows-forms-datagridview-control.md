---
title: "如何：設定 Windows Form DataGridView 控制項的字型和色彩樣式 | Microsoft Docs"
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
  - "資料格, 色彩樣式"
  - "資料格, 自訂儲存格"
  - "資料格, 字型樣式"
  - "DataGridView 控制項 [Windows Form], 儲存格自訂"
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：設定 Windows Form DataGridView 控制項的字型和色彩樣式
您可以設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別的屬性，在 <xref:System.Windows.Forms.DataGridView> 控制項內指定儲存格的視覺外觀。  您可以從 <xref:System.Windows.Forms.DataGridView> 類別和其附屬類別的各種屬性擷取此類別的執行個體，或者您可以具現化 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件以便指派給這些屬性。  
  
 下列程序將示範使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> 屬性進行儲存格外觀的基本自訂。  控制項中的每個儲存格會透過這個屬性繼承指定的樣式，除非它們在資料行、資料列，或儲存格層級遭到覆寫。  如需樣式繼承的範例，請參閱[如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。  如需 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別其他用法的相關資訊，請參閱＜另請參閱＞一節中所列的主題。  
  
 在 Visual Studio 中對這項工作有廣泛的支援。  另請參閱[如何：使用設計工具設定 Windows Form DataGridView 控制項的預設儲存格樣式和儲存格式](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\))。  
  
### 指定 DataGridView 儲存格所使用的字型  
  
-   設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> 屬性。  下列程式碼範例使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> 屬性來設定整個控制項的字型。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### 指定 DataGridView 儲存格的前景和背景色彩  
  
-   設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> 屬性。  下列程式碼範例使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> 屬性來設定整個控制項的字型。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### 指定所選取 DataGridView 儲存格的前景和背景色彩  
  
-   設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> 和 <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> 屬性。  下列程式碼範例使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> 屬性來設定整個控制項的字型。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Drawing?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 穩固程式設計  
 若要達到最大延展性，您應該在使用相同樣式的多個資料列、資料行或儲存格之間共用 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，而不是分別設定每個項目的樣式屬性。  如需詳細資訊，請參閱[縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 [Windows Form DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)