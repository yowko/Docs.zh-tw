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
ms.openlocfilehash: e8fa4c084ae9c775a18de06c344b2c0b439c2b1b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517357"
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="767a6-102">mc:Ignorable 屬性</span><span class="sxs-lookup"><span data-stu-id="767a6-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="767a6-103">指定哪些[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]標記檔案中遇到的命名空間前置詞可能會忽略[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器。</span><span class="sxs-lookup"><span data-stu-id="767a6-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="767a6-104">`mc:Ignorable`屬性支援標記相容性，以及自訂的命名空間對應性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]版本控制。</span><span class="sxs-lookup"><span data-stu-id="767a6-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="767a6-105">XAML 屬性使用方式 （單一前置詞）</span><span class="sxs-lookup"><span data-stu-id="767a6-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="767a6-106">XAML 屬性使用方式 （兩個前置詞）</span><span class="sxs-lookup"><span data-stu-id="767a6-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="767a6-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="767a6-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="767a6-108">*ignorablePrefix ignorablePrefix1、 等等。*</span><span class="sxs-lookup"><span data-stu-id="767a6-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="767a6-109">任何有效的前置詞字串，根據 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="767a6-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="767a6-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="767a6-110">*ignorableUri*</span></span>|<span data-ttu-id="767a6-111">對指定的命名空間，根據 XML 1.0 規格任何有效的 URI。</span><span class="sxs-lookup"><span data-stu-id="767a6-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="767a6-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="767a6-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="767a6-113">項目，可以忽略[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]處理器實作中，如果無法解析的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="767a6-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="767a6-114">備註</span><span class="sxs-lookup"><span data-stu-id="767a6-114">Remarks</span></span>  
 <span data-ttu-id="767a6-115">`mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]命名空間前置詞會使用對應時的建議前置詞慣例[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]相容性命名空間[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="767a6-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="767a6-116">項目或屬性的項目名稱的前置詞部分會識別為`mc:Ignorable`將不會引發錯誤時由處理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器。</span><span class="sxs-lookup"><span data-stu-id="767a6-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="767a6-117">如果該屬性不可以解析為基礎的型別或程式設計建構，則會忽略該元素。</span><span class="sxs-lookup"><span data-stu-id="767a6-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="767a6-118">不過請注意，已忽略的項目可能還是會產生副作用不處理該項目的的其他項目需求的其他剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="767a6-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="767a6-119">例如，特定項目內容的模型可能需要只有一個子項目，但指定的子項目是否在`mc:Ignorable`前置詞和指定的子項目無法解析型別，則[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器可能引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="767a6-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="767a6-120">`mc:Ignorable` 僅適用於命名空間對應到識別項字串。</span><span class="sxs-lookup"><span data-stu-id="767a6-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="767a6-121">`mc:Ignorable` 不會套用到命名空間對應至組件，指定[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]命名空間和組件 （或與組件的目前可執行檔的預設值）。</span><span class="sxs-lookup"><span data-stu-id="767a6-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="767a6-122">如果您要實作[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器，處理器實作必須引發剖析或處理的任何項目或屬性，以識別為前置詞來限定的型別解析錯誤`mc:Ignorable`。</span><span class="sxs-lookup"><span data-stu-id="767a6-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="767a6-123">但您的處理器實作仍會引發例外狀況是次要的項目，無法載入或處理，如稍早指定的其中一個子元素範例的結果。</span><span class="sxs-lookup"><span data-stu-id="767a6-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="767a6-124">根據預設，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器將會忽略已忽略的項目內的內容。</span><span class="sxs-lookup"><span data-stu-id="767a6-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="767a6-125">不過，您可以指定一個額外的屬性[mc: processcontent 屬性](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md)，需要繼續的處理下一個可用的父元素所忽略的元素內的內容。</span><span class="sxs-lookup"><span data-stu-id="767a6-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="767a6-126">可以指定多個前置詞，在屬性中，使用一或多個空格字元作為分隔符號，例如： `mc:Ignorable="ignore1 ignore2"`。</span><span class="sxs-lookup"><span data-stu-id="767a6-126">Multiple prefixes can be specified in the attribute, using one or more white-space characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  

 <span data-ttu-id="767a6-127">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]命名空間會定義其他項目和屬性的這個區域中未記載之[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="767a6-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="767a6-128">如需詳細資訊，請參閱 < [XML 標記相容性規格](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification)。</span><span class="sxs-lookup"><span data-stu-id="767a6-128">For more information, see [XML Markup Compatibility Specification](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="767a6-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="767a6-129">See Also</span></span>  
 <xref:System.Windows.Markup.XamlReader>  
 [<span data-ttu-id="767a6-130">PresentationOptions:Freeze 屬性</span><span class="sxs-lookup"><span data-stu-id="767a6-130">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [<span data-ttu-id="767a6-131">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="767a6-131">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="767a6-132">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="767a6-132">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
