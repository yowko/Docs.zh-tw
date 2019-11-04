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
ms.openlocfilehash: f9265e3f7b287e1e8c264e89325f7c9649eebe2c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459140"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>如何：尋找 DataTemplate 產生的項目
這個範例會示範如何尋找 <xref:System.Windows.DataTemplate>所產生的元素。  
  
## <a name="example"></a>範例  
 在此範例中，有一個 <xref:System.Windows.Controls.ListBox> 系結至某些 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料：  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> 使用下列 <xref:System.Windows.DataTemplate>：  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 如果您想要取出特定 <xref:System.Windows.Controls.ListBoxItem>的 <xref:System.Windows.DataTemplate> 所產生的 <xref:System.Windows.Controls.TextBlock> 專案，您需要取得 <xref:System.Windows.Controls.ListBoxItem>、在該 <xref:System.Windows.Controls.ContentPresenter> 內尋找 <xref:System.Windows.Controls.ListBoxItem>，然後在設定的 <xref:System.Windows.FrameworkTemplate.FindName%2A> 上呼叫 <xref:System.Windows.DataTemplate><xref:System.Windows.Controls.ContentPresenter>。 下列範例顯示如何執行這些步驟。 基於示範目的，此範例會建立訊息方塊，以顯示 <xref:System.Windows.DataTemplate>產生之文字區塊的文字內容。  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 以下是使用 <xref:System.Windows.Media.VisualTreeHelper> 方法的 `FindVisualChild`的執行：  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>請參閱

- [操作說明：尋找 ControlTemplate 產生的元素](../controls/how-to-find-controltemplate-generated-elements.md)
- [資料繫結概觀](data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [WPF XAML 名稱範圍](../advanced/wpf-xaml-namescopes.md)
- [WPF 中的樹狀結構](../advanced/trees-in-wpf.md)
