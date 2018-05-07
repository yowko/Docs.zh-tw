---
title: 如何：尋找 DataTemplate 產生的項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
ms.openlocfilehash: d46a408bc1b5fc512905aa5bf176b13bd1511865
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-datatemplate-generated-elements"></a>如何：尋找 DataTemplate 產生的項目
這個範例示範如何尋找所產生的項目<xref:System.Windows.DataTemplate>。  
  
## <a name="example"></a>範例  
 在此範例中，沒有<xref:System.Windows.Controls.ListBox>某些繫結[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料：  
  
 [!code-xaml[FindGeneratedItems#LB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox>會使用下列<xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 如果您想要擷取<xref:System.Windows.Controls.TextBlock>所產生的項目<xref:System.Windows.DataTemplate>某些<xref:System.Windows.Controls.ListBoxItem>，您需要取得<xref:System.Windows.Controls.ListBoxItem>，尋找<xref:System.Windows.Controls.ContentPresenter>在<xref:System.Windows.Controls.ListBoxItem>，然後呼叫<xref:System.Windows.FrameworkTemplate.FindName%2A>上<xref:System.Windows.DataTemplate>上的設定<xref:System.Windows.Controls.ContentPresenter>。 下列範例會示範如何執行這些步驟。 針對示範用途，此範例會建立一個訊息方塊，顯示的文字內容的<xref:System.Windows.DataTemplate>-產生的文字區塊。  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 以下是實作`FindVisualChild`，它會使用<xref:System.Windows.Media.VisualTreeHelper>方法：  
  
 [!code-csharp[FindGeneratedItems#FVC](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：尋找 ControlTemplate 產生的元素](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [WPF XAML 名稱範圍](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
