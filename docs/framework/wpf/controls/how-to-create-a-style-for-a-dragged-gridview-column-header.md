---
title: "如何：為已拖曳的 GridView 資料行行首建立樣式 | Microsoft Docs"
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
  - "ListView 控制項, 樣式"
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：為已拖曳的 GridView 資料行行首建立樣式
本範例顯示當使用者變更資料行的位置時，如何變更拖曳之 <xref:System.Windows.Controls.GridViewColumnHeader> 的外觀。  
  
## 範例  
 在使用 <xref:System.Windows.Controls.GridView> 做為檢視模式的 <xref:System.Windows.Controls.ListView> 中，當您將資料行行首拖曳至另一個位置時，資料行會移動至新位置。  當您拖曳資料行行首時，除了原始行首之外，還會出現行首的浮動複本。  <xref:System.Windows.Controls.GridView> 中的資料行行首是由 <xref:System.Windows.Controls.GridViewColumnHeader> 物件表示。  
  
 若要自訂浮動和原始行首的外觀，您可以設定 <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> 以修改 <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>。  當 <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> 屬性值是 `true`，而且 <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> 屬性值 <xref:System.Windows.Controls.GridViewColumnHeaderRole> 時，就會套用這些 <xref:System.Windows.Controls.ControlTemplate.Triggers%2A>。  
  
 當使用者按下滑鼠按鈕，按住並將滑鼠停留在 <xref:System.Windows.Controls.GridViewColumnHeader> 時，<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> 屬性值會變更為 `true`。  同樣地，當使用者開始進行拖曳作業時，<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> 屬性會變更為 <xref:System.Windows.Controls.GridViewColumnHeaderRole>。  
  
 下列範例說明當使用者將資料行拖曳至新位置時，如何設定 <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> 以變更原始和浮動行首的 <xref:System.Windows.Controls.Control.Foreground%2A> 和 <xref:System.Windows.Controls.Control.Background%2A> 色彩。  
  
 [!code-xml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## 請參閱  
 <xref:System.Windows.Controls.GridViewColumnHeader>   
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>   
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)