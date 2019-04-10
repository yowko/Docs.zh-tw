---
title: HOW TO：使用範本為使用 GridView 的 ListView 設定樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: 1caa652c4a2a3a7d0a8d40fe703df7a3e8038c9b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147091"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>HOW TO：使用範本為使用 GridView 的 ListView 設定樣式
此範例示範如何使用<xref:System.Windows.DataTemplate>並<xref:System.Windows.Style>物件，以指定的外觀<xref:System.Windows.Controls.ListView>使用的控制項<xref:System.Windows.Controls.GridView>檢視模式。  
  
## <a name="example"></a>範例  
 下列範例所示<xref:System.Windows.Style>並<xref:System.Windows.DataTemplate>物件的自訂資料行標題的外觀<xref:System.Windows.Controls.GridViewColumn>。  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 下列範例示範如何使用這些<xref:System.Windows.Style>並<xref:System.Windows.DataTemplate>設定為<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>並<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>的屬性<xref:System.Windows.Controls.GridViewColumn>。 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性會定義資料行儲存格的內容。  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>並<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>只有兩種數個屬性，您可以使用自訂資料行的標頭外觀<xref:System.Windows.Controls.GridView>控制項。 如需詳細資訊，請參閱 [GridView 資料行標頭樣式和範本概觀](gridview-column-header-styles-and-templates-overview.md)。  
  
 下列範例示範如何定義<xref:System.Windows.DataTemplate>的自訂中的資料格的外觀<xref:System.Windows.Controls.GridViewColumn>。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 下列範例示範如何使用這<xref:System.Windows.DataTemplate>定義的內容<xref:System.Windows.Controls.GridViewColumn>資料格。 而不是使用此範本<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性顯示在上一個<xref:System.Windows.Controls.GridViewColumn>範例。  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [GridView 概觀](gridview-overview.md)
- [HOW TO 主題](listview-how-to-topics.md)
- [ListView 概觀](listview-overview.md)
