---
title: "操作說明：為實作 GridView 之 ListView 中的資料列設定樣式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c51f6cc5c35200267aa84960655fd734a937a7c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>操作說明：為實作 GridView 之 ListView 中的資料列設定樣式
這個範例示範如何設定樣式中的資料列<xref:System.Windows.Controls.ListView>實作控制項<xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A>模式。  
  
## <a name="example"></a>範例  
 您可以設定樣式中的資料列<xref:System.Windows.Controls.ListView>藉由設定控制<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>上<xref:System.Windows.Controls.ListView>控制項。 將會以表示其項目的樣式設定<xref:System.Windows.Controls.ListViewItem>物件。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>參考<xref:System.Windows.Controls.ControlTemplate>用來顯示資料列內容的物件。  
  
 完整範例 (下列範例的擷取來源) 會顯示一個儲存在 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料庫中歌曲資訊的集合。 資料庫中的每一首歌都有一個評等欄位，而此欄位的值會指定歌曲資訊資料列的顯示方式。  
  
 下列範例示範如何定義<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>如<xref:System.Windows.Controls.ListViewItem>代表歌曲集合中的歌曲的物件。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>參考<xref:System.Windows.Controls.ControlTemplate>指定如何顯示歌曲資訊的資料列的物件。  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 下列範例所示<xref:System.Windows.Controls.ControlTemplate>，將文字字串加入`"Strongly Recommended"`資料列。 此範本會參考<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>並顯示當歌曲的評等的值為 5 （五個）。 <xref:System.Windows.Controls.ControlTemplate>包含<xref:System.Windows.Controls.GridViewRowPresenter>配置所定義的資料行中的資料列內容的物件<xref:System.Windows.Controls.GridView>檢視模式。  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 下列範例會定義<xref:System.Windows.Controls.GridView>。  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [操作說明主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)
