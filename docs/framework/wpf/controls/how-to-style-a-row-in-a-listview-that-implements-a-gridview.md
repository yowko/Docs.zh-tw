---
title: HOW TO：在實作 GridView 的 ListView 中設定資料列的樣式
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 9af8d10c7db2d3bbe8b9443402cbb1cfeaa7edb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052010"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>HOW TO：在實作 GridView 的 ListView 中設定資料列的樣式
此範例示範如何在資料列的樣式<xref:System.Windows.Controls.ListView>控制項，可實作<xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A>模式。  
  
## <a name="example"></a>範例  
 您可以在資料列的樣式<xref:System.Windows.Controls.ListView>控制項，藉由設定<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>上<xref:System.Windows.Controls.ListView>控制項。 設定以其項目的樣式<xref:System.Windows.Controls.ListViewItem>物件。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>參考<xref:System.Windows.Controls.ControlTemplate>用來顯示資料列內容的物件。  
  
 完整範例 (下列範例的擷取來源) 會顯示一個儲存在 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料庫中歌曲資訊的集合。 資料庫中的每一首歌都有一個評等欄位，而此欄位的值會指定歌曲資訊資料列的顯示方式。  
  
 下列範例示範如何定義<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>針對<xref:System.Windows.Controls.ListViewItem>代表歌曲集合中的歌曲的物件。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>參考<xref:System.Windows.Controls.ControlTemplate>物件，以指定如何顯示歌曲資訊資料列。  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 下列範例所示<xref:System.Windows.Controls.ControlTemplate>，將文字字串加入`"Strongly Recommended"`資料列。 此範本中參考<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>，並且在歌曲的評等的值為 5 （五） 時顯示。 <xref:System.Windows.Controls.ControlTemplate>包含<xref:System.Windows.Controls.GridViewRowPresenter>配置的資料行中的資料列的內容所定義的物件<xref:System.Windows.Controls.GridView>檢視模式。  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 下列範例會定義<xref:System.Windows.Controls.GridView>。  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [HOW-TO 主題](listview-how-to-topics.md)
- [ListView 概觀](listview-overview.md)
- [樣式設定和範本化](styling-and-templating.md)
