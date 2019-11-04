---
title: 內嵌樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b88ef444283f4e1e85009c59b39f3cc41965d300
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460000"
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="8c205-102">內嵌樣式和範本</span><span class="sxs-lookup"><span data-stu-id="8c205-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="8c205-103">提供 <xref:System.Windows.Style> 物件和樣板物件（<xref:System.Windows.FrameworkTemplate> 子類別）做為在資源中定義元素視覺外觀的方式，讓它們可以多次使用。</span><span class="sxs-lookup"><span data-stu-id="8c205-103">provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="8c205-104">基於這個理由，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中採用類型 <xref:System.Windows.Style> 和 <xref:System.Windows.FrameworkTemplate> 的屬性，幾乎一律會對現有的樣式和範本進行資源參考，而不是以內嵌方式定義新的。</span><span class="sxs-lookup"><span data-stu-id="8c205-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="8c205-105">內嵌樣式和範本的限制</span><span class="sxs-lookup"><span data-stu-id="8c205-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="8c205-106">在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，樣式和範本屬性可以透過兩種方式的其中一種來設定。</span><span class="sxs-lookup"><span data-stu-id="8c205-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="8c205-107">您可以使用屬性語法來參考資源內所定義的樣式，例如 `<`*物件*`Style="{StaticResource`*myResourceKey*`}" .../>`。</span><span class="sxs-lookup"><span data-stu-id="8c205-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="8c205-108">或者，您可以使用屬性專案語法來定義內嵌樣式，例如：</span><span class="sxs-lookup"><span data-stu-id="8c205-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="8c205-109">`<`*物件*`>`</span><span class="sxs-lookup"><span data-stu-id="8c205-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="8c205-110">`<`*物件*`.Style>`</span><span class="sxs-lookup"><span data-stu-id="8c205-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="8c205-111">`<` `Style``.../>`</span><span class="sxs-lookup"><span data-stu-id="8c205-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="8c205-112">`</`*物件*`.Style>`</span><span class="sxs-lookup"><span data-stu-id="8c205-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="8c205-113">`</`*物件*`>`</span><span class="sxs-lookup"><span data-stu-id="8c205-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="8c205-114">屬性使用方式更為常見。</span><span class="sxs-lookup"><span data-stu-id="8c205-114">The attribute usage is much more common.</span></span> <span data-ttu-id="8c205-115">在資源中定義為內嵌且未定義的樣式，必須僅限於包含元素，而且因為沒有資源索引鍵，所以無法重複使用。</span><span class="sxs-lookup"><span data-stu-id="8c205-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="8c205-116">一般而言，資源定義的樣式更具彈性且有用，而且更符合一般 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 程式設計模型原則，這是在程式碼中將程式邏輯與標記中的設計分隔開來。</span><span class="sxs-lookup"><span data-stu-id="8c205-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="8c205-117">通常不需要設定樣式或範本內嵌，即使您只想要在該位置使用該樣式或範本也一樣。</span><span class="sxs-lookup"><span data-stu-id="8c205-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="8c205-118">大部分可接受樣式或範本的專案也都支援內容屬性和內容模型。</span><span class="sxs-lookup"><span data-stu-id="8c205-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="8c205-119">如果您只使用透過樣式設定或範本化所建立的任何邏輯樹狀結構，則只需要在直接標記中使用對等的子項目來填入該內容屬性，會變得更容易。</span><span class="sxs-lookup"><span data-stu-id="8c205-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="8c205-120">這會完全略過樣式和範本機制。</span><span class="sxs-lookup"><span data-stu-id="8c205-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="8c205-121">針對樣式和範本，也可能由傳回物件的標記延伸所啟用的其他語法。</span><span class="sxs-lookup"><span data-stu-id="8c205-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="8c205-122">具有可能案例的兩個這類延伸模組，包括[TemplateBinding](templatebinding-markup-extension.md)和 <xref:System.Windows.Data.Binding>。</span><span class="sxs-lookup"><span data-stu-id="8c205-122">Two such extensions that have possible scenarios include [TemplateBinding](templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c205-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="8c205-123">See also</span></span>

- [<span data-ttu-id="8c205-124">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="8c205-124">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
