---
title: PresentationOptions:Freeze 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: 9909a4170bdb217f91a1fc5713e89bb3a979a999
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512169"
---
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="d51e4-102">PresentationOptions:Freeze 屬性</span><span class="sxs-lookup"><span data-stu-id="d51e4-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="d51e4-103">設定組<xref:System.Windows.Freezable.IsFrozen%2A>狀態`true`上包含<xref:System.Windows.Freezable>項目。</span><span class="sxs-lookup"><span data-stu-id="d51e4-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="d51e4-104">預設行為<xref:System.Windows.Freezable>而不需要`PresentationOptions:Freeze`指定的屬性是<xref:System.Windows.Freezable.IsFrozen%2A>是`false`在載入時間和在一般的相依<xref:System.Windows.Freezable>在執行階段的行為。</span><span class="sxs-lookup"><span data-stu-id="d51e4-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="d51e4-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="d51e4-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="d51e4-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="d51e4-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="d51e4-107">XML 命名空間前置詞，它可以是任何有效的前置詞字串，根據 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="d51e4-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="d51e4-108">前置詞`PresentationOptions`用做為識別用途，此文件中。</span><span class="sxs-lookup"><span data-stu-id="d51e4-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="d51e4-109">具現化任何項目衍生的類別<xref:System.Windows.Freezable>。</span><span class="sxs-lookup"><span data-stu-id="d51e4-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d51e4-110">備註</span><span class="sxs-lookup"><span data-stu-id="d51e4-110">Remarks</span></span>  
 <span data-ttu-id="d51e4-111">`Freeze`屬性是唯一的屬性或其他程式設計項目定義在`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="d51e4-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="d51e4-112">`Freeze`屬性存在這個特殊的命名空間中，好讓它可以為忽略，使用指定特別[mc: Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)做為根項目宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="d51e4-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="d51e4-113">原因，`Freeze`必須是能夠忽略因為不是所有[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作都能 freeze<xref:System.Windows.Freezable>在載入時，這項功能不屬於[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]規格。</span><span class="sxs-lookup"><span data-stu-id="d51e4-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="d51e4-114">處理能力`Freeze`屬性特別是內建[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器處理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]編譯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d51e4-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="d51e4-115">任何類別中，不支援的屬性和屬性語法不是可延伸或修改。</span><span class="sxs-lookup"><span data-stu-id="d51e4-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="d51e4-116">如果您要實作您自己[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]您可以選擇平行的凍結行為的處理器[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器在處理時`Freeze`屬性<xref:System.Windows.Freezable>在載入時間的項目。</span><span class="sxs-lookup"><span data-stu-id="d51e4-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="d51e4-117">任何值`Freeze`以外的其他屬性`true`（不區分大小寫） 會產生載入時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="d51e4-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="d51e4-118">(指定`Freeze`屬性為`false`不是錯誤，但這已經預設值，因此將設定為`false`不執行任何動作)。</span><span class="sxs-lookup"><span data-stu-id="d51e4-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51e4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d51e4-119">See also</span></span>
- <xref:System.Windows.Freezable>
- [<span data-ttu-id="d51e4-120">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="d51e4-120">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [<span data-ttu-id="d51e4-121">mc:Ignorable 屬性</span><span class="sxs-lookup"><span data-stu-id="d51e4-121">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
