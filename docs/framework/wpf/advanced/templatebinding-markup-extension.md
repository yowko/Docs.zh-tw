---
title: TemplateBinding 標記延伸
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: 3ae17dc98137bd417d2468fb0415fb2078acf20f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686019"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="ef448-102">TemplateBinding 標記延伸</span><span class="sxs-lookup"><span data-stu-id="ef448-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="ef448-103">將控制項樣板中的屬性值連結成為樣板化控制項上另一個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ef448-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="ef448-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="ef448-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="ef448-105">XAML 屬性使用方式 (針對樣板或樣式中的 Setter 屬性)</span><span class="sxs-lookup"><span data-stu-id="ef448-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="ef448-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="ef448-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="ef448-107">在 setter 語法中設定之屬性的 <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ef448-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="ef448-108">存在於樣板化類型上的另一個相依性屬性，由其 <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> 所指定。</span><span class="sxs-lookup"><span data-stu-id="ef448-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="ef448-109">-或-</span><span class="sxs-lookup"><span data-stu-id="ef448-109">- or -</span></span><br /><br /> <span data-ttu-id="ef448-110">「穿插句點」的屬性名稱，由樣板化目標類型以外的不同類型所定義。</span><span class="sxs-lookup"><span data-stu-id="ef448-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="ef448-111">這實際上是一個 <xref:System.Windows.PropertyPath>。</span><span class="sxs-lookup"><span data-stu-id="ef448-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="ef448-112">請參閱[PropertyPath XAML 語法](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="ef448-112">See [PropertyPath XAML Syntax](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef448-113">備註</span><span class="sxs-lookup"><span data-stu-id="ef448-113">Remarks</span></span>  
 <span data-ttu-id="ef448-114">A`TemplateBinding`是的最佳化的形式[繫結](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)範本的情況下，類似於`Binding`建構`{Binding RelativeSource={RelativeSource TemplatedParent}}`。</span><span class="sxs-lookup"><span data-stu-id="ef448-114">A `TemplateBinding` is an optimized form of a [Binding](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="ef448-115">`TemplateBinding` 永遠是單向繫結，即使相關的屬性是預設為雙向繫結也一樣。</span><span class="sxs-lookup"><span data-stu-id="ef448-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="ef448-116">相關的兩個屬性必須是相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="ef448-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="ef448-117">為了達到樣板化父代的雙向繫結下列繫結陳述式改為使用`{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`。</span><span class="sxs-lookup"><span data-stu-id="ef448-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span> 
  
 <span data-ttu-id="ef448-118">[RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)是另一個標記延伸，有時候搭配使用或取而代之`TemplateBinding`才能執行相對屬性繫結，在範本內。</span><span class="sxs-lookup"><span data-stu-id="ef448-118">[RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="ef448-119">概念說明控制項樣板未涵蓋;如需詳細資訊，請參閱 <<c0> [ 控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="ef448-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="ef448-120">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="ef448-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="ef448-121">`TemplateBinding` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.TemplateBindingExtension.Property%2A> 延伸類別的 <xref:System.Windows.TemplateBindingExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="ef448-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="ef448-122">物件項目語法雖然可行，但由於沒有實際的應用程式，所以這裡不加說明。</span><span class="sxs-lookup"><span data-stu-id="ef448-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="ef448-123">`TemplateBinding` 是用來以評估後的運算式填滿 setter 內的值，而使用 `TemplateBinding` 的物件項目語法來填滿 `<Setter.Property>` 屬性項目語法則太過繁瑣。</span><span class="sxs-lookup"><span data-stu-id="ef448-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="ef448-124">`TemplateBinding` 也可以用於會指定 <xref:System.Windows.TemplateBindingExtension.Property%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。</span><span class="sxs-lookup"><span data-stu-id="ef448-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="ef448-125">詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。</span><span class="sxs-lookup"><span data-stu-id="ef448-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="ef448-126">因為 `TemplateBinding` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。</span><span class="sxs-lookup"><span data-stu-id="ef448-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="ef448-127">在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 處理器實作中，這個標記延伸的處理由定義<xref:System.Windows.TemplateBindingExtension>類別。</span><span class="sxs-lookup"><span data-stu-id="ef448-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="ef448-128">`TemplateBinding` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="ef448-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="ef448-129">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="ef448-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="ef448-130">在 XAML 使用的所有標記延伸`{`和`}`字元在其屬性語法中，這是用 XAML 處理器會辨識為標記延伸必須處理這個屬性的慣例。</span><span class="sxs-lookup"><span data-stu-id="ef448-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="ef448-131">如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="ef448-131">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef448-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef448-132">See also</span></span>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ef448-133">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="ef448-133">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="ef448-134">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="ef448-134">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="ef448-135">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="ef448-135">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="ef448-136">RelativeSource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="ef448-136">RelativeSource MarkupExtension</span></span>](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)
- [<span data-ttu-id="ef448-137">Binding 標記延伸</span><span class="sxs-lookup"><span data-stu-id="ef448-137">Binding Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)
