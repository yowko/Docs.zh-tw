---
title: "mc:ProcessContent 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aaf83fe66d5367d5e51428cb8f35aa88c12c9c39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="22998-102">mc:ProcessContent 屬性</span><span class="sxs-lookup"><span data-stu-id="22998-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="22998-103">指定哪一個[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目仍應該內容相關的父項目處理，即使直屬父項目可能會略過[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]因為指定的處理器[mc: Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="22998-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span></span> <span data-ttu-id="22998-104">`mc:ProcessContent`屬性支援標記相容性，適用於自訂的命名空間對應和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]版本控制。</span><span class="sxs-lookup"><span data-stu-id="22998-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="22998-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="22998-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="22998-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="22998-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22998-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="22998-107">*ignorablePrefix*</span></span>|<span data-ttu-id="22998-108">任何有效的前置詞字串，根據 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="22998-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="22998-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="22998-109">*ignorableUri*</span></span>|<span data-ttu-id="22998-110">指定命名空間，根據 XML 1.0 規格的任何有效的 URI。</span><span class="sxs-lookup"><span data-stu-id="22998-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="22998-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="22998-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="22998-112">項目，可以忽略[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]處理器實作中，如果無法解析的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="22998-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="22998-113">*[內容]*</span><span class="sxs-lookup"><span data-stu-id="22998-113">*[content]*</span></span>|<span data-ttu-id="22998-114">*ThisElementCanBeIgnored*標示為可忽略。</span><span class="sxs-lookup"><span data-stu-id="22998-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="22998-115">如果處理器忽略該項目*[內容]*處理*物件*。</span><span class="sxs-lookup"><span data-stu-id="22998-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22998-116">備註</span><span class="sxs-lookup"><span data-stu-id="22998-116">Remarks</span></span>  
 <span data-ttu-id="22998-117">根據預設，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器將會忽略忽略項目內的內容。</span><span class="sxs-lookup"><span data-stu-id="22998-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="22998-118">您可以指定特定的項目由`mc:ProcessContent`，和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器會繼續處理的忽略項目內的內容。</span><span class="sxs-lookup"><span data-stu-id="22998-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="22998-119">此外，這通常會使用內容為巢狀內至少都有一個可忽略和至少一個不是可忽略的數個標記時。</span><span class="sxs-lookup"><span data-stu-id="22998-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="22998-120">中的屬性，例如使用空間的分隔符號，可指定多個前置詞： `mc:ProcessContent="ignore:Element1 ignore:Element2"`。</span><span class="sxs-lookup"><span data-stu-id="22998-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="22998-121">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]命名空間會定義其他的項目和屬性的這個區域中未記載之[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="22998-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="22998-122">如需詳細資訊，請參閱[XML 標記相容性規格](http://go.microsoft.com/fwlink/?LinkId=73824)。</span><span class="sxs-lookup"><span data-stu-id="22998-122">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22998-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22998-123">See Also</span></span>  
 [<span data-ttu-id="22998-124">mc:Ignorable 屬性</span><span class="sxs-lookup"><span data-stu-id="22998-124">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [<span data-ttu-id="22998-125">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="22998-125">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
