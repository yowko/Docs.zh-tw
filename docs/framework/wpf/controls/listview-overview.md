---
title: ListView 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 2f336d1eb8dcdfec3c3c8059ba865147c6b6c825
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187511"
---
# <a name="listview-overview"></a>ListView 概觀
該<xref:System.Windows.Controls.ListView>控制項提供基礎結構以在不同的佈局或視圖中顯示一組資料項目。 例如，使用者可能會想要以表格顯示資料項目，還要排序其資料行。  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>什麼是 ListView？  
 控制項<xref:System.Windows.Controls.ListView>是從<xref:System.Windows.Controls.ItemsControl>派生的<xref:System.Windows.Controls.ListBox>。 通常，其項是資料收集的成員，並表示為<xref:System.Windows.Controls.ListViewItem>物件。 a<xref:System.Windows.Controls.ListViewItem>是<xref:System.Windows.Controls.ContentControl>，只能包含單個子項目。 不過，該子元素可以是任何視覺元素。  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>定義 ListView 的檢視模式  
 要為<xref:System.Windows.Controls.ListView>控制項的內容指定視圖模式，請設置 屬性<xref:System.Windows.Controls.ListView.View%2A>。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供的一種視圖模式是<xref:System.Windows.Controls.GridView>，它顯示具有可自訂列的表中的資料項目的集合。  
  
 下面的示例演示如何為顯示員工資訊的<xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView>控制項定義 。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示上一個範例的資料顯示方式。  
  
 ![顯示帶有 GridView 輸出的 ListView 的螢幕截圖。](./media/gridview-overview/listview-gridview-output.jpg)  
  
 可以通過定義從類繼承的<xref:System.Windows.Controls.ViewBase>類來創建自訂視圖模式。 類<xref:System.Windows.Controls.ViewBase>提供創建自訂視圖所需的基礎結構。 如需有關如何建立自訂檢視的詳細資訊，請參閱[建立 ListView 的自訂檢視模式](how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>將資料繫結至 ListView  
 使用<xref:System.Windows.Controls.ItemsControl.Items%2A>和<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性為控制項指定項<xref:System.Windows.Controls.ListView>。 下面的示例將<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性設置到稱為`EmployeeInfoDataSource`的資料收集。  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 在<xref:System.Windows.Controls.GridView>中<xref:System.Windows.Controls.GridViewColumn>，物件綁定到指定的資料欄位。 下面的示例通過為<xref:System.Windows.Controls.GridViewColumn><xref:System.Windows.Data.Binding><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性指定 的 將物件綁定到資料欄位。  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 還可以指定 作為<xref:System.Windows.Data.Binding>用於設置列儲存格樣式<xref:System.Windows.DataTemplate>的定義的一部分。 在下面的<xref:System.Windows.DataTemplate>示例中，使用<xref:System.Windows.ResourceKey>集<xref:System.Windows.Data.Binding>標識 的 。 <xref:System.Windows.Controls.GridViewColumn> 請注意，此示例不定義，<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>因為這樣做會覆蓋 由<xref:System.Windows.DataTemplate>指定的綁定。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>為實作 GridView 的 ListView 設定樣式  
 控制項<xref:System.Windows.Controls.ListView>包含<xref:System.Windows.Controls.ListViewItem>表示顯示的資料項目的物件。 您可以使用下列屬性來定義資料項目的內容和樣式：  
  
- 在控制項<xref:System.Windows.Controls.ListView>上，使用<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>和<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>屬性。  
  
- 在控制項<xref:System.Windows.Controls.ListViewItem>上，使用<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>和<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>屬性。  
  
 為了避免 在<xref:System.Windows.Controls.GridView>的儲存格之間對齊問題，請勿使用<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>來設置 屬性或添加影響 中項寬度的內容<xref:System.Windows.Controls.ListView>。 例如，在 中設置<xref:System.Windows.FrameworkElement.Margin%2A>屬性時，可能會出現對齊問題。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 要指定影響 中項寬度的屬性或定義內容<xref:System.Windows.Controls.GridView>，請使用<xref:System.Windows.Controls.GridView>類及其相關類的屬性，如<xref:System.Windows.Controls.GridViewColumn>。  
  
 有關如何使用<xref:System.Windows.Controls.GridView>及其支援類的詳細資訊，請參閱[GridView 概述](gridview-overview.md)。  
  
 如果<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>為<xref:System.Windows.Controls.ListView>控制項定義 。 ，並且還定義了<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>， 必須在樣式<xref:System.Windows.Controls.ContentPresenter><xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>中包括 。  
  
 不要對使用<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>顯示<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A><xref:System.Windows.Controls.ListView>的內容使用 和 屬性<xref:System.Windows.Controls.GridView>。 要指定 內容在 的列中的對齊方式<xref:System.Windows.Controls.GridView>，請定義<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>。  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>共用相同的檢視模式  
 兩<xref:System.Windows.Controls.ListView>個控制項不能同時共用同一視圖模式。 如果嘗試對多個<xref:System.Windows.Controls.ListView>控制項使用相同的視圖模式，則會發生異常。  
  
 要指定可以由多個<xref:System.Windows.Controls.ListView>多個同時使用的視圖模式，請使用範本或樣式。
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>建立自訂檢視模式  
 自訂視圖如<xref:System.Windows.Controls.GridView>從<xref:System.Windows.Controls.ViewBase>抽象類別派生，它提供了顯示表示為<xref:System.Windows.Controls.ListViewItem>物件的資料項目的工具。
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView 概觀](gridview-overview.md)
- [如何使用主題](listview-how-to-topics.md)
- [控制](../advanced/optimizing-performance-controls.md)
