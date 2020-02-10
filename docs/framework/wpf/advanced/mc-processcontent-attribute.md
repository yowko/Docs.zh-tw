---
title: mc:ProcessContent 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: bcf55668bdc70902e346c401549a88f6ccb9072e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095121"
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="3ae88-102">mc:ProcessContent 屬性</span><span class="sxs-lookup"><span data-stu-id="3ae88-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="3ae88-103">指定哪些 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 專案應該仍有相關的父項目處理的內容，即使 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的處理器因為指定[mc：](mc-ignorable-attribute.md)可忽略的屬性，可能會忽略直屬父項目也一樣。</span><span class="sxs-lookup"><span data-stu-id="3ae88-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](mc-ignorable-attribute.md).</span></span> <span data-ttu-id="3ae88-104">`mc:ProcessContent` 屬性支援自訂命名空間對應和 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 版本設定的標記相容性。</span><span class="sxs-lookup"><span data-stu-id="3ae88-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3ae88-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="3ae88-105">XAML Attribute Usage</span></span>  
  
```xaml  
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
  
## <a name="xaml-values"></a><span data-ttu-id="3ae88-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="3ae88-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ae88-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="3ae88-107">*ignorablePrefix*</span></span>|<span data-ttu-id="3ae88-108">任何有效的前置字串，依據 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="3ae88-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="3ae88-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="3ae88-109">*ignorableUri*</span></span>|<span data-ttu-id="3ae88-110">根據 XML 1.0 規格，指定命名空間的任何有效 URI。</span><span class="sxs-lookup"><span data-stu-id="3ae88-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="3ae88-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="3ae88-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="3ae88-112">如果無法解析基礎類型，則 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 處理器實作為可以忽略的元素。</span><span class="sxs-lookup"><span data-stu-id="3ae88-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="3ae88-113">*content*</span><span class="sxs-lookup"><span data-stu-id="3ae88-113">*[content]*</span></span>|<span data-ttu-id="3ae88-114">*ThisElementCanBeIgnored*會標示為可忽略。</span><span class="sxs-lookup"><span data-stu-id="3ae88-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="3ae88-115">如果處理器忽略該元素， *[content]* 就會由*物件*處理。</span><span class="sxs-lookup"><span data-stu-id="3ae88-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ae88-116">備註</span><span class="sxs-lookup"><span data-stu-id="3ae88-116">Remarks</span></span>  
 <span data-ttu-id="3ae88-117">根據預設，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的處理器會忽略忽略專案中的內容。</span><span class="sxs-lookup"><span data-stu-id="3ae88-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="3ae88-118">您可以 `mc:ProcessContent`指定特定專案，而 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器會繼續處理忽略專案中的內容。</span><span class="sxs-lookup"><span data-stu-id="3ae88-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="3ae88-119">如果內容是在數個標記中嵌套，通常會使用此方法，其中至少有一個是可忽略的，而且至少有一個無法忽略。</span><span class="sxs-lookup"><span data-stu-id="3ae88-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="3ae88-120">在屬性中，您可以使用空格分隔符號來指定多個前置詞，例如： `mc:ProcessContent="ignore:Element1 ignore:Element2"`。</span><span class="sxs-lookup"><span data-stu-id="3ae88-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="3ae88-121">`http://schemas.openxmlformats.org/markup-compatibility/2006` 命名空間會定義在 SDK 的這個區域中未記載的其他元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="3ae88-121">The `http://schemas.openxmlformats.org/markup-compatibility/2006` namespace defines other elements and attributes that are not documented within this area of the SDK.</span></span> <span data-ttu-id="3ae88-122">如需詳細資訊，請參閱[XML 標記相容性規格](https://docs.microsoft.com/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification)。</span><span class="sxs-lookup"><span data-stu-id="3ae88-122">For more information, see [XML Markup Compatibility Specification](https://docs.microsoft.com/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae88-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ae88-123">See also</span></span>

- [<span data-ttu-id="3ae88-124">mc:Ignorable 屬性</span><span class="sxs-lookup"><span data-stu-id="3ae88-124">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
- [<span data-ttu-id="3ae88-125">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="3ae88-125">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
