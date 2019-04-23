---
title: HOW TO：指定繫結的方向
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 4334ed178e7f2ed90928db6b434eb8c9fee77bf7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206430"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="678b4-102">HOW TO：指定繫結的方向</span><span class="sxs-lookup"><span data-stu-id="678b4-102">How to: Specify the Direction of the Binding</span></span>
<span data-ttu-id="678b4-103">本範例顯示如何指定繫結只更新繫結目標 (目標) 屬性、繫結來源 (來源) 屬性，或同時更新目標屬性與來源屬性。</span><span class="sxs-lookup"><span data-stu-id="678b4-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="678b4-104">範例</span><span class="sxs-lookup"><span data-stu-id="678b4-104">Example</span></span>  
 <span data-ttu-id="678b4-105">您使用<xref:System.Windows.Data.Binding.Mode%2A>屬性來指定繫結的方向。</span><span class="sxs-lookup"><span data-stu-id="678b4-105">You use the <xref:System.Windows.Data.Binding.Mode%2A> property to specify the direction of the binding.</span></span> <span data-ttu-id="678b4-106">下列列舉清單顯示繫結更新的可用選項：</span><span class="sxs-lookup"><span data-stu-id="678b4-106">The following enumeration list shows the available options for binding updates:</span></span>  
  
-   <span data-ttu-id="678b4-107"><xref:System.Windows.Data.BindingMode.TwoWay> 目標屬性或 [來源] 屬性變更時，請更新目標屬性。</span><span class="sxs-lookup"><span data-stu-id="678b4-107"><xref:System.Windows.Data.BindingMode.TwoWay> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
-   <span data-ttu-id="678b4-108"><xref:System.Windows.Data.BindingMode.OneWay> [來源] 屬性變更時才會更新目標屬性。</span><span class="sxs-lookup"><span data-stu-id="678b4-108"><xref:System.Windows.Data.BindingMode.OneWay> updates the target property only when the source property changes.</span></span>  
  
-   <span data-ttu-id="678b4-109"><xref:System.Windows.Data.BindingMode.OneTime> 更新目標屬性，只有在應用程式啟動時或<xref:System.Windows.FrameworkElement.DataContext%2A>; 歷經變更。</span><span class="sxs-lookup"><span data-stu-id="678b4-109"><xref:System.Windows.Data.BindingMode.OneTime> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
-   <span data-ttu-id="678b4-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> 當目標屬性變更時，請更新來源屬性。</span><span class="sxs-lookup"><span data-stu-id="678b4-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> updates the source property when the target property changes.</span></span>  
  
-   <span data-ttu-id="678b4-111"><xref:System.Windows.Data.BindingMode.Default> 讓預設<xref:System.Windows.Data.Binding.Mode%2A>要使用的目標屬性的值。</span><span class="sxs-lookup"><span data-stu-id="678b4-111"><xref:System.Windows.Data.BindingMode.Default> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="678b4-112">如需詳細資訊，請參閱 <xref:System.Windows.Data.BindingMode> 列舉。</span><span class="sxs-lookup"><span data-stu-id="678b4-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="678b4-113">下列範例會示範如何設定 <xref:System.Windows.Data.Binding.Mode%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="678b4-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="678b4-114">若要偵測來源變更 (適用於<xref:System.Windows.Data.BindingMode.OneWay>並<xref:System.Windows.Data.BindingMode.TwoWay>繫結)，來源必須實作適合的屬性變更通知機制，例如<xref:System.ComponentModel.INotifyPropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="678b4-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="678b4-115">請參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)如需範例的<xref:System.ComponentModel.INotifyPropertyChanged>實作。</span><span class="sxs-lookup"><span data-stu-id="678b4-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="678b4-116">針對<xref:System.Windows.Data.BindingMode.TwoWay>或是<xref:System.Windows.Data.BindingMode.OneWayToSource>繫結，您可以設定來控制來源更新的時機<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="678b4-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="678b4-117">如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>。</span><span class="sxs-lookup"><span data-stu-id="678b4-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="678b4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="678b4-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="678b4-119">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="678b4-119">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="678b4-120">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="678b4-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
