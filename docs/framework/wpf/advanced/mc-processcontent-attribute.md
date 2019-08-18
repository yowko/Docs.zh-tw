---
title: mc:ProcessContent 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: bc406659bec3fd8d5da87b597356a3411c7a2605
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567406"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="8dd3e-102">mc:ProcessContent 屬性</span><span class="sxs-lookup"><span data-stu-id="8dd3e-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="8dd3e-103">指定即使[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]因為指定[mc:](mc-ignorable-attribute.md)可忽略的屬性, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器可能會忽略直屬父項目, 哪些專案仍應具有相關的父元素所處理的內容。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](mc-ignorable-attribute.md).</span></span> <span data-ttu-id="8dd3e-104">屬性支援自訂命名空間對應[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和版本設定的標記相容性。 `mc:ProcessContent`</span><span class="sxs-lookup"><span data-stu-id="8dd3e-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="8dd3e-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="8dd3e-105">XAML Attribute Usage</span></span>  
  
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
  
## <a name="xaml-values"></a><span data-ttu-id="8dd3e-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="8dd3e-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8dd3e-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="8dd3e-107">*ignorablePrefix*</span></span>|<span data-ttu-id="8dd3e-108">任何有效的前置字串, 依據 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="8dd3e-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="8dd3e-109">*ignorableUri*</span></span>|<span data-ttu-id="8dd3e-110">根據 XML 1.0 規格, 指定命名空間的任何有效 URI。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="8dd3e-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="8dd3e-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="8dd3e-112">如果無法解析基礎類型, 則[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]處理器執行可以忽略的元素。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="8dd3e-113">*[content]*</span><span class="sxs-lookup"><span data-stu-id="8dd3e-113">*[content]*</span></span>|<span data-ttu-id="8dd3e-114">*ThisElementCanBeIgnored*會標示為可忽略。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="8dd3e-115">如果處理器忽略該元素, *[content]* 就會由*物件*處理。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dd3e-116">備註</span><span class="sxs-lookup"><span data-stu-id="8dd3e-116">Remarks</span></span>  
 <span data-ttu-id="8dd3e-117">根據預設, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器會忽略忽略之元素內的內容。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="8dd3e-118">您可以藉由`mc:ProcessContent`指定特定元素, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]而處理器會繼續處理忽略專案中的內容。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="8dd3e-119">如果內容是在數個標記中嵌套, 通常會使用此方法, 其中至少有一個是可忽略的, 而且至少有一個無法忽略。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="8dd3e-120">在屬性中, 您可以使用空格分隔符號來指定多個前置詞, 例如`mc:ProcessContent="ignore:Element1 ignore:Element2"`:。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="8dd3e-121">[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]命名空間會定義在 SDK 的這個區域中未記載的其他元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="8dd3e-122">如需詳細資訊, 請參閱[XML 標記相容性規格](https://go.microsoft.com/fwlink/?LinkId=73824)。</span><span class="sxs-lookup"><span data-stu-id="8dd3e-122">For more information, see [XML Markup Compatibility Specification](https://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd3e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dd3e-123">See also</span></span>

- [<span data-ttu-id="8dd3e-124">mc:Ignorable 屬性</span><span class="sxs-lookup"><span data-stu-id="8dd3e-124">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
- [<span data-ttu-id="8dd3e-125">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="8dd3e-125">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
