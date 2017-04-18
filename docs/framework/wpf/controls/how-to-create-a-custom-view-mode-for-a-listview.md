---
title: "如何：建立 ListView 的自訂檢視模式 | Microsoft Docs"
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
  - "ListView 控制項, 建立自訂檢視模式"
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：建立 ListView 的自訂檢視模式
本範例示範如何建立 <xref:System.Windows.Controls.ListView> 控制項的自訂 <xref:System.Windows.Controls.ListView.View%2A> 模式。  
  
## 範例  
 當您建立 <xref:System.Windows.Controls.ListView> 控制項的自訂檢視時，必須使用 <xref:System.Windows.Controls.ViewBase> 類別。  下列範例顯示稱為 `PlainView` 的檢視模式，這個模式是從 <xref:System.Windows.Controls.ViewBase> 類別衍生而來。  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 若要將樣式套用到自訂檢視，請使用 <xref:System.Windows.Style> 類別。  下列範例會定義 `PlainView` 檢視模式的 <xref:System.Windows.Style>。  在上一個範例中，這個樣式是設定成 `PlainView` 定義的 <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> 屬性值。  
  
 [!code-xml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 若要定義自訂檢視模式中資料的配置，請定義 <xref:System.Windows.DataTemplate> 物件。  下列範例定義可用來在 `PlainView` 檢視模式中顯示資料的 <xref:System.Windows.DataTemplate>。  
  
 [!code-xml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 下列範例示範如何定義 `PlainView` 檢視模式的 <xref:System.Windows.ResourceKey>，而該檢視模式則使用上一個範例中定義的 <xref:System.Windows.DataTemplate>。  
  
 [!code-xml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 如果您將 <xref:System.Windows.Controls.ListView.View%2A> 屬性設定為資源索引鍵，<xref:System.Windows.Controls.ListView> 控制項就可以使用自訂檢視。  下列範例示範如何指定 `PlainView` 做為 <xref:System.Windows.Controls.ListView> 的檢視模式。  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 如需完整範例，請參閱[具有多個檢視的 ListView 範例](http://go.microsoft.com/fwlink/?LinkID=160013) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)