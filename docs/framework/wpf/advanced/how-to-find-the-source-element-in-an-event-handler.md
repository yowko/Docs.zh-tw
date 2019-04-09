---
title: HOW TO：尋找事件處理常式中的來源項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: 9a49878c9ad8313903df4506796998fd43e2e749
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104555"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>HOW TO：尋找事件處理常式中的來源項目
此範例示範如何尋找來源項目中的事件處理常式。  
  
## <a name="example"></a>範例  
 下列範例所示<xref:System.Windows.Controls.Primitives.ButtonBase.Click>程式碼後置檔案中所宣告的事件處理常式。 當使用者按一下按鈕處理常式附加至處理常式就會變更屬性值。 處理常式程式碼會使用<xref:System.Windows.RoutedEventArgs.Source%2A>路由的事件資料變更的事件引數中回報的屬性<xref:System.Windows.FrameworkElement.Width%2A>上的屬性值<xref:System.Windows.RoutedEventArgs.Source%2A>項目。  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.RoutedEventArgs>
- [路由事件概觀](routed-events-overview.md)
- [HOW TO 主題](events-how-to-topics.md)
