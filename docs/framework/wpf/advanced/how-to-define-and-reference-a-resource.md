---
title: HOW TO：定義和參考資源
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 80be1460906100072e6263c967c213df7968c705
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776502"
---
# <a name="how-to-define-and-reference-a-resource"></a><span data-ttu-id="12b04-102">HOW TO：定義和參考資源</span><span class="sxs-lookup"><span data-stu-id="12b04-102">How to: Define and Reference a Resource</span></span>

<span data-ttu-id="12b04-103">此範例示範如何定義資源，並在使用中的屬性中參考此[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12b04-103">This example shows how to define a resource and reference it by using an attribute in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

## <a name="example"></a><span data-ttu-id="12b04-104">範例</span><span class="sxs-lookup"><span data-stu-id="12b04-104">Example</span></span>

<span data-ttu-id="12b04-105">下列範例會定義兩種資源類型：<xref:System.Windows.Media.SolidColorBrush>資源，以及數個<xref:System.Windows.Style>資源。</span><span class="sxs-lookup"><span data-stu-id="12b04-105">The following example defines two types of resources: a <xref:System.Windows.Media.SolidColorBrush> resource, and several <xref:System.Windows.Style> resources.</span></span> <span data-ttu-id="12b04-106"><xref:System.Windows.Media.SolidColorBrush> Resource`MyBrush`用來提供數個屬性的值，每個需要<xref:System.Windows.Media.Brush>輸入值。</span><span class="sxs-lookup"><span data-stu-id="12b04-106">The <xref:System.Windows.Media.SolidColorBrush> resource `MyBrush` is used to provide the value of several properties that each take a <xref:System.Windows.Media.Brush> type value.</span></span> <span data-ttu-id="12b04-107"><xref:System.Windows.Style>資源`PageBackground`，`TitleText`和`Label`每個目標的特定控制項類型。</span><span class="sxs-lookup"><span data-stu-id="12b04-107">The <xref:System.Windows.Style> resources `PageBackground`, `TitleText` and `Label` each target a particular control type.</span></span> <span data-ttu-id="12b04-108">樣式各種不同的屬性上設定的目標控制項，當該樣式資源資源索引鍵所參考，並將用來設定<xref:System.Windows.FrameworkElement.Style%2A>屬性中定義的數個特定的控制項項目[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12b04-108">The styles set a variety of different properties on the targeted controls, when that style resource is referenced by resource key and is used to set the <xref:System.Windows.FrameworkElement.Style%2A> property of several specific control elements defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>

<span data-ttu-id="12b04-109">Setter 內屬性的其中一個筆記`Label`樣式也會參考`MyBrush`稍早定義的資源。</span><span class="sxs-lookup"><span data-stu-id="12b04-109">Note that one of the properties within the setters of the `Label` style also references the `MyBrush` resource defined earlier.</span></span> <span data-ttu-id="12b04-110">這是常用的技巧，但請務必記住，資源會被剖析，並輸入的資源字典中的順序，就會提供。</span><span class="sxs-lookup"><span data-stu-id="12b04-110">This is a common technique, but it is important to remember that resources are parsed and entered into a resource dictionary in the order that they are given.</span></span> <span data-ttu-id="12b04-111">如果您使用，字典中找到的順序也要求資源[StaticResource 標記延伸](staticresource-markup-extension.md)參考從另一個資源內。</span><span class="sxs-lookup"><span data-stu-id="12b04-111">Resources are also requested by the order found within the dictionary if you use the [StaticResource Markup Extension](staticresource-markup-extension.md) to reference them from within another resource.</span></span> <span data-ttu-id="12b04-112">請確定您參考的任何資源稍早定義於其中然後要求該資源的資源集合內。</span><span class="sxs-lookup"><span data-stu-id="12b04-112">Make sure that any resource that you reference is defined earlier within the resources collection than where that resource is then requested.</span></span> <span data-ttu-id="12b04-113">如果有必要，您可以解決的資源參考的嚴格的建立順序使用[DynamicResource 標記延伸](dynamicresource-markup-extension.md)相反地，參考在執行階段的資源，但您應該要注意，此 DynamicResource技術會影響效能。</span><span class="sxs-lookup"><span data-stu-id="12b04-113">If necessary, you can work around the strict creation order of resource references by using a [DynamicResource Markup Extension](dynamicresource-markup-extension.md) to reference the resource at runtime instead, but you should be aware that this DynamicResource technique has performance consequences.</span></span> <span data-ttu-id="12b04-114">如需詳細資訊，請參閱 < [XAML 資源](xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="12b04-114">For details, see [XAML Resources](xaml-resources.md).</span></span>

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a><span data-ttu-id="12b04-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12b04-115">See also</span></span>

- [<span data-ttu-id="12b04-116">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="12b04-116">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="12b04-117">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="12b04-117">Styling and Templating</span></span>](../controls/styling-and-templating.md)
