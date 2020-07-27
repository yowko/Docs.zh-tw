---
title: ListView 概觀
description: 瞭解 Windows Presentation Foundation ListView 控制項，其可提供基礎結構，以在不同的版面配置或視圖中顯示資料項目。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 419c6216f0af696ec71e7607c79c2db637caa785
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164555"
---
# <a name="listview-overview"></a>ListView 概觀
<xref:System.Windows.Controls.ListView>控制項會提供基礎結構，以在不同的版面配置或視圖中顯示一組資料項目。 例如，使用者可能會想要以表格顯示資料項目，還要排序其資料行。  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>什麼是 ListView？  
 <xref:System.Windows.Controls.ListView>控制項是 <xref:System.Windows.Controls.ItemsControl> 衍生自的 <xref:System.Windows.Controls.ListBox> 。 通常，其專案為資料集合的成員，並以物件表示 <xref:System.Windows.Controls.ListViewItem> 。 <xref:System.Windows.Controls.ListViewItem>是 <xref:System.Windows.Controls.ContentControl> ，而且只能包含單一子項目。 不過，該子元素可以是任何視覺元素。  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>定義 ListView 的檢視模式  
 若要指定控制項內容的視圖模式 <xref:System.Windows.Controls.ListView> ，請設定 <xref:System.Windows.Controls.ListView.View%2A> 屬性。 提供的一個 view 模式 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 是 <xref:System.Windows.Controls.GridView> ，它會在具有可自訂資料行的資料表中顯示資料項目的集合。  
  
 下列範例示範如何為 <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView> 顯示員工資訊的控制項定義。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示上一個範例的資料顯示方式。  
  
 ![顯示具有 GridView 輸出之 ListView 的螢幕擷取畫面。](./media/gridview-overview/listview-gridview-output.jpg)  
  
 您可以藉由定義繼承自類別的類別來建立自訂視圖模式 <xref:System.Windows.Controls.ViewBase> 。 <xref:System.Windows.Controls.ViewBase>類別會提供建立自訂視圖所需的基礎結構。 如需有關如何建立自訂檢視的詳細資訊，請參閱[建立 ListView 的自訂檢視模式](how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>將資料繫結至 ListView  
 您 <xref:System.Windows.Controls.ItemsControl.Items%2A> 可以使用和 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性來指定控制項的專案 <xref:System.Windows.Controls.ListView> 。 下列範例 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 會將屬性設定為所呼叫的資料集合 `EmployeeInfoDataSource` 。  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 在中 <xref:System.Windows.Controls.GridView> ，物件會系結 <xref:System.Windows.Controls.GridViewColumn> 至指定的資料欄位。 下列範例會藉由指定屬性的來將物件系結 <xref:System.Windows.Controls.GridViewColumn> 至資料欄位 <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 。  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 您也可以將指定 <xref:System.Windows.Data.Binding> 為 <xref:System.Windows.DataTemplate> 定義的一部分，以用來將資料行中的儲存格樣式。 在下列範例中， <xref:System.Windows.DataTemplate> 使用所識別的會設定的 <xref:System.Windows.ResourceKey> <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn> 。 請注意，此範例不會定義， <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 因為這樣做會覆寫所指定的系結 <xref:System.Windows.DataTemplate> 。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>為實作 GridView 的 ListView 設定樣式  
 <xref:System.Windows.Controls.ListView>控制項包含 <xref:System.Windows.Controls.ListViewItem> 物件，代表顯示的資料項目。 您可以使用下列屬性來定義資料項目的內容和樣式：  
  
- 在 <xref:System.Windows.Controls.ListView> 控制項上，使用 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 、 <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 屬性。  
  
- 在 <xref:System.Windows.Controls.ListViewItem> 控制項上，使用 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 和 <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> 屬性。  
  
 若要避免在中的資料格之間對齊問題 <xref:System.Windows.Controls.GridView> ，請勿使用 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 來設定屬性，或加入會影響中專案寬度的內容 <xref:System.Windows.Controls.ListView> 。 例如，當您在中設定屬性時，可能會發生對齊問題 <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 。 若要指定屬性或定義會影響中專案寬度的內容 <xref:System.Windows.Controls.GridView> ，請使用類別的屬性 <xref:System.Windows.Controls.GridView> 及其相關類別，例如 <xref:System.Windows.Controls.GridViewColumn> 。  
  
 如需如何使用 <xref:System.Windows.Controls.GridView> 及其支援類別的詳細資訊，請參閱[GridView 總覽](gridview-overview.md)。  
  
 如果您 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 為 <xref:System.Windows.Controls.ListView> 控制項定義，並同時定義 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> ，則必須在樣式中包含，才能 <xref:System.Windows.Controls.ContentPresenter> 讓正常 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 運作。  
  
 請不要 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> 針對使用所顯示的內容使用和屬性 <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.GridView> 。 若要指定資料行中內容的對齊方式 <xref:System.Windows.Controls.GridView> ，請定義 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> 。  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>共用相同的檢視模式  
 兩個 <xref:System.Windows.Controls.ListView> 控制項不能同時共用相同的視圖模式。 如果您嘗試使用與多個控制項相同的 view 模式 <xref:System.Windows.Controls.ListView> ，就會發生例外狀況。  
  
 若要指定可同時由多個使用的視圖模式 <xref:System.Windows.Controls.ListView> ，請使用範本或樣式。
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>建立自訂檢視模式  
 之類的自訂視圖 <xref:System.Windows.Controls.GridView> 衍生自 <xref:System.Windows.Controls.ViewBase> 抽象類別，它提供工具來顯示以物件表示的資料項目 <xref:System.Windows.Controls.ListViewItem> 。
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView 概觀](gridview-overview.md)
- [操作說明主題](listview-how-to-topics.md)
- [控制項](../advanced/optimizing-performance-controls.md)
