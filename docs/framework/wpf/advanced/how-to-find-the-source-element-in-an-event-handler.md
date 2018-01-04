---
title: "如何：尋找事件處理常式中的來源項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d62d657b886b867481088e32fe1dd0614377e146
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>如何：尋找事件處理常式中的來源項目
這個範例示範如何尋找來源項目中的事件處理常式。  
  
## <a name="example"></a>範例  
 下列範例所示<xref:System.Windows.Controls.Primitives.ButtonBase.Click>程式碼後置檔案中所宣告的事件處理常式。 當使用者按一下按鈕處理常式附加至時，此處理常式會變更屬性值。 處理常式程式碼會使用<xref:System.Windows.RoutedEventArgs.Source%2A>屬性中所報告的事件引數來變更路由的事件資料的<xref:System.Windows.FrameworkElement.Width%2A>上的屬性值<xref:System.Windows.RoutedEventArgs.Source%2A>項目。  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.RoutedEventArgs>  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
