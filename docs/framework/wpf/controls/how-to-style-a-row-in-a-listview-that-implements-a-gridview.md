---
title: 操作說明：為實作 GridView 之 ListView 中的資料列設定樣式
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 150988aab368e3ffef0107d29bea5ebc53163946
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459317"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>操作說明：為實作 GridView 之 ListView 中的資料列設定樣式
這個範例示範如何在 <xref:System.Windows.Controls.ListView> 控制項中，將執行 <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> 模式的資料列樣式。  
  
## <a name="example"></a>範例  
 您可以藉由在 [<xref:System.Windows.Controls.ListView>] 控制項上設定 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>，將 <xref:System.Windows.Controls.ListView> 控制項中的資料列樣式。 針對以 <xref:System.Windows.Controls.ListViewItem> 物件表示的專案，設定其樣式。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 會參考用來顯示資料列內容的 <xref:System.Windows.Controls.ControlTemplate> 物件。  
  
 完整範例 (下列範例的擷取來源) 會顯示一個儲存在 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料庫中歌曲資訊的集合。 資料庫中的每一首歌都有一個評等欄位，而此欄位的值會指定歌曲資訊資料列的顯示方式。  
  
 下列範例示範如何定義代表歌曲集合中歌曲的 <xref:System.Windows.Controls.ListViewItem> 物件 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 會參考 <xref:System.Windows.Controls.ControlTemplate> 物件，以指定如何顯示歌曲資訊的資料列。  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 下列範例顯示將文字字串 `"Strongly Recommended"` 加入資料列的 <xref:System.Windows.Controls.ControlTemplate>。 此範本會在 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 中參照，並會在歌曲的評等值為5（5）時顯示。 <xref:System.Windows.Controls.ControlTemplate> 包含 <xref:System.Windows.Controls.GridViewRowPresenter> 物件，它會在資料行中配置資料列的內容，如 <xref:System.Windows.Controls.GridView> 視圖模式所定義。  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 下列範例會定義 <xref:System.Windows.Controls.GridView>。  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [「如何」主題](listview-how-to-topics.md)
- [ListView 概觀](listview-overview.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
