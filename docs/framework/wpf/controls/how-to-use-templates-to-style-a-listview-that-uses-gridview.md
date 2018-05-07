---
title: 如何：使用範本為使用 GridView 的 ListView 設定樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: 481d92d4301401f8ba87c4912cd44b17c5104b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>如何：使用範本為使用 GridView 的 ListView 設定樣式
這個範例示範如何使用<xref:System.Windows.DataTemplate>和<xref:System.Windows.Style>物件，指定的外觀<xref:System.Windows.Controls.ListView>使用控制項<xref:System.Windows.Controls.GridView>檢視模式。  
  
## <a name="example"></a>範例  
 下列範例會顯示<xref:System.Windows.Style>和<xref:System.Windows.DataTemplate>物件可自訂的資料行標頭的外觀<xref:System.Windows.Controls.GridViewColumn>。  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 下列範例示範如何使用這些<xref:System.Windows.Style>和<xref:System.Windows.DataTemplate>物件來設定<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>和<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>屬性<xref:System.Windows.Controls.GridViewColumn>。 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性定義的資料行儲存格的內容。  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>和<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>只有兩種數個屬性，您可以用來自訂資料行的標頭外觀<xref:System.Windows.Controls.GridView>控制項。 如需詳細資訊，請參閱 [GridView 資料行標頭樣式和範本概觀](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)。  
  
 下列範例示範如何定義<xref:System.Windows.DataTemplate>之自訂中的資料格的外觀<xref:System.Windows.Controls.GridViewColumn>。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 下列範例會示範如何使用這個<xref:System.Windows.DataTemplate>來定義的內容<xref:System.Windows.Controls.GridViewColumn>儲存格。 而不是使用此範本<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性顯示在舊版<xref:System.Windows.Controls.GridViewColumn>範例。  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)
