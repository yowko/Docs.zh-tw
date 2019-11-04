---
title: 如何：定義和參考資源
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 89471c45aabd9f3415c45a2e8af41d1a52900324
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460169"
---
# <a name="how-to-define-and-reference-a-resource"></a><span data-ttu-id="adc5e-102">如何：定義和參考資源</span><span class="sxs-lookup"><span data-stu-id="adc5e-102">How to: Define and Reference a Resource</span></span>

<span data-ttu-id="adc5e-103">這個範例示範如何使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中的屬性，定義資源並加以參考。</span><span class="sxs-lookup"><span data-stu-id="adc5e-103">This example shows how to define a resource and reference it by using an attribute in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

## <a name="example"></a><span data-ttu-id="adc5e-104">範例</span><span class="sxs-lookup"><span data-stu-id="adc5e-104">Example</span></span>

<span data-ttu-id="adc5e-105">下列範例會定義兩種資源類型： <xref:System.Windows.Media.SolidColorBrush> 資源和數個 <xref:System.Windows.Style> 資源。</span><span class="sxs-lookup"><span data-stu-id="adc5e-105">The following example defines two types of resources: a <xref:System.Windows.Media.SolidColorBrush> resource, and several <xref:System.Windows.Style> resources.</span></span> <span data-ttu-id="adc5e-106"><xref:System.Windows.Media.SolidColorBrush> 資源 `MyBrush` 是用來提供數個屬性的值，每個都採用 <xref:System.Windows.Media.Brush> 的類型值。</span><span class="sxs-lookup"><span data-stu-id="adc5e-106">The <xref:System.Windows.Media.SolidColorBrush> resource `MyBrush` is used to provide the value of several properties that each take a <xref:System.Windows.Media.Brush> type value.</span></span> <span data-ttu-id="adc5e-107"><xref:System.Windows.Style> 資源 `PageBackground`、`TitleText` 和 `Label` 各以特定控制項類型為目標。</span><span class="sxs-lookup"><span data-stu-id="adc5e-107">The <xref:System.Windows.Style> resources `PageBackground`, `TitleText` and `Label` each target a particular control type.</span></span> <span data-ttu-id="adc5e-108">樣式會在目標控制項上設定各種不同的屬性，而資源索引鍵會參考該樣式資源，並且用來設定 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中定義之數個特定控制項專案的 <xref:System.Windows.FrameworkElement.Style%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="adc5e-108">The styles set a variety of different properties on the targeted controls, when that style resource is referenced by resource key and is used to set the <xref:System.Windows.FrameworkElement.Style%2A> property of several specific control elements defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>

<span data-ttu-id="adc5e-109">請注意，`Label` 樣式的 setter 中，其中一個屬性也會參考先前定義的 `MyBrush` 資源。</span><span class="sxs-lookup"><span data-stu-id="adc5e-109">Note that one of the properties within the setters of the `Label` style also references the `MyBrush` resource defined earlier.</span></span> <span data-ttu-id="adc5e-110">這是常見的技巧，但請務必記住，資源會依照其指定的順序，進行剖析和輸入至資源字典。</span><span class="sxs-lookup"><span data-stu-id="adc5e-110">This is a common technique, but it is important to remember that resources are parsed and entered into a resource dictionary in the order that they are given.</span></span> <span data-ttu-id="adc5e-111">如果您使用[StaticResource 標記延伸](staticresource-markup-extension.md)從另一個資源中參考，則也會依字典中找到的順序要求資源。</span><span class="sxs-lookup"><span data-stu-id="adc5e-111">Resources are also requested by the order found within the dictionary if you use the [StaticResource Markup Extension](staticresource-markup-extension.md) to reference them from within another resource.</span></span> <span data-ttu-id="adc5e-112">請確定您參考的任何資源都是在資源集合中稍早定義，而不是要求該資源的位置。</span><span class="sxs-lookup"><span data-stu-id="adc5e-112">Make sure that any resource that you reference is defined earlier within the resources collection than where that resource is then requested.</span></span> <span data-ttu-id="adc5e-113">如有需要，您可以使用[DynamicResource 標記延伸](dynamicresource-markup-extension.md)，改為在執行時間參考資源，以解決資源參考的嚴格建立順序，但請注意，此 DynamicResource 技術具有效能後果.</span><span class="sxs-lookup"><span data-stu-id="adc5e-113">If necessary, you can work around the strict creation order of resource references by using a [DynamicResource Markup Extension](dynamicresource-markup-extension.md) to reference the resource at runtime instead, but you should be aware that this DynamicResource technique has performance consequences.</span></span> <span data-ttu-id="adc5e-114">如需詳細資訊，請參閱[XAML 資源](xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="adc5e-114">For details, see [XAML Resources](xaml-resources.md).</span></span>

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a><span data-ttu-id="adc5e-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="adc5e-115">See also</span></span>

- [<span data-ttu-id="adc5e-116">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="adc5e-116">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="adc5e-117">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="adc5e-117">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
