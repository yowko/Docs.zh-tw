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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104555"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a><span data-ttu-id="df777-102">HOW TO：尋找事件處理常式中的來源項目</span><span class="sxs-lookup"><span data-stu-id="df777-102">How to: Find the Source Element in an Event Handler</span></span>
<span data-ttu-id="df777-103">此範例示範如何尋找來源項目中的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="df777-103">This example shows how to find the source element in an event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df777-104">範例</span><span class="sxs-lookup"><span data-stu-id="df777-104">Example</span></span>  
 <span data-ttu-id="df777-105">下列範例所示<xref:System.Windows.Controls.Primitives.ButtonBase.Click>程式碼後置檔案中所宣告的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="df777-105">The following example shows a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler that is declared in a code-behind file.</span></span> <span data-ttu-id="df777-106">當使用者按一下按鈕處理常式附加至處理常式就會變更屬性值。</span><span class="sxs-lookup"><span data-stu-id="df777-106">When a user clicks the button that the handler is attached to, the handler changes a property value.</span></span> <span data-ttu-id="df777-107">處理常式程式碼會使用<xref:System.Windows.RoutedEventArgs.Source%2A>路由的事件資料變更的事件引數中回報的屬性<xref:System.Windows.FrameworkElement.Width%2A>上的屬性值<xref:System.Windows.RoutedEventArgs.Source%2A>項目。</span><span class="sxs-lookup"><span data-stu-id="df777-107">The handler code uses the <xref:System.Windows.RoutedEventArgs.Source%2A> property of the routed event data that is reported in the event arguments to change the <xref:System.Windows.FrameworkElement.Width%2A> property value on the <xref:System.Windows.RoutedEventArgs.Source%2A> element.</span></span>  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="df777-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df777-108">See also</span></span>

- <xref:System.Windows.RoutedEventArgs>
- [<span data-ttu-id="df777-109">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="df777-109">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="df777-110">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="df777-110">How-to Topics</span></span>](events-how-to-topics.md)
