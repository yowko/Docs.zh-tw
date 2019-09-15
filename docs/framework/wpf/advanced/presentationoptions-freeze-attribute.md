---
title: PresentationOptions:Freeze 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: d3e0cee293a9585b972b0145da953976ed94b74c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991432"
---
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="8f991-102">PresentationOptions:Freeze 屬性</span><span class="sxs-lookup"><span data-stu-id="8f991-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="8f991-103">將狀態設定為`true`包含<xref:System.Windows.Freezable>專案上的。 <xref:System.Windows.Freezable.IsFrozen%2A></span><span class="sxs-lookup"><span data-stu-id="8f991-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="8f991-104">未指定<xref:System.Windows.Freezable> `PresentationOptions:Freeze` 屬性之<xref:System.Windows.Freezable.IsFrozen%2A>的預設行為是<xref:System.Windows.Freezable>在載入時，並取決於執行時間的一般行為。 `false`</span><span class="sxs-lookup"><span data-stu-id="8f991-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="8f991-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="8f991-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8f991-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="8f991-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="8f991-107">XML 命名空間前置詞，可以是任何有效的前置字串，依據 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="8f991-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="8f991-108">在本`PresentationOptions`檔中，此前置詞是用於識別用途。</span><span class="sxs-lookup"><span data-stu-id="8f991-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="8f991-109">具現化之<xref:System.Windows.Freezable>任何衍生類別的元素。</span><span class="sxs-lookup"><span data-stu-id="8f991-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f991-110">備註</span><span class="sxs-lookup"><span data-stu-id="8f991-110">Remarks</span></span>  
 <span data-ttu-id="8f991-111">屬性是`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML 命名空間中定義的唯一屬性或其他程式設計項目。 `Freeze`</span><span class="sxs-lookup"><span data-stu-id="8f991-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="8f991-112">屬性會特別存在於這個特殊的命名空間中，以便將其指定為可忽略，並使用[mc：可忽略的屬性](mc-ignorable-attribute.md)做為根項目宣告的一部分。 `Freeze`</span><span class="sxs-lookup"><span data-stu-id="8f991-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="8f991-113">`Freeze`必須能夠忽略的原因是因為並非所有[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器的執行<xref:System.Windows.Freezable>都能夠在載入時凍結，這項[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]功能不是規格的一部分。</span><span class="sxs-lookup"><span data-stu-id="8f991-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="8f991-114">處理`Freeze`屬性的能力，特別是內建[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]于處理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]已編譯應用程式的處理器。</span><span class="sxs-lookup"><span data-stu-id="8f991-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="8f991-115">任何類別都不支援屬性，而且屬性語法不可延伸或可修改。</span><span class="sxs-lookup"><span data-stu-id="8f991-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="8f991-116">如果您要執行[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]自己的處理器，您可以在載入時，選擇平行處理[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `Freeze`專案的屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] （attribute <xref:System.Windows.Freezable> ）。</span><span class="sxs-lookup"><span data-stu-id="8f991-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="8f991-117">除了`true` （不區分`Freeze`大小寫）以外的任何屬性值，都會產生載入時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f991-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="8f991-118">（將`Freeze`屬性指定為`false`不是錯誤，但已是預設值，因此設定為`false`不執行任何動作）。</span><span class="sxs-lookup"><span data-stu-id="8f991-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f991-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f991-119">See also</span></span>

- <xref:System.Windows.Freezable>
- [<span data-ttu-id="8f991-120">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="8f991-120">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="8f991-121">mc:Ignorable 屬性</span><span class="sxs-lookup"><span data-stu-id="8f991-121">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
