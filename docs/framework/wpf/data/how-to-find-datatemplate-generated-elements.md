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
ms.openlocfilehash: 3b222880aa4eda32502e3dcece2fa5c0b57b7a51
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646426"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>如何：尋找 DataTemplate 產生的項目
此範例展示如何尋找建立的元素<xref:System.Windows.DataTemplate>。  
  
## <a name="example"></a>範例  
 這個樣本範例中,有綁定到<xref:System.Windows.Controls.ListBox>某些 XML 資料的 a:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 使用<xref:System.Windows.Controls.ListBox>以下內容<xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 如果要檢查<xref:System.Windows.Controls.TextBlock>索<xref:System.Windows.DataTemplate>由某一<xref:System.Windows.Controls.ListBoxItem><xref:System.Windows.Controls.ListBoxItem>元素 產生的元素,則需要取得<xref:System.Windows.Controls.ContentPresenter>,<xref:System.Windows.Controls.ListBoxItem>請找到內部的元素<xref:System.Windows.FrameworkTemplate.FindName%2A><xref:System.Windows.DataTemplate>,然後呼叫<xref:System.Windows.Controls.ContentPresenter>上設定的元素 。 下面的示例演示如何執行這些步驟。 出於展示目的,此範例創建一個顯示<xref:System.Windows.DataTemplate>生成的文本塊的文本內容的消息框。  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 以下是的實`FindVisualChild`作<xref:System.Windows.Media.VisualTreeHelper>, 它使用這些方法:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>另請參閱

- [操作說明：尋找 ControlTemplate 產生的元素](../controls/how-to-find-controltemplate-generated-elements.md)
- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [如何主題](data-binding-how-to-topics.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [WPF XAML 名稱範圍](../advanced/wpf-xaml-namescopes.md)
- [WPF 中的樹狀結構](../advanced/trees-in-wpf.md)
