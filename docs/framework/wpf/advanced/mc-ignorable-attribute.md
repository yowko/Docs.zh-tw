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
ms.openlocfilehash: 7b8a2ef6e27bc6b25776157e59bef04b883fcb1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546194"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="013d2-102">mc:Ignorable 屬性</span><span class="sxs-lookup"><span data-stu-id="013d2-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="013d2-103">指定哪一個[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]標記檔案中遇到的命名空間前置詞可能會略過[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器。</span><span class="sxs-lookup"><span data-stu-id="013d2-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="013d2-104">`mc:Ignorable`屬性支援標記相容性，適用於自訂的命名空間對應和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]版本控制。</span><span class="sxs-lookup"><span data-stu-id="013d2-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="013d2-105">XAML 屬性使用方式 （單一前置詞）</span><span class="sxs-lookup"><span data-stu-id="013d2-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="013d2-106">XAML 屬性使用方式 （兩個前置詞）</span><span class="sxs-lookup"><span data-stu-id="013d2-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="013d2-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="013d2-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="013d2-108">*ignorablePrefix ignorablePrefix1、 等等。*</span><span class="sxs-lookup"><span data-stu-id="013d2-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="013d2-109">任何有效的前置詞字串，根據 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="013d2-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="013d2-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="013d2-110">*ignorableUri*</span></span>|<span data-ttu-id="013d2-111">指定命名空間，根據 XML 1.0 規格的任何有效的 URI。</span><span class="sxs-lookup"><span data-stu-id="013d2-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="013d2-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="013d2-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="013d2-113">項目，可以忽略[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]處理器實作中，如果無法解析的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="013d2-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="013d2-114">備註</span><span class="sxs-lookup"><span data-stu-id="013d2-114">Remarks</span></span>  
 <span data-ttu-id="013d2-115">`mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]命名空間前置詞是用來對應時的建議前置詞慣例[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]相容性命名空間[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="013d2-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="013d2-116">項目或屬性的項目名稱的前置詞部分會識別為`mc:Ignorable`將不會引發錯誤時處理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器。</span><span class="sxs-lookup"><span data-stu-id="013d2-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="013d2-117">如果該屬性無法解析至基礎類型或程式設計建構，則會忽略該元素。</span><span class="sxs-lookup"><span data-stu-id="013d2-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="013d2-118">不過請注意略過的項目仍可能會產生副作用的未處理該元素的其他項目需求的其他剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="013d2-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="013d2-119">比方說，特定項目內容的模型可能需要一個子元素，但如果指定的子項目已在`mc:Ignorable`前置詞和指定的子項目無法解析型別，則[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器可能引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="013d2-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="013d2-120">`mc:Ignorable` 僅適用於命名空間對應的識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="013d2-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="013d2-121">`mc:Ignorable` 不適用於命名空間的對應為組件，指定[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]命名空間和組件 （或在目前的組件的可執行檔的預設值）。</span><span class="sxs-lookup"><span data-stu-id="013d2-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="013d2-122">如果您實作[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器，處理器實作必須不會引發剖析或處理的任何元素或屬性的識別做為前置詞限定的型別解析錯誤`mc:Ignorable`。</span><span class="sxs-lookup"><span data-stu-id="013d2-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="013d2-123">但您的處理器實作仍然可以引發是項目無法載入或處理，例如稍早指定的其中一個子元素範例的第二個結果的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="013d2-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="013d2-124">根據預設，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器將會忽略忽略項目內的內容。</span><span class="sxs-lookup"><span data-stu-id="013d2-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="013d2-125">不過，您可以指定一個額外的屬性[mc:ProcessContent 屬性](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md)、 為需要繼續的處理的下一個可用的父元素所忽略項目內的內容。</span><span class="sxs-lookup"><span data-stu-id="013d2-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="013d2-126">中的屬性，做為分隔符號，例如使用一或多個空格字元，可以指定多個前置詞： `mc:Ignorable="ignore1 ignore2"`。</span><span class="sxs-lookup"><span data-stu-id="013d2-126">Multiple prefixes can be specified in the attribute, using one or more whitespace characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  
  
 <span data-ttu-id="013d2-127">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]命名空間會定義其他的項目和屬性的這個區域中未記載之[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="013d2-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="013d2-128">如需詳細資訊，請參閱[XML 標記相容性規格](http://go.microsoft.com/fwlink/?LinkId=73824)。</span><span class="sxs-lookup"><span data-stu-id="013d2-128">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013d2-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="013d2-129">See Also</span></span>  
 <xref:System.Windows.Markup.XamlReader>  
 [<span data-ttu-id="013d2-130">PresentationOptions:Freeze 屬性</span><span class="sxs-lookup"><span data-stu-id="013d2-130">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [<span data-ttu-id="013d2-131">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="013d2-131">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="013d2-132">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="013d2-132">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
