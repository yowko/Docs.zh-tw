---
title: 如何：在使用 GridView 的 ListView 中為數據列建立樣式
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271941"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>操作說明：為實作 GridView 之 ListView 中的資料列設定樣式
這個範例示範如何在使用模式的控制項中為數據列建立樣式 <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> 。  
  
## <a name="example"></a>範例  
 您可以設定控制項的來設定控制項的資料列樣式 <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListView> 。 針對以物件表示的專案設定樣式 <xref:System.Windows.Controls.ListViewItem> 。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ControlTemplate> 會參考用來顯示資料列內容的物件。  
  
 從下列範例解壓縮的完整範例，會顯示儲存在 XML 資料庫中的一組歌曲資訊。 資料庫中的每一首歌都有一個評等欄位，而此欄位的值會指定歌曲資訊資料列的顯示方式。  
  
 下列範例示範如何定義 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListViewItem> 代表 song 集合中之歌曲的物件。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>參考 <xref:System.Windows.Controls.ControlTemplate> 物件，這些物件會指定如何顯示歌曲資訊的資料列。  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 下列範例顯示 <xref:System.Windows.Controls.ControlTemplate> 將文字字串加入 `"Strongly Recommended"` 至資料列的。 此範本會在中參考 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ，並且會在歌曲的評等值為 5 (五) 時顯示。 <xref:System.Windows.Controls.ControlTemplate>包含 <xref:System.Windows.Controls.GridViewRowPresenter> 物件，該物件會根據 view 模式所定義，在資料行中配置資料列的內容 <xref:System.Windows.Controls.GridView> 。  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 下列範例會定義 <xref:System.Windows.Controls.GridView> 。  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [操作說明主題](listview-how-to-topics.md)
- [ListView 概觀](listview-overview.md)
- [樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
