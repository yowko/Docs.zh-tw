---
title: "GridView 資料行行首樣式和範本概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料行行首, 自訂"
  - "控制項, ListView"
  - "GridView 檢視模式, 自訂資料行行首"
  - "頁首, 自訂"
  - "ListView 控制項 [WPF], GridView 資料行行首樣式"
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# GridView 資料行行首樣式和範本概觀
本概觀將討論在 <xref:System.Windows.Controls.ListView> 控制項的 <xref:System.Windows.Controls.GridView> 檢視模式下，用來自訂資料行行首的屬性優先順序。  
  
## 自訂 GridView 中的資料行行首  
 在 <xref:System.Windows.Controls.GridView> 中定義資料行行首的內容、配置和樣式的屬性可以在許多相關的類別找到。  這些屬性有部分的功能類似或完全相同。  
  
 下表的列顯示執行相同功能的屬性群組。  您可以使用這些屬性自訂 <xref:System.Windows.Controls.GridView> 中的資料行行首。  相關屬性的優先順序是從右到左，最右欄的屬性擁有最高的優先順序。  例如，如果在 <xref:System.Windows.Controls.GridViewColumnHeader> 物件上設定 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>，而且在相關聯的 <xref:System.Windows.Controls.GridViewColumn> 上設定 <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>，則 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 優先適用。  在此情況下，<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> 就沒有作用。  
  
 **GridView 中資料行行首的相關屬性**  
  
|||||  
|-|-|-|-|  
|**類別**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**內容功能表屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|不適用|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**工具提示**<br /><br /> **屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|不適用|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**頁首樣板**<br /><br /> **屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>\/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>\/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>\/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**樣式屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>針對**行首樣板屬性**，如果同時設定樣板和樣板選取器屬性，則樣板屬性優先適用。  例如，如果同時設定 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 和 <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> 屬性，則 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 屬性優先適用。  
  
## 請參閱  
 [HOW TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)