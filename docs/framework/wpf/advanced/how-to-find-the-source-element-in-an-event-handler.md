---
title: 如何：尋找事件處理常式中的來源項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: c3ae893cd7fd7780854d6eb6ffd682feadb5c5a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543996"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>如何：尋找事件處理常式中的來源項目
這個範例示範如何尋找來源項目中的事件處理常式。  
  
## <a name="example"></a>範例  
 下列範例所示<xref:System.Windows.Controls.Primitives.ButtonBase.Click>程式碼後置檔案中所宣告的事件處理常式。 當使用者按一下按鈕處理常式附加至時，此處理常式會變更屬性值。 處理常式程式碼會使用<xref:System.Windows.RoutedEventArgs.Source%2A>屬性中所報告的事件引數來變更路由的事件資料的<xref:System.Windows.FrameworkElement.Width%2A>上的屬性值<xref:System.Windows.RoutedEventArgs.Source%2A>項目。  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.RoutedEventArgs>  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
