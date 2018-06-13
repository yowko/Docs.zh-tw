---
title: 如何：定義和參考資源
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 347804f0ce6dd3b907d3ac088248a64569a63695
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543490"
---
# <a name="how-to-define-and-reference-a-resource"></a><span data-ttu-id="5d430-102">如何：定義和參考資源</span><span class="sxs-lookup"><span data-stu-id="5d430-102">How to: Define and Reference a Resource</span></span>
<span data-ttu-id="5d430-103">這個範例示範如何定義資源，並使用中的屬性來參考該[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d430-103">This example shows how to define a resource and reference it by using an attribute in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d430-104">範例</span><span class="sxs-lookup"><span data-stu-id="5d430-104">Example</span></span>  
 <span data-ttu-id="5d430-105">下列範例會定義兩種資源類型：<xref:System.Windows.Media.SolidColorBrush>資源，以及數個<xref:System.Windows.Style>資源。</span><span class="sxs-lookup"><span data-stu-id="5d430-105">The following example defines two types of resources: a <xref:System.Windows.Media.SolidColorBrush> resource, and several <xref:System.Windows.Style> resources.</span></span> <span data-ttu-id="5d430-106"><xref:System.Windows.Media.SolidColorBrush>資源`MyBrush`用來提供數個屬性的值，每個接受<xref:System.Windows.Media.Brush>輸入值。</span><span class="sxs-lookup"><span data-stu-id="5d430-106">The <xref:System.Windows.Media.SolidColorBrush> resource `MyBrush` is used to provide the value of several properties that each take a <xref:System.Windows.Media.Brush> type value.</span></span> <span data-ttu-id="5d430-107"><xref:System.Windows.Style>資源`PageBackground`，`TitleText`和`Label`每個目標特定控制項類型。</span><span class="sxs-lookup"><span data-stu-id="5d430-107">The <xref:System.Windows.Style> resources `PageBackground`, `TitleText` and `Label` each target a particular control type.</span></span> <span data-ttu-id="5d430-108">樣式的各種不同的屬性時上設定目標的控制項，該樣式資源資源索引鍵所參考，且用來設定<xref:System.Windows.FrameworkElement.Style%2A>數個特定的控制項項目中定義的屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d430-108">The styles set a variety of different properties on the targeted controls, when that style resource is referenced by resource key and is used to set the <xref:System.Windows.FrameworkElement.Style%2A> property of several specific control elements defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="5d430-109">中的 setter 屬性的一個附註`Label`樣式也會參考`MyBrush`先前定義的資源。</span><span class="sxs-lookup"><span data-stu-id="5d430-109">Note that one of the properties within the setters of the `Label` style also references the `MyBrush` resource defined earlier.</span></span> <span data-ttu-id="5d430-110">這是常見的技術，但請務必記住，資源會剖析並輸入的資源字典中指定的順序。</span><span class="sxs-lookup"><span data-stu-id="5d430-110">This is a common technique, but it is important to remember that resources are parsed and entered into a resource dictionary in the order that they are given.</span></span> <span data-ttu-id="5d430-111">如果您使用字典中找到的順序也要求資源[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)參考從另一個資源內。</span><span class="sxs-lookup"><span data-stu-id="5d430-111">Resources are also requested by the order found within the dictionary if you use the [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) to reference them from within another resource.</span></span> <span data-ttu-id="5d430-112">請確定您參考的任何資源先前定義的資源集合比該資源都在要求中。</span><span class="sxs-lookup"><span data-stu-id="5d430-112">Make sure that any resource that you reference is defined earlier within the resources collection than where that resource is then requested.</span></span> <span data-ttu-id="5d430-113">如果有必要，您可以解決的資源 refererences 嚴格的建立順序使用[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)相反地，參考這個資源，在執行階段，但您應該注意，此 DynamicResource方法會影響效能。</span><span class="sxs-lookup"><span data-stu-id="5d430-113">If necessary, you can work around the strict creation order of resource refererences by using a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) to reference the resource at runtime instead, but you should be aware that this DynamicResource technique has performance consequences.</span></span> <span data-ttu-id="5d430-114">如需詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="5d430-114">For details, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a><span data-ttu-id="5d430-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d430-115">See Also</span></span>  
 [<span data-ttu-id="5d430-116">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="5d430-116">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="5d430-117">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="5d430-117">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
