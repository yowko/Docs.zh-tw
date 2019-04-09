---
title: 內嵌樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b566e157e2d4a9e9be21a678541bf5d5341a898c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091430"
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="1de76-102">內嵌樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1de76-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="1de76-103">提供<xref:System.Windows.Style>物件和範本物件 (<xref:System.Windows.FrameworkTemplate>子類別) 來定義資源中的視覺外觀的項目，以便他們可以使用多次。</span><span class="sxs-lookup"><span data-stu-id="1de76-103">provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="1de76-104">基於這個理由中的屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]會採用型別<xref:System.Windows.Style>和<xref:System.Windows.FrameworkTemplate>幾乎一律讓現有的樣式和範本的資源參考而不是定義新的內嵌。</span><span class="sxs-lookup"><span data-stu-id="1de76-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="1de76-105">內嵌樣式和範本的限制</span><span class="sxs-lookup"><span data-stu-id="1de76-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="1de76-106">在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，技術上可以在下列其中一種設定樣式和範本屬性。</span><span class="sxs-lookup"><span data-stu-id="1de76-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="1de76-107">您可以使用屬性語法來參考定義內的資源，例如樣式`<`*物件*`Style="{StaticResource`*myResourceKey*`}" .../>`。</span><span class="sxs-lookup"><span data-stu-id="1de76-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="1de76-108">或者，您可以使用屬性元素語法來定義內嵌樣式，例如：</span><span class="sxs-lookup"><span data-stu-id="1de76-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 `<` *<span data-ttu-id="1de76-109">object</span><span class="sxs-lookup"><span data-stu-id="1de76-109">object</span></span>* `>`  
  
 `<` *<span data-ttu-id="1de76-110">object</span><span class="sxs-lookup"><span data-stu-id="1de76-110">object</span></span>* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *<span data-ttu-id="1de76-111">object</span><span class="sxs-lookup"><span data-stu-id="1de76-111">object</span></span>* `.Style>`  
  
 `</` *<span data-ttu-id="1de76-112">object</span><span class="sxs-lookup"><span data-stu-id="1de76-112">object</span></span>* `>`  
  
 <span data-ttu-id="1de76-113">屬性使用方式是更為普遍。</span><span class="sxs-lookup"><span data-stu-id="1de76-113">The attribute usage is much more common.</span></span> <span data-ttu-id="1de76-114">是內嵌定義和資源中沒有定義的樣式一定範圍是包含的項目，而且不能容易重複使用，因為它有沒有資源索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1de76-114">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="1de76-115">一般資源所定義的樣式更具彈性且實用，且是基於一般[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]程式設計模型的程式碼中的程式邏輯區分開來標記中的設計的原則。</span><span class="sxs-lookup"><span data-stu-id="1de76-115">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="1de76-116">通常沒有理由將樣式或範本的內嵌，即使您只想要使用該樣式或範本，在該位置。</span><span class="sxs-lookup"><span data-stu-id="1de76-116">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="1de76-117">大部分的項目，可能需要樣式或範本也支援內容的屬性和內容模型。</span><span class="sxs-lookup"><span data-stu-id="1de76-117">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="1de76-118">如果您只使用任何邏輯樹狀結構一次透過樣式或範本建立，它會更輕鬆地只將該內容屬性填入 equivalent 子系中的項目直接的標記。</span><span class="sxs-lookup"><span data-stu-id="1de76-118">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="1de76-119">這會完全略過的樣式和範本機制。</span><span class="sxs-lookup"><span data-stu-id="1de76-119">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="1de76-120">傳回物件的標記延伸模組啟用其他語法也會讓樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="1de76-120">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="1de76-121">包含兩個這類有可能的案例的延伸模組[TemplateBinding](templatebinding-markup-extension.md)和<xref:System.Windows.Data.Binding>。</span><span class="sxs-lookup"><span data-stu-id="1de76-121">Two such extensions that have possible scenarios include [TemplateBinding](templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de76-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1de76-122">See also</span></span>

- [<span data-ttu-id="1de76-123">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="1de76-123">Styling and Templating</span></span>](../controls/styling-and-templating.md)
