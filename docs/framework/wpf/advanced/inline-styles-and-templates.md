---
title: "內嵌樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dccf0b274121ff4fe88c9270119a2f631ffcf29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="12e79-102">內嵌樣式和範本</span><span class="sxs-lookup"><span data-stu-id="12e79-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="12e79-103">提供<xref:System.Windows.Style>物件和範本物件 (<xref:System.Windows.FrameworkTemplate>子類別) 做為在資源定義元素的視覺外觀的方式，以便它們可以用於多次。</span><span class="sxs-lookup"><span data-stu-id="12e79-103"> provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="12e79-104">基於這個理由中的屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]可接受型別<xref:System.Windows.Style>和<xref:System.Windows.FrameworkTemplate>幾乎資源參考現有的樣式和範本，而非定義新的內嵌。</span><span class="sxs-lookup"><span data-stu-id="12e79-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="12e79-105">內嵌樣式和範本的限制</span><span class="sxs-lookup"><span data-stu-id="12e79-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="12e79-106">在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、 樣式和樣板屬性技術上可以設定在兩種方式之一。</span><span class="sxs-lookup"><span data-stu-id="12e79-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="12e79-107">您可以使用屬性語法來參考已定義內的資源，例如樣式`<`*物件*`Style="{StaticResource`*myResourceKey*`}" .../>`。</span><span class="sxs-lookup"><span data-stu-id="12e79-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="12e79-108">或者，您可以使用屬性項目語法來定義內嵌樣式，例如：</span><span class="sxs-lookup"><span data-stu-id="12e79-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="12e79-109">`<`*物件*`>`</span><span class="sxs-lookup"><span data-stu-id="12e79-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="12e79-110">`<`*物件*`.Style>`</span><span class="sxs-lookup"><span data-stu-id="12e79-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="12e79-111">`<` `Style`  `.../>`</span><span class="sxs-lookup"><span data-stu-id="12e79-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="12e79-112">`</`*物件*`.Style>`</span><span class="sxs-lookup"><span data-stu-id="12e79-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="12e79-113">`</`*物件*`>`</span><span class="sxs-lookup"><span data-stu-id="12e79-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="12e79-114">屬性使用方式是更加普遍。</span><span class="sxs-lookup"><span data-stu-id="12e79-114">The attribute usage is much more common.</span></span> <span data-ttu-id="12e79-115">為內嵌定義和資源中沒有定義的樣式一定範圍內包含的項目，並不容易重複使用，因為它有沒有資源索引鍵。</span><span class="sxs-lookup"><span data-stu-id="12e79-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="12e79-116">一般情況下的資源定義樣式是更具彈性的且有用的而且比較為了保持一般[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]程式設計模型原則的程式碼邏輯分離標記中的設計。</span><span class="sxs-lookup"><span data-stu-id="12e79-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="12e79-117">通常沒有理由將樣式或範本的內嵌，即使您只想要使用該樣式或範本的位置。</span><span class="sxs-lookup"><span data-stu-id="12e79-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="12e79-118">可以採用樣式或範本的大部分項目也支援內容的屬性和內容模型。</span><span class="sxs-lookup"><span data-stu-id="12e79-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="12e79-119">如果您只使用任何邏輯樹狀結構中一次透過樣式或範本建立，就更容易只 equivalent 子系中的項目直接標記填滿該內容的屬性。</span><span class="sxs-lookup"><span data-stu-id="12e79-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="12e79-120">這會完全略過的樣式和範本機制。</span><span class="sxs-lookup"><span data-stu-id="12e79-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="12e79-121">傳回物件的標記延伸模組所啟用的其他語法是樣式和範本允許的。</span><span class="sxs-lookup"><span data-stu-id="12e79-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="12e79-122">有可能的案例的兩個這類延伸包括[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)和<xref:System.Windows.Data.Binding>。</span><span class="sxs-lookup"><span data-stu-id="12e79-122">Two such extensions that have possible scenarios include [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e79-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="12e79-123">See Also</span></span>  
 [<span data-ttu-id="12e79-124">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="12e79-124">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
