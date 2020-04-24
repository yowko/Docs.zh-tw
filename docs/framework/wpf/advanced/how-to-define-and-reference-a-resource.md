---
title: 如何：定義和參考資源
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: e33c86b03d8b18113f3a15b3ab251753958ff5b2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646516"
---
# <a name="how-to-define-and-reference-a-resource"></a><span data-ttu-id="00a32-102">如何：定義和參考資源</span><span class="sxs-lookup"><span data-stu-id="00a32-102">How to: Define and Reference a Resource</span></span>

<span data-ttu-id="00a32-103">此範例簡報如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中的屬性定義資源並引用它。</span><span class="sxs-lookup"><span data-stu-id="00a32-103">This example shows how to define a resource and reference it by using an attribute in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

## <a name="example"></a><span data-ttu-id="00a32-104">範例</span><span class="sxs-lookup"><span data-stu-id="00a32-104">Example</span></span>

<span data-ttu-id="00a32-105">下面的範例定義了兩種類型的資源:一種<xref:System.Windows.Media.SolidColorBrush>資源和<xref:System.Windows.Style>多個資源。</span><span class="sxs-lookup"><span data-stu-id="00a32-105">The following example defines two types of resources: a <xref:System.Windows.Media.SolidColorBrush> resource, and several <xref:System.Windows.Style> resources.</span></span> <span data-ttu-id="00a32-106">該<xref:System.Windows.Media.SolidColorBrush>資源`MyBrush`用於提供每個屬性的值,每個屬性都採用<xref:System.Windows.Media.Brush>類型值。</span><span class="sxs-lookup"><span data-stu-id="00a32-106">The <xref:System.Windows.Media.SolidColorBrush> resource `MyBrush` is used to provide the value of several properties that each take a <xref:System.Windows.Media.Brush> type value.</span></span> <span data-ttu-id="00a32-107">資源和<xref:System.Windows.Style>`PageBackground``TitleText`每個目標為特定的控制`Label`項類型。</span><span class="sxs-lookup"><span data-stu-id="00a32-107">The <xref:System.Windows.Style> resources `PageBackground`, `TitleText` and `Label` each target a particular control type.</span></span> <span data-ttu-id="00a32-108">當資源鍵引用該樣式資源並用於設置<xref:System.Windows.FrameworkElement.Style%2A>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中 定義的多個特定控制項元素的屬性時,樣式在目標控制項上設置各種不同的屬性。</span><span class="sxs-lookup"><span data-stu-id="00a32-108">The styles set a variety of different properties on the targeted controls, when that style resource is referenced by resource key and is used to set the <xref:System.Windows.FrameworkElement.Style%2A> property of several specific control elements defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>

<span data-ttu-id="00a32-109">請注意,`Label`樣式的 setter 中的一個屬性也引用`MyBrush`前面定義的 資源。</span><span class="sxs-lookup"><span data-stu-id="00a32-109">Note that one of the properties within the setters of the `Label` style also references the `MyBrush` resource defined earlier.</span></span> <span data-ttu-id="00a32-110">這是一種常見的技術,但請務必記住,資源按給定順序解析並輸入到資源字典中。</span><span class="sxs-lookup"><span data-stu-id="00a32-110">This is a common technique, but it is important to remember that resources are parsed and entered into a resource dictionary in the order that they are given.</span></span> <span data-ttu-id="00a32-111">如果使用[靜態資源標記擴展](staticresource-markup-extension.md)從其他資源中引用資源,則字典中找到的順序也會請求資源。</span><span class="sxs-lookup"><span data-stu-id="00a32-111">Resources are also requested by the order found within the dictionary if you use the [StaticResource Markup Extension](staticresource-markup-extension.md) to reference them from within another resource.</span></span> <span data-ttu-id="00a32-112">確保引用的任何資源在資源集合中定義的任何資源都早於請求該資源的位置。</span><span class="sxs-lookup"><span data-stu-id="00a32-112">Make sure that any resource that you reference is defined earlier within the resources collection than where that resource is then requested.</span></span> <span data-ttu-id="00a32-113">如有必要,可以使用[動態資源標記擴展](dynamicresource-markup-extension.md)在運行時引用資源,從而繞過資源引用的嚴格創建順序,但您應該知道此動態資源技術具有性能後果。</span><span class="sxs-lookup"><span data-stu-id="00a32-113">If necessary, you can work around the strict creation order of resource references by using a [DynamicResource Markup Extension](dynamicresource-markup-extension.md) to reference the resource at runtime instead, but you should be aware that this DynamicResource technique has performance consequences.</span></span> <span data-ttu-id="00a32-114">有關詳細資訊,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="00a32-114">For details, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a><span data-ttu-id="00a32-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00a32-115">See also</span></span>

- [<span data-ttu-id="00a32-116">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="00a32-116">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="00a32-117">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="00a32-117">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
