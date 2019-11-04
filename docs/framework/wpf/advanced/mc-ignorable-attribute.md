---
title: mc:Ignorable 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: d8fdeec8784c9a44c9b272a0a5a8b9c56ace5230
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458825"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="38e0e-102">mc:Ignorable 屬性</span><span class="sxs-lookup"><span data-stu-id="38e0e-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="38e0e-103">指定 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器可以忽略標記檔案中發現的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="38e0e-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="38e0e-104">`mc:Ignorable` 屬性支援自訂命名空間對應和 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 版本設定的標記相容性。</span><span class="sxs-lookup"><span data-stu-id="38e0e-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="38e0e-105">XAML 屬性使用方式（單一前置詞）</span><span class="sxs-lookup"><span data-stu-id="38e0e-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="38e0e-106">XAML 屬性使用方式（兩個首碼）</span><span class="sxs-lookup"><span data-stu-id="38e0e-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```xaml  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="38e0e-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="38e0e-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38e0e-108">*ignorablePrefix、ignorablePrefix1 等等。*</span><span class="sxs-lookup"><span data-stu-id="38e0e-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="38e0e-109">任何有效的前置字串，依據 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="38e0e-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="38e0e-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="38e0e-110">*ignorableUri*</span></span>|<span data-ttu-id="38e0e-111">根據 XML 1.0 規格，指定命名空間的任何有效 URI。</span><span class="sxs-lookup"><span data-stu-id="38e0e-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="38e0e-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="38e0e-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="38e0e-113">如果無法解析基礎類型，則 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 處理器實作為可以忽略的元素。</span><span class="sxs-lookup"><span data-stu-id="38e0e-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38e0e-114">備註</span><span class="sxs-lookup"><span data-stu-id="38e0e-114">Remarks</span></span>  
 <span data-ttu-id="38e0e-115">`mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間前置詞是對應 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 相容性命名空間 `http://schemas.openxmlformats.org/markup-compatibility/2006`時所使用的建議前置詞慣例。</span><span class="sxs-lookup"><span data-stu-id="38e0e-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace `http://schemas.openxmlformats.org/markup-compatibility/2006`.</span></span>  
  
 <span data-ttu-id="38e0e-116">元素或屬性，其中專案名稱的前置詞部分會識別為 `mc:Ignorable` 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器處理時不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="38e0e-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="38e0e-117">如果該屬性無法解析成基礎類型或程式設計結構，則會忽略該元素。</span><span class="sxs-lookup"><span data-stu-id="38e0e-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="38e0e-118">不過，請注意，忽略的元素仍然可能針對該專案未處理的其他專案需求，產生額外的剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="38e0e-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="38e0e-119">例如，特定專案內容模型可能只需要一個子專案，但如果指定的子專案是在 `mc:Ignorable` 前置詞中，而指定的子專案無法解析成型別，則 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的處理器可能會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="38e0e-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="38e0e-120">`mc:Ignorable` 只適用于命名空間對應至識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="38e0e-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="38e0e-121">`mc:Ignorable` 不會套用至元件中的命名空間對應，這會指定 CLR 命名空間和元件（或預設為目前可執行檔做為元件）。</span><span class="sxs-lookup"><span data-stu-id="38e0e-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a CLR namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="38e0e-122">如果您要執行 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器，則您的處理器執行不能針對識別為 `mc:Ignorable`的前置詞所限定的任何元素或屬性，在類型解析上引發剖析或處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="38e0e-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="38e0e-123">但是，您的處理器執行仍然可以引發無法載入或處理之元素的次要結果的例外狀況，例如先前指定的一個子項目範例。</span><span class="sxs-lookup"><span data-stu-id="38e0e-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="38e0e-124">根據預設，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的處理器會忽略忽略專案中的內容。</span><span class="sxs-lookup"><span data-stu-id="38e0e-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="38e0e-125">不過，您可以指定其他屬性[mc： ProcessContent 屬性](mc-processcontent-attribute.md)，以要求在下一個可用的父元素中繼續處理忽略專案內的內容。</span><span class="sxs-lookup"><span data-stu-id="38e0e-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="38e0e-126">您可以在屬性中指定多個前置詞，使用一或多個空白字元做為分隔符號，例如： `mc:Ignorable="ignore1 ignore2"`。</span><span class="sxs-lookup"><span data-stu-id="38e0e-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="38e0e-127">`http://schemas.openxmlformats.org/markup-compatibility/2006` 命名空間會定義在 SDK 的這個區域中未記載的其他元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="38e0e-127">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="38e0e-128">如需詳細資訊，請參閱[XML 標記相容性規格](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification)。</span><span class="sxs-lookup"><span data-stu-id="38e0e-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e0e-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="38e0e-129">See also</span></span>

- <xref:System.Windows.Markup.XamlReader>
- [<span data-ttu-id="38e0e-130">PresentationOptions:Freeze 屬性</span><span class="sxs-lookup"><span data-stu-id="38e0e-130">PresentationOptions:Freeze Attribute</span></span>](presentationoptions-freeze-attribute.md)
- [<span data-ttu-id="38e0e-131">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="38e0e-131">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="38e0e-132">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="38e0e-132">Documents in WPF</span></span>](documents-in-wpf.md)
