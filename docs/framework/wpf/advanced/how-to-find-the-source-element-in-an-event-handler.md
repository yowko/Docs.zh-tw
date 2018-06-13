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
# <a name="how-to-find-the-source-element-in-an-event-handler"></a><span data-ttu-id="8ed93-102">如何：尋找事件處理常式中的來源項目</span><span class="sxs-lookup"><span data-stu-id="8ed93-102">How to: Find the Source Element in an Event Handler</span></span>
<span data-ttu-id="8ed93-103">這個範例示範如何尋找來源項目中的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8ed93-103">This example shows how to find the source element in an event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ed93-104">範例</span><span class="sxs-lookup"><span data-stu-id="8ed93-104">Example</span></span>  
 <span data-ttu-id="8ed93-105">下列範例所示<xref:System.Windows.Controls.Primitives.ButtonBase.Click>程式碼後置檔案中所宣告的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8ed93-105">The following example shows a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler that is declared in a code-behind file.</span></span> <span data-ttu-id="8ed93-106">當使用者按一下按鈕處理常式附加至時，此處理常式會變更屬性值。</span><span class="sxs-lookup"><span data-stu-id="8ed93-106">When a user clicks the button that the handler is attached to, the handler changes a property value.</span></span> <span data-ttu-id="8ed93-107">處理常式程式碼會使用<xref:System.Windows.RoutedEventArgs.Source%2A>屬性中所報告的事件引數來變更路由的事件資料的<xref:System.Windows.FrameworkElement.Width%2A>上的屬性值<xref:System.Windows.RoutedEventArgs.Source%2A>項目。</span><span class="sxs-lookup"><span data-stu-id="8ed93-107">The handler code uses the <xref:System.Windows.RoutedEventArgs.Source%2A> property of the routed event data that is reported in the event arguments to change the <xref:System.Windows.FrameworkElement.Width%2A> property value on the <xref:System.Windows.RoutedEventArgs.Source%2A> element.</span></span>  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="8ed93-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ed93-108">See Also</span></span>  
 <xref:System.Windows.RoutedEventArgs>  
 [<span data-ttu-id="8ed93-109">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="8ed93-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="8ed93-110">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="8ed93-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
