---
title: "PresentationOptions:Freeze 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb305c69cec7c4e4766153ae64d37b19ab0bccea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="c4633-102">PresentationOptions:Freeze 屬性</span><span class="sxs-lookup"><span data-stu-id="c4633-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="c4633-103">設定<xref:System.Windows.Freezable.IsFrozen%2A>狀態`true`上包含<xref:System.Windows.Freezable>項目。</span><span class="sxs-lookup"><span data-stu-id="c4633-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="c4633-104">預設行為<xref:System.Windows.Freezable>不含`PresentationOptions:Freeze`指定屬性是<xref:System.Windows.Freezable.IsFrozen%2A>是`false`在載入時間，取決於一般<xref:System.Windows.Freezable>在執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="c4633-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c4633-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="c4633-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c4633-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="c4633-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="c4633-107">XML 命名空間前置詞，它可以是任何有效的前置詞字串，根據 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="c4633-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="c4633-108">前置詞`PresentationOptions`用於識別這個文件中。</span><span class="sxs-lookup"><span data-stu-id="c4633-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="c4633-109">具現化任何元素的衍生類別<xref:System.Windows.Freezable>。</span><span class="sxs-lookup"><span data-stu-id="c4633-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4633-110">備註</span><span class="sxs-lookup"><span data-stu-id="c4633-110">Remarks</span></span>  
 <span data-ttu-id="c4633-111">`Freeze`屬性是唯一的屬性，或是其他程式設計項目中定義`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c4633-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="c4633-112">`Freeze`屬性存在這個特殊的命名空間中，特別是，以便將它指定為可忽略，使用[mc: Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)做為根項目宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="c4633-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="c4633-113">原因，`Freeze`必須能夠被忽略因為不是所有[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作可凍結<xref:System.Windows.Freezable>在載入時間; 這項功能不屬於[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]規格。</span><span class="sxs-lookup"><span data-stu-id="c4633-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="c4633-114">處理能力`Freeze`屬性特別內建[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器處理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]用於編譯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c4633-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="c4633-115">屬性不支援的任何類別，且屬性語法可延伸或可修改。</span><span class="sxs-lookup"><span data-stu-id="c4633-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="c4633-116">如果您要實作您自己[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器平行的凍結行為時，您可以選擇[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器處理時`Freeze`屬性<xref:System.Windows.Freezable>在載入時間的項目。</span><span class="sxs-lookup"><span data-stu-id="c4633-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="c4633-117">任何值`Freeze`屬性以外`true`（不區分大小寫） 會產生載入時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4633-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="c4633-118">(指定`Freeze`屬性做為`false`不是錯誤，但已經預設值，因此將設定為`false`不做任何動作)。</span><span class="sxs-lookup"><span data-stu-id="c4633-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4633-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4633-119">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 [<span data-ttu-id="c4633-120">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="c4633-120">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="c4633-121">mc:Ignorable 屬性</span><span class="sxs-lookup"><span data-stu-id="c4633-121">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
