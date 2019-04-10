---
title: HOW TO：設定繫結更新的通知
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 4185198312ed98f9aaa1388626600d9f21abae55
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213958"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="b29ad-102">HOW TO：設定繫結更新的通知</span><span class="sxs-lookup"><span data-stu-id="b29ad-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="b29ad-103">本範例顯示如何設定在繫結的繫結目標 (目標) 或繫結來源 (來源) 屬性更新時收到通知。</span><span class="sxs-lookup"><span data-stu-id="b29ad-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b29ad-104">範例</span><span class="sxs-lookup"><span data-stu-id="b29ad-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="b29ad-105">引發資料更新事件，每次已更新的繫結來源或目標。</span><span class="sxs-lookup"><span data-stu-id="b29ad-105">raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="b29ad-106">在內部，此事件是用於通知使用者介面 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 它該更新，因為繫結的資料已經變更。</span><span class="sxs-lookup"><span data-stu-id="b29ad-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="b29ad-107">請注意，這些事件運作，同時也為單向或雙向繫結才能正常運作，需要實作您的資料類別使用<xref:System.ComponentModel.INotifyPropertyChanged>介面。</span><span class="sxs-lookup"><span data-stu-id="b29ad-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="b29ad-108">如需詳細資訊，請參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="b29ad-108">For more information, see [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="b29ad-109">設定<xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>或是<xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>屬性 （或兩者） 來`true`繫結中。</span><span class="sxs-lookup"><span data-stu-id="b29ad-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="b29ad-110">您提供用來接聽此事件的處理常式必須直接附加至您想收到其變更通知的元素，或者，如果您想知道內容中的任何變更，則附加至整體資料內容。</span><span class="sxs-lookup"><span data-stu-id="b29ad-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="b29ad-111">這個範例顯示如何設定在目標屬性更新時收到通知。</span><span class="sxs-lookup"><span data-stu-id="b29ad-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="b29ad-112">接著，您可以根據 EventHandler\<T> 委派 (在此範例中是 *OnTargetUpdated*) 指派處理常式來處理事件：</span><span class="sxs-lookup"><span data-stu-id="b29ad-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="b29ad-113">事件的參數，如型別或特定元素 (若同一處理常式附加至一個或數個元素)，可用來決定已變更之屬性的詳細資訊，如果在單一元素上有數個繫結屬性，這十分有用。</span><span class="sxs-lookup"><span data-stu-id="b29ad-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29ad-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b29ad-114">See also</span></span>

- [<span data-ttu-id="b29ad-115">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="b29ad-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="b29ad-116">HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="b29ad-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
