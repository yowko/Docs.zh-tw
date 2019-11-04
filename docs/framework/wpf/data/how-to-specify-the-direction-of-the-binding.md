---
title: 操作說明：指定繫結的方向
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 8f7d843382ee3409047d7cf9549267d582883984
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459100"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="ba35c-102">如何：指定系結的方向</span><span class="sxs-lookup"><span data-stu-id="ba35c-102">How to: Specify the direction of the binding</span></span>

<span data-ttu-id="ba35c-103">本範例顯示如何指定繫結只更新繫結目標 (目標) 屬性、繫結來源 (來源) 屬性，或同時更新目標屬性與來源屬性。</span><span class="sxs-lookup"><span data-stu-id="ba35c-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba35c-104">範例</span><span class="sxs-lookup"><span data-stu-id="ba35c-104">Example</span></span>  
 <span data-ttu-id="ba35c-105">您可以使用 <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> 屬性來指定系結的方向。</span><span class="sxs-lookup"><span data-stu-id="ba35c-105">You use the <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> property to specify the direction of the binding.</span></span> <span data-ttu-id="ba35c-106">以下是可用來系結更新的選項：</span><span class="sxs-lookup"><span data-stu-id="ba35c-106">The following are the available options for binding updates:</span></span>  
  
- <span data-ttu-id="ba35c-107">每當目標屬性或來源屬性變更時，<xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> 會更新目標屬性或屬性。</span><span class="sxs-lookup"><span data-stu-id="ba35c-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
- <span data-ttu-id="ba35c-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> 只有在來源屬性變更時，才會更新目標屬性。</span><span class="sxs-lookup"><span data-stu-id="ba35c-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> updates the target property only when the source property changes.</span></span>  
  
- <span data-ttu-id="ba35c-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> 只有在應用程式啟動或 <xref:System.Windows.FrameworkElement.DataContext%2A> 進行變更時，才會更新目標屬性。</span><span class="sxs-lookup"><span data-stu-id="ba35c-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
- <span data-ttu-id="ba35c-110">當目標屬性變更時，<xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> 更新 source 屬性。</span><span class="sxs-lookup"><span data-stu-id="ba35c-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> updates the source property when the target property changes.</span></span>  
  
- <span data-ttu-id="ba35c-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> 會使用目標屬性的預設 <xref:System.Windows.Data.Binding.Mode%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="ba35c-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="ba35c-112">如需詳細資訊，請參閱 <xref:System.Windows.Data.BindingMode> 列舉。</span><span class="sxs-lookup"><span data-stu-id="ba35c-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="ba35c-113">下列範例會示範如何設定 <xref:System.Windows.Data.Binding.Mode%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ba35c-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="ba35c-114">若要偵測來源變更（適用于 <xref:System.Windows.Data.BindingMode.OneWay> 和 <xref:System.Windows.Data.BindingMode.TwoWay> 系結），來源必須執行適當的屬性變更通知機制，例如 <xref:System.ComponentModel.INotifyPropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="ba35c-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="ba35c-115">如需 <xref:System.ComponentModel.INotifyPropertyChanged> 執行的範例，請參閱[執行屬性變更通知](how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="ba35c-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="ba35c-116">針對 <xref:System.Windows.Data.BindingMode.TwoWay> 或 <xref:System.Windows.Data.BindingMode.OneWayToSource> 系結，您可以藉由設定 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性來控制來源更新的時間。</span><span class="sxs-lookup"><span data-stu-id="ba35c-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="ba35c-117">如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>。</span><span class="sxs-lookup"><span data-stu-id="ba35c-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba35c-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ba35c-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="ba35c-119">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="ba35c-119">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ba35c-120">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="ba35c-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
