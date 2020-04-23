---
title: x:Key 指示詞
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: c05f98932ceceeb1530b34a09b1923f2af1378b5
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071497"
---
# <a name="xkey-directive"></a><span data-ttu-id="57c97-102">x:Key 指示詞</span><span class="sxs-lookup"><span data-stu-id="57c97-102">x:Key Directive</span></span>
<span data-ttu-id="57c97-103">唯一標識在 XAML 定義的字典中創建和引用的元素。</span><span class="sxs-lookup"><span data-stu-id="57c97-103">Uniquely identifies elements that are created and referenced in a XAML-defined dictionary.</span></span> <span data-ttu-id="57c97-104">向`x:Key`XAML 物件元素添加值是標識資源字典中資源的最常見方法,例如在<xref:System.Windows.ResourceDictionary>WPF 中。</span><span class="sxs-lookup"><span data-stu-id="57c97-104">Adding an `x:Key` value to a XAML object element is the most common way to identify a resource in a resource dictionary, for example in a WPF <xref:System.Windows.ResourceDictionary>.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="57c97-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="57c97-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a><span data-ttu-id="57c97-106">XAML 屬性使用方式(特定於 WPF)</span><span class="sxs-lookup"><span data-stu-id="57c97-106">XAML Attribute Usage (WPF-specific)</span></span>  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="57c97-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="57c97-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`stringKeyValue`|<span data-ttu-id="57c97-108">用作鍵的文字字串。</span><span class="sxs-lookup"><span data-stu-id="57c97-108">A text string to use as a key.</span></span> <span data-ttu-id="57c97-109">文字字串必須符合[XamlName 語法](xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="57c97-109">The text string must conform to the [XamlName Grammar](xamlname-grammar.md).</span></span>|  
|`markupExtensionUsage`|<span data-ttu-id="57c97-110">在標記延伸分隔符{}中,提供用作鍵的對象的標記擴展用法。</span><span class="sxs-lookup"><span data-stu-id="57c97-110">Within the markup extension delimiters {}, a markup extension usage that provides an object to use as a key.</span></span> <span data-ttu-id="57c97-111">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="57c97-111">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57c97-112">備註</span><span class="sxs-lookup"><span data-stu-id="57c97-112">Remarks</span></span>  
 <span data-ttu-id="57c97-113">`x:Key`支援 XAML 資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="57c97-113">`x:Key` supports the XAML resource dictionary concept.</span></span> <span data-ttu-id="57c97-114">XAML 作為一種語言不會定義資源字典實現,而資源字典實現留給特定的 UI 框架。</span><span class="sxs-lookup"><span data-stu-id="57c97-114">XAML as a language doesn't define a resource dictionary implementation, that is left to specific UI frameworks.</span></span> <span data-ttu-id="57c97-115">要瞭解有關如何在 WPF 中實現 XAML 資源字典的更多資訊,請參閱[XAML 資源](../fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="57c97-115">To learn more about how XAML resource dictionaries are implemented in WPF, see [XAML Resources](../fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="57c97-116">在 XAML 2006 和`x:Key`WPF 中,必須作為屬性提供。</span><span class="sxs-lookup"><span data-stu-id="57c97-116">In XAML 2006 and WPF, `x:Key` must be provided as an attribute.</span></span> <span data-ttu-id="57c97-117">您仍可以使用非字串鍵,但這需要標記擴展用法才能在屬性窗體中提供非字串值。</span><span class="sxs-lookup"><span data-stu-id="57c97-117">You can still use nonstring keys, but this requires a markup extension usage in order to provide the nonstring value in attribute form.</span></span> <span data-ttu-id="57c97-118">如果使用 XAML 2009,`x:Key`則可以指定為元素,以顯式支援由字串以外的對象類型鍵控的字典,而無需標記擴展中間。</span><span class="sxs-lookup"><span data-stu-id="57c97-118">If you are using XAML 2009, `x:Key` can be specified as an element, to explicitly support dictionaries keyed by object types other than strings without requiring a markup extension intermediate.</span></span> <span data-ttu-id="57c97-119">請參閱本主題中的「XAML 2009」部分。</span><span class="sxs-lookup"><span data-stu-id="57c97-119">See the "XAML 2009" section in this topic.</span></span> <span data-ttu-id="57c97-120">備註部分的其餘部分特別適用於 XAML 2006 實現。</span><span class="sxs-lookup"><span data-stu-id="57c97-120">The remainder of the Remarks section applies specifically to the XAML 2006 implementation.</span></span>  
  
 <span data-ttu-id="57c97-121">的屬性`x:Key`值可以是[XamlName 語法](xamlname-grammar.md)中定義的任何字串,也可以是通過標記擴展計算的物件。</span><span class="sxs-lookup"><span data-stu-id="57c97-121">The attribute value of `x:Key` can be any string defined in the [XamlName Grammar](xamlname-grammar.md) or can be an object evaluated through a markup extension.</span></span> <span data-ttu-id="57c97-122">有關 WPF 的範例,請參閱"WPF 使用說明"。</span><span class="sxs-lookup"><span data-stu-id="57c97-122">See "WPF Usage Notes" for an example from WPF.</span></span>  
  
 <span data-ttu-id="57c97-123">作為<xref:System.Collections.IDictionary>實現的父元素的子元素通常必須包含`x:Key`指定 該字典中唯一鍵值的屬性。</span><span class="sxs-lookup"><span data-stu-id="57c97-123">Child elements of a parent element that is an <xref:System.Collections.IDictionary> implementation must typically include an `x:Key` attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="57c97-124">框架可能實現別名鍵屬性,`x:Key`以替換特定類型;定義此類屬性的類型應歸因於<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>。</span><span class="sxs-lookup"><span data-stu-id="57c97-124">Frameworks might implement aliased key properties to substitute for `x:Key` on particular types; types that define such properties should be attributed with <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span></span>  
  
 <span data-ttu-id="57c97-125">指定`x:Key`等效的代碼是用於基礎<xref:System.Collections.IDictionary>的鍵。</span><span class="sxs-lookup"><span data-stu-id="57c97-125">The code equivalent of specifying `x:Key` is the key that is used for the underlying <xref:System.Collections.IDictionary>.</span></span> <span data-ttu-id="57c97-126">例如,在`x:Key`WPF 中資源標記中應用的與將資源添加到代碼中的`key`<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType><xref:System.Windows.ResourceDictionary>WPF 時的參數值等效。</span><span class="sxs-lookup"><span data-stu-id="57c97-126">For example, an `x:Key` that is applied in markup for a resource in WPF is equivalent to the value of the `key` parameter of <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> when you add the resource to a WPF <xref:System.Windows.ResourceDictionary> in code.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="57c97-127">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="57c97-127">WPF Usage Notes</span></span>  
 <span data-ttu-id="57c97-128">作為<xref:System.Collections.IDictionary>實現(如 WPF)<xref:System.Windows.ResourceDictionary>的父物件的子物件通常必須`x:Key`包含屬性 ,並且鍵值必須是唯一的字典。</span><span class="sxs-lookup"><span data-stu-id="57c97-128">Child objects of a parent object that is an <xref:System.Collections.IDictionary> implementation, such as the WPF <xref:System.Windows.ResourceDictionary>, must typically include an `x:Key` attribute, and the key value must be unique within that dictionary.</span></span> <span data-ttu-id="57c97-129">有兩個值得注意的例外:</span><span class="sxs-lookup"><span data-stu-id="57c97-129">There are two notable exceptions:</span></span>  
  
- <span data-ttu-id="57c97-130">某些 WPF 類型聲明字典用法的隱式鍵。</span><span class="sxs-lookup"><span data-stu-id="57c97-130">Some WPF types declare an implicit key for dictionary usage.</span></span> <span data-ttu-id="57c97-131">例如,帶<xref:System.Windows.Style><xref:System.Windows.Style.TargetType%2A>的或<xref:System.Windows.DataTemplate>的<xref:System.Windows.DataTemplate.DataType%2A>和,<xref:System.Windows.ResourceDictionary>可以位於中,並使用隱式鍵。</span><span class="sxs-lookup"><span data-stu-id="57c97-131">For example, a <xref:System.Windows.Style> with a <xref:System.Windows.Style.TargetType%2A>, or a <xref:System.Windows.DataTemplate> with a <xref:System.Windows.DataTemplate.DataType%2A>, can be  in a <xref:System.Windows.ResourceDictionary> and use the implicit key.</span></span>  
  
- <span data-ttu-id="57c97-132">WPF 支援合併的資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="57c97-132">WPF supports a merged resource dictionary concept.</span></span> <span data-ttu-id="57c97-133">金鑰可以在合併字典之間共享,並且可以使用<xref:System.Windows.FrameworkContentElement.FindResource%2A>訪問共用密鑰行為。</span><span class="sxs-lookup"><span data-stu-id="57c97-133">Keys can be shared between the merged dictionaries, and the shared key behavior can be accessed using <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span></span> <span data-ttu-id="57c97-134">如需詳細資訊，請參閱[合併的資源字典](../../framework/wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="57c97-134">For more information, see [Merged Resource Dictionaries](../../framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
 <span data-ttu-id="57c97-135">在整體 WPF XAML 實現和應用模型中,XAML 標記編譯器不檢查密鑰唯一性。</span><span class="sxs-lookup"><span data-stu-id="57c97-135">In the overall WPF XAML implementation and application model, key uniqueness is not checked by the XAML markup compiler.</span></span> <span data-ttu-id="57c97-136">相反,缺少或非唯`x:Key`一值會導致載入時間 XAML 解析器錯誤。</span><span class="sxs-lookup"><span data-stu-id="57c97-136">Instead, missing or nonunique `x:Key` values cause load-time XAML parser errors.</span></span> <span data-ttu-id="57c97-137">但是,Visual Studio 處理 WPF 字典時通常可以在設計階段注意到此類錯誤。</span><span class="sxs-lookup"><span data-stu-id="57c97-137">However, Visual Studio handling of dictionaries for WPF can often note such errors in the design phase.</span></span>  
  
 <span data-ttu-id="57c97-138">請注意,在所示的語法中,<xref:System.Windows.ResourceDictionary>物件隱化於 WPF XAML 處理器如何生成<xref:System.Windows.FrameworkElement.Resources%2A>集合以填充 集合。</span><span class="sxs-lookup"><span data-stu-id="57c97-138">Note that in the syntax shown, the <xref:System.Windows.ResourceDictionary> object is implicit in how the WPF XAML processor produces a collection to populate a <xref:System.Windows.FrameworkElement.Resources%2A> collection.</span></span> <span data-ttu-id="57c97-139">在<xref:System.Windows.ResourceDictionary>標記中,通常不作為元素顯式提供 a,儘管在某些情況下,如果需要,它可以是集合物件元素(<xref:System.Windows.FrameworkElement.Resources%2A>它將是 屬性元素和填充字典中的項之間的集合物件元素)。</span><span class="sxs-lookup"><span data-stu-id="57c97-139">A <xref:System.Windows.ResourceDictionary> is not typically provided explicitly as an element in markup, although it can be in some cases if wanted for clarity (it would be a collection object element between the <xref:System.Windows.FrameworkElement.Resources%2A> property element and the items within that populate the dictionary).</span></span> <span data-ttu-id="57c97-140">有關集合物件在標記中幾乎總是隱式元素的原因的資訊,請參閱[XAML 語法詳細資訊](../../framework/wpf/advanced/xaml-syntax-in-detail.md)。</span><span class="sxs-lookup"><span data-stu-id="57c97-140">For information about why a collection object is almost always an implicit element in markup, see [XAML Syntax In Detail](../../framework/wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
 <span data-ttu-id="57c97-141">在 WPF XAML 實現中,資源字典密鑰<xref:System.Windows.ResourceKey>的處理由 抽象類定義。</span><span class="sxs-lookup"><span data-stu-id="57c97-141">In the WPF XAML implementation, the handling for resource dictionary keys is defined by the <xref:System.Windows.ResourceKey> abstract class.</span></span> <span data-ttu-id="57c97-142">但是,WPF XAML 處理器會根據密鑰的用法為密鑰生成不同的基礎擴展類型。</span><span class="sxs-lookup"><span data-stu-id="57c97-142">However the WPF XAML processor produces different underlying extension types for keys based on their usages.</span></span> <span data-ttu-id="57c97-143">例如,或<xref:System.Windows.DataTemplate>任何派生類的鍵單獨處理,並生成不同的<xref:System.Windows.DataTemplateKey>物件。</span><span class="sxs-lookup"><span data-stu-id="57c97-143">For example, the key for a <xref:System.Windows.DataTemplate> or any derived class is handled separately, and produces a distinct <xref:System.Windows.DataTemplateKey> object.</span></span>  
  
 <span data-ttu-id="57c97-144">鍵與名稱在基本的`x:Key`XAML`x:Name`定義 中使用不同的指令和語言元素 ( 對 ) 。</span><span class="sxs-lookup"><span data-stu-id="57c97-144">Keys and names use different directives and language elements (`x:Key` versus `x:Name`) in the basic XAML definition.</span></span> <span data-ttu-id="57c97-145">WPF 的定義和這些概念的應用也在不同的情況下使用密鑰和名稱。</span><span class="sxs-lookup"><span data-stu-id="57c97-145">Keys and names are also used in different situations by the WPF definition and application of these concepts.</span></span> <span data-ttu-id="57c97-146">有關詳細資訊,請參閱[WPF XAML 名稱範圍](../../framework/wpf/advanced/wpf-xaml-namescopes.md)。</span><span class="sxs-lookup"><span data-stu-id="57c97-146">For details, see [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).</span></span>  
  
 <span data-ttu-id="57c97-147">如前所述,鍵的值可以通過標記擴展提供,並且可以不提供字串值。</span><span class="sxs-lookup"><span data-stu-id="57c97-147">As stated previously, the value of a key can be supplied through a markup extension and can be other than a string value.</span></span> <span data-ttu-id="57c97-148">WPF 專案的範例是,`x:Key`的值 可能是[元件資源金鑰](../../framework/wpf/advanced/componentresourcekey-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="57c97-148">An example WPF scenario is that the value of `x:Key` may be a [ComponentResourceKey](../../framework/wpf/advanced/componentresourcekey-markup-extension.md).</span></span> <span data-ttu-id="57c97-149">某些控件公開自定義樣式資源的該類型的樣式鍵,該樣式資源在不完全替換樣式的情況下會影響該控件的部分外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="57c97-149">Certain controls expose a style key of that type for a custom style resource that influences part of the appearance and behavior of that control without totally replacing the style.</span></span> <span data-ttu-id="57c97-150">此鍵的一個例子是<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="57c97-150">An example of such a key is <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span></span>  
  
 <span data-ttu-id="57c97-151">WPF 合併字典功能引入了關鍵唯一性和密鑰查找行為的其他注意事項。</span><span class="sxs-lookup"><span data-stu-id="57c97-151">The WPF merged dictionary feature introduces additional considerations for key uniqueness and key lookup behavior.</span></span> <span data-ttu-id="57c97-152">如需詳細資訊，請參閱[合併的資源字典](../../framework/wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="57c97-152">For more information, see [Merged Resource Dictionaries](../../framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="57c97-153">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="57c97-153">XAML 2009</span></span>  
 <span data-ttu-id="57c97-154">XAML 2009`x:Key`放寬了始終以屬性形式提供的限制。</span><span class="sxs-lookup"><span data-stu-id="57c97-154">XAML 2009 relaxes the restriction that `x:Key` always be provided in attribute form.</span></span>  
  
 <span data-ttu-id="57c97-155">在 WPF 中,可以使用 XAML 2009 功能,但僅適用於未標記編譯的 XAML。</span><span class="sxs-lookup"><span data-stu-id="57c97-155">In WPF, you can use XAML 2009 features, but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="57c97-156">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="57c97-156">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="57c97-157">在 XAML 2009 下`x:Key`,您可以通過以下用法指定元素:</span><span class="sxs-lookup"><span data-stu-id="57c97-157">Under XAML 2009, you can specify `x:Key` elements through the following usage:</span></span>  
  
### <a name="xaml-element-usage-xaml-2009-only"></a><span data-ttu-id="57c97-158">XAML 元素使用(僅限 XAML 2009)</span><span class="sxs-lookup"><span data-stu-id="57c97-158">XAML Element Usage (XAML 2009 only)</span></span>  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a><span data-ttu-id="57c97-159">XAML 值</span><span class="sxs-lookup"><span data-stu-id="57c97-159">XAML Values</span></span>  
  
|||  
|-|-|  
|`keyObject`|<span data-ttu-id="57c97-160">物件的物件元素,該物件用作專用字典中給定`object`項的鍵。</span><span class="sxs-lookup"><span data-stu-id="57c97-160">Object element for the object that is used as the key for a given `object` in a specialized dictionary.</span></span>|  
  
- <span data-ttu-id="57c97-161">此種使用的容器/父級不在此處顯示。</span><span class="sxs-lookup"><span data-stu-id="57c97-161">The container/parent for this kind of use is not shown here.</span></span> <span data-ttu-id="57c97-162">`object`應作為表示專用字典實現的物件元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="57c97-162">`object` is expected to be a child of an object element that represents a specialized dictionary implementation.</span></span> <span data-ttu-id="57c97-163">`keyObject`應作為該特定專用字典實現的關鍵的物件實例(或值類型的值)。</span><span class="sxs-lookup"><span data-stu-id="57c97-163">`keyObject` is expected to be an object instance (or a value of a value type) that is appropriate as the key for that particular specialized dictionary implementation.</span></span>  
  
- <span data-ttu-id="57c97-164">WPF 不實現需要此用法的字典。</span><span class="sxs-lookup"><span data-stu-id="57c97-164">WPF does not implement dictionaries that require this usage.</span></span> <span data-ttu-id="57c97-165">對象鍵是 XAML 語言的一個常規功能,對於某些自定義字典方案可能很有用,在其中需要在 XAML 中創建字典。</span><span class="sxs-lookup"><span data-stu-id="57c97-165">Object keys is more a general feature of the XAML language, possibly useful for certain custom dictionary scenarios where creating the dictionary in XAML is desirable.</span></span> <span data-ttu-id="57c97-166">對於 WPF 功能(如使用非字串鍵進行資源化的隱式樣式),存在其他用於建立或指定鍵的技術,因此無需使用物件鍵。</span><span class="sxs-lookup"><span data-stu-id="57c97-166">For WPF features such as implicit styles that use non-string keys for resources, other techniques for establishing or specifying the keys exist, so using an object key is not necessary.</span></span>  
  
- <span data-ttu-id="57c97-167">`keyObject`也可以是物件元素形式的標記擴展用法,而不是直接的物件實例。</span><span class="sxs-lookup"><span data-stu-id="57c97-167">`keyObject` could also be a markup extension usage in object element form, rather than a direct object instance.</span></span>  
  
## <a name="silverlight-usage-notes"></a><span data-ttu-id="57c97-168">銀光使用說明</span><span class="sxs-lookup"><span data-stu-id="57c97-168">Silverlight Usage Notes</span></span>  
 <span data-ttu-id="57c97-169">`x:Key`銀光單獨記錄。</span><span class="sxs-lookup"><span data-stu-id="57c97-169">`x:Key` for Silverlight is documented separately.</span></span> <span data-ttu-id="57c97-170">有關詳細資訊,請參閱[XAML 命名空間 (x:)語言功能(銀光)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).</span><span class="sxs-lookup"><span data-stu-id="57c97-170">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c97-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57c97-171">See also</span></span>

- [<span data-ttu-id="57c97-172">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="57c97-172">XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="57c97-173">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="57c97-173">Resources and Code</span></span>](../../framework/wpf/advanced/resources-and-code.md)
- [<span data-ttu-id="57c97-174">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="57c97-174">StaticResource Markup Extension</span></span>](../../framework/wpf/advanced/staticresource-markup-extension.md)
