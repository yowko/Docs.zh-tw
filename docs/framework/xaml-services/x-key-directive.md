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
ms.openlocfilehash: 4ffd7a2922c7f3ba35ccb9ac7ce29a6a00cd99af
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837203"
---
# <a name="xkey-directive"></a><span data-ttu-id="93805-102">x:Key 指示詞</span><span class="sxs-lookup"><span data-stu-id="93805-102">x:Key Directive</span></span>
<span data-ttu-id="93805-103">在 XAML 定義的字典中建立和參考的唯一識別項目。</span><span class="sxs-lookup"><span data-stu-id="93805-103">Uniquely identifies elements that are created and referenced in a XAML-defined dictionary.</span></span> <span data-ttu-id="93805-104">將 `x:Key` 值加入至 XAML 物件項目是在資源字典中識別資源的常見方式，例如在 WPF <xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="93805-104">Adding an `x:Key` value to a XAML object element is the most common way to identify a resource in a resource dictionary, for example in a WPF <xref:System.Windows.ResourceDictionary>.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="93805-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="93805-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a><span data-ttu-id="93805-106">XAML 屬性使用方式 (特定於 WPF)</span><span class="sxs-lookup"><span data-stu-id="93805-106">XAML Attribute Usage (WPF-specific)</span></span>  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="93805-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="93805-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`stringKeyValue`|<span data-ttu-id="93805-108">文字字串，使用做為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93805-108">A text string to use as a key.</span></span> <span data-ttu-id="93805-109">文字字串必須符合[XamlName 文法](xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="93805-109">The text string must conform to the [XamlName Grammar](xamlname-grammar.md).</span></span>|  
|`markupExtensionUsage`|<span data-ttu-id="93805-110">在標記延伸分隔符號 {}中，這是一種標記延伸使用方式，可提供要當做索引鍵使用的物件。</span><span class="sxs-lookup"><span data-stu-id="93805-110">Within the markup extension delimiters {}, a markup extension usage that provides an object to use as a key.</span></span> <span data-ttu-id="93805-111">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="93805-111">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93805-112">備註</span><span class="sxs-lookup"><span data-stu-id="93805-112">Remarks</span></span>  
 <span data-ttu-id="93805-113">`x:Key` 支援 XAML 資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="93805-113">`x:Key` supports the XAML resource dictionary concept.</span></span> <span data-ttu-id="93805-114">XAML 語言不定義資源字典實作，而是保留給特定 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="93805-114">XAML as a language doesn't define a resource dictionary implementation, that is left to specific UI frameworks.</span></span> <span data-ttu-id="93805-115">若要深入瞭解如何在 WPF 中執行 XAML 資源字典，請參閱[Xaml 資源](../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="93805-115">To learn more about how XAML resource dictionaries are implemented in WPF, see [XAML Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="93805-116">在 XAML 2006 和 WPF 中，必須以屬性的形式提供 `x:Key`。</span><span class="sxs-lookup"><span data-stu-id="93805-116">In XAML 2006 and WPF, `x:Key` must be provided as an attribute.</span></span> <span data-ttu-id="93805-117">您依然可以使用非字串索引鍵，但這需要標記延伸使用方式，才能在屬性表單中提供非字串值。</span><span class="sxs-lookup"><span data-stu-id="93805-117">You can still use nonstring keys, but this requires a markup extension usage in order to provide the nonstring value in attribute form.</span></span> <span data-ttu-id="93805-118">如果您使用 XAML 2009，則可以將 `x:Key` 指定為元素，以明確支援字串以外的物件類型所建立的字典，而不需要標記延伸的中繼。</span><span class="sxs-lookup"><span data-stu-id="93805-118">If you are using XAML 2009, `x:Key` can be specified as an element, to explicitly support dictionaries keyed by object types other than strings without requiring a markup extension intermediate.</span></span> <span data-ttu-id="93805-119">請參閱本主題中的「XAML 2009」一節。</span><span class="sxs-lookup"><span data-stu-id="93805-119">See the "XAML 2009" section in this topic.</span></span> <span data-ttu-id="93805-120">[備註] 區段的其餘部分會特別適用于 XAML 2006 的執行。</span><span class="sxs-lookup"><span data-stu-id="93805-120">The remainder of the Remarks section applies specifically to the XAML 2006 implementation.</span></span>  
  
 <span data-ttu-id="93805-121">`x:Key` 的屬性值可以是在[XamlName 文法](xamlname-grammar.md)中定義的任何字串，或者可以是透過標記延伸評估的物件。</span><span class="sxs-lookup"><span data-stu-id="93805-121">The attribute value of `x:Key` can be any string defined in the [XamlName Grammar](xamlname-grammar.md) or can be an object evaluated through a markup extension.</span></span> <span data-ttu-id="93805-122">如需 WPF 的範例，請參閱＜WPF 使用方式附註＞。</span><span class="sxs-lookup"><span data-stu-id="93805-122">See "WPF Usage Notes" for an example from WPF.</span></span>  
  
 <span data-ttu-id="93805-123">本身為 <xref:System.Collections.IDictionary> 實作的父項目，其子項目通常必須包含 `x:Key` 屬性，以指定該字典內的唯一索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="93805-123">Child elements of a parent element that is an <xref:System.Collections.IDictionary> implementation must typically include an `x:Key` attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="93805-124">架構可能會實作別名索引鍵屬性以取代特定類型上的 `x:Key`。定義這類屬性的類型都應該以 <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 屬性化。</span><span class="sxs-lookup"><span data-stu-id="93805-124">Frameworks might implement aliased key properties to substitute for `x:Key` on particular types; types that define such properties should be attributed with <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span></span>  
  
 <span data-ttu-id="93805-125">指定 `x:Key` 的相同程式碼，也就是用於基礎 <xref:System.Collections.IDictionary> 的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93805-125">The code equivalent of specifying `x:Key` is the key that is used for the underlying <xref:System.Collections.IDictionary>.</span></span> <span data-ttu-id="93805-126">例如，套用在 WPF 內資源之標記中的 `x:Key`，就等同於在程式碼中將資源加入至 WPF <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> 時，<xref:System.Windows.ResourceDictionary> 的 `key` 參數值。</span><span class="sxs-lookup"><span data-stu-id="93805-126">For example, an `x:Key` that is applied in markup for a resource in WPF is equivalent to the value of the `key` parameter of <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> when you add the resource to a WPF <xref:System.Windows.ResourceDictionary> in code.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="93805-127">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="93805-127">WPF Usage Notes</span></span>  
 <span data-ttu-id="93805-128">做為父物件的子物件，如果是 <xref:System.Collections.IDictionary> 實作，像是 WPF <xref:System.Windows.ResourceDictionary>，通常必須包含 `x:Key` 屬性，而且索引鍵值在字典內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="93805-128">Child objects of a parent object that is an <xref:System.Collections.IDictionary> implementation, such as the WPF <xref:System.Windows.ResourceDictionary>, must typically include an `x:Key` attribute, and the key value must be unique within that dictionary.</span></span> <span data-ttu-id="93805-129">有兩個值得注意的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="93805-129">There are two notable exceptions:</span></span>  
  
- <span data-ttu-id="93805-130">一些 WPF 類型宣告字典使用方式的隱含索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93805-130">Some WPF types declare an implicit key for dictionary usage.</span></span> <span data-ttu-id="93805-131">例如，具有 <xref:System.Windows.Style> 的 <xref:System.Windows.Style.TargetType%2A>，或是具有 <xref:System.Windows.DataTemplate> 的 <xref:System.Windows.DataTemplate.DataType%2A>，都可位在 <xref:System.Windows.ResourceDictionary> 中，並使用隱含機碼。</span><span class="sxs-lookup"><span data-stu-id="93805-131">For example, a <xref:System.Windows.Style> with a <xref:System.Windows.Style.TargetType%2A>, or a <xref:System.Windows.DataTemplate> with a <xref:System.Windows.DataTemplate.DataType%2A>, can be  in a <xref:System.Windows.ResourceDictionary> and use the implicit key.</span></span>  
  
- <span data-ttu-id="93805-132">WPF 支援合併的資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="93805-132">WPF supports a merged resource dictionary concept.</span></span> <span data-ttu-id="93805-133">索引鍵可以在合併的字典之間共用，而且可以使用 <xref:System.Windows.FrameworkContentElement.FindResource%2A> 來存取共用的索引鍵行為。</span><span class="sxs-lookup"><span data-stu-id="93805-133">Keys can be shared between the merged dictionaries, and the shared key behavior can be accessed using <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span></span> <span data-ttu-id="93805-134">如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="93805-134">For more information, see [Merged Resource Dictionaries](../wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
 <span data-ttu-id="93805-135">在整體 WPF XAML 實作和應用程式模型中，XAML 標記編譯器不會檢查索引鍵唯一性。</span><span class="sxs-lookup"><span data-stu-id="93805-135">In the overall WPF XAML implementation and application model, key uniqueness is not checked by the XAML markup compiler.</span></span> <span data-ttu-id="93805-136">反之，缺少或非唯一`x:Key`值會導致載入時間 XAML 剖析器錯誤。</span><span class="sxs-lookup"><span data-stu-id="93805-136">Instead, missing or nonunique `x:Key` values cause load-time XAML parser errors.</span></span> <span data-ttu-id="93805-137">不過，Visual Studio WPF 的字典處理，通常可以在設計階段中注意這類錯誤。</span><span class="sxs-lookup"><span data-stu-id="93805-137">However, Visual Studio handling of dictionaries for WPF can often note such errors in the design phase.</span></span>  
  
 <span data-ttu-id="93805-138">請注意，在以下語法中，在 WPF XAML 處理器產生集合以填入 <xref:System.Windows.ResourceDictionary> 集合的過程中，<xref:System.Windows.FrameworkElement.Resources%2A> 物件是隱含的。</span><span class="sxs-lookup"><span data-stu-id="93805-138">Note that in the syntax shown, the <xref:System.Windows.ResourceDictionary> object is implicit in how the WPF XAML processor produces a collection to populate a <xref:System.Windows.FrameworkElement.Resources%2A> collection.</span></span> <span data-ttu-id="93805-139"><xref:System.Windows.ResourceDictionary> 通常不會在標記中明確提供為項目，雖然在某些情況下，可以於必要時提供以避免困擾 (它會是 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性項目與其內部填入字典的項目之間的集合物件項目)。</span><span class="sxs-lookup"><span data-stu-id="93805-139">A <xref:System.Windows.ResourceDictionary> is not typically provided explicitly as an element in markup, although it can be in some cases if wanted for clarity (it would be a collection object element between the <xref:System.Windows.FrameworkElement.Resources%2A> property element and the items within that populate the dictionary).</span></span> <span data-ttu-id="93805-140">如需集合物件幾乎一律是標記中隱含元素的原因資訊，請參閱[XAML 語法詳細資料](../wpf/advanced/xaml-syntax-in-detail.md)。</span><span class="sxs-lookup"><span data-stu-id="93805-140">For information about why a collection object is almost always an implicit element in markup, see [XAML Syntax In Detail](../wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
 <span data-ttu-id="93805-141">在 WPF XAML 的實作中，資源字典索引鍵的處理是由 <xref:System.Windows.ResourceKey> 抽象類別所定義。</span><span class="sxs-lookup"><span data-stu-id="93805-141">In the WPF XAML implementation, the handling for resource dictionary keys is defined by the <xref:System.Windows.ResourceKey> abstract class.</span></span> <span data-ttu-id="93805-142">不過，WPF XAML 處理器會根據索引鍵的使用方式，產生不同的基礎擴充類型。</span><span class="sxs-lookup"><span data-stu-id="93805-142">However the WPF XAML processor produces different underlying extension types for keys based on their usages.</span></span> <span data-ttu-id="93805-143">例如，<xref:System.Windows.DataTemplate> 或任何衍生類別的索引鍵都是分開處理的，並會產生不同的 <xref:System.Windows.DataTemplateKey> 物件。</span><span class="sxs-lookup"><span data-stu-id="93805-143">For example, the key for a <xref:System.Windows.DataTemplate> or any derived class is handled separately, and produces a distinct <xref:System.Windows.DataTemplateKey> object.</span></span>  
  
 <span data-ttu-id="93805-144">索引鍵和名稱使用基本 XAML 定義中的不同指示詞和語言項目 ( `x:Key` 與 `x:Name` 的比較)。</span><span class="sxs-lookup"><span data-stu-id="93805-144">Keys and names use different directives and language elements (`x:Key` versus `x:Name`) in the basic XAML definition.</span></span> <span data-ttu-id="93805-145">索引鍵和名稱也會在不同的情況下，由 WPF 定義和這些概念的應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="93805-145">Keys and names are also used in different situations by the WPF definition and application of these concepts.</span></span> <span data-ttu-id="93805-146">如需詳細資訊，請參閱[WPF XAML 名稱範圍](../wpf/advanced/wpf-xaml-namescopes.md)。</span><span class="sxs-lookup"><span data-stu-id="93805-146">For details, see [WPF XAML Namescopes](../wpf/advanced/wpf-xaml-namescopes.md).</span></span>  
  
 <span data-ttu-id="93805-147">如先前所述，機碼的值可以透過標記延伸提供，並成為字串值以外的值。</span><span class="sxs-lookup"><span data-stu-id="93805-147">As stated previously, the value of a key can be supplied through a markup extension and can be other than a string value.</span></span> <span data-ttu-id="93805-148">WPF 案例的範例是 `x:Key` 的值可能是[ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="93805-148">An example WPF scenario is that the value of `x:Key` may be a [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md).</span></span> <span data-ttu-id="93805-149">某些控制項會針對影響控制項之外觀及行為部分，而不取代樣式的自訂樣式資源，公開該類型的樣式索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93805-149">Certain controls expose a style key of that type for a custom style resource that influences part of the appearance and behavior of that control without totally replacing the style.</span></span> <span data-ttu-id="93805-150">這類索引鍵的範例有 <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="93805-150">An example of such a key is <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span></span>  
  
 <span data-ttu-id="93805-151">WPF 合併字典功能對於索引鍵唯一性和索引鍵查閱行為，引入了額外的考量。</span><span class="sxs-lookup"><span data-stu-id="93805-151">The WPF merged dictionary feature introduces additional considerations for key uniqueness and key lookup behavior.</span></span> <span data-ttu-id="93805-152">如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="93805-152">For more information, see [Merged Resource Dictionaries](../wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="93805-153">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="93805-153">XAML 2009</span></span>  
 <span data-ttu-id="93805-154">XAML 2009 放寬一定會在屬性格式中提供 `x:Key` 的限制。</span><span class="sxs-lookup"><span data-stu-id="93805-154">XAML 2009 relaxes the restriction that `x:Key` always be provided in attribute form.</span></span>  
  
 <span data-ttu-id="93805-155">在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于未編譯標記的 XAML。</span><span class="sxs-lookup"><span data-stu-id="93805-155">In WPF, you can use XAML 2009 features, but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="93805-156">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="93805-156">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="93805-157">在 XAML 2009 底下，您可以透過下列用法指定 `x:Key` 元素：</span><span class="sxs-lookup"><span data-stu-id="93805-157">Under XAML 2009, you can specify `x:Key` elements through the following usage:</span></span>  
  
### <a name="xaml-element-usage-xaml-2009-only"></a><span data-ttu-id="93805-158">XAML 項目使用方式 (僅適用於 XAML 2009)</span><span class="sxs-lookup"><span data-stu-id="93805-158">XAML Element Usage (XAML 2009 only)</span></span>  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a><span data-ttu-id="93805-159">XAML 值</span><span class="sxs-lookup"><span data-stu-id="93805-159">XAML Values</span></span>  
  
|||  
|-|-|  
|`keyObject`|<span data-ttu-id="93805-160">在特殊字典中做為指定 `object` 的索引鍵之物件的物件項目。</span><span class="sxs-lookup"><span data-stu-id="93805-160">Object element for the object that is used as the key for a given `object` in a specialized dictionary.</span></span>|  
  
- <span data-ttu-id="93805-161">這裡不會顯示這種用途的容器/父代。</span><span class="sxs-lookup"><span data-stu-id="93805-161">The container/parent for this kind of use is not shown here.</span></span> <span data-ttu-id="93805-162">`object` 必須是某個表示特製化字典實作之物件項目的子代。</span><span class="sxs-lookup"><span data-stu-id="93805-162">`object` is expected to be a child of an object element that represents a specialized dictionary implementation.</span></span> <span data-ttu-id="93805-163">`keyObject` 應該是物件執行個體 (或實值類型的值)，而且適當做為該特定特殊字典實作的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93805-163">`keyObject` is expected to be an object instance (or a value of a value type) that is appropriate as the key for that particular specialized dictionary implementation.</span></span>  
  
- <span data-ttu-id="93805-164">WPF 不會實作需要這種使用方式的字典。</span><span class="sxs-lookup"><span data-stu-id="93805-164">WPF does not implement dictionaries that require this usage.</span></span> <span data-ttu-id="93805-165">物件索引鍵是更廣泛的 XAML 語言功能，可能適用於需要在 XAML 中建立字典的某些自訂字典案例。</span><span class="sxs-lookup"><span data-stu-id="93805-165">Object keys is more a general feature of the XAML language, possibly useful for certain custom dictionary scenarios where creating the dictionary in XAML is desirable.</span></span> <span data-ttu-id="93805-166">若為 WPF 功能 (例如使用資源非字串索引鍵的隱含樣式)，會有其他建立或指定索引鍵的技術存在，因此不需使用物件索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93805-166">For WPF features such as implicit styles that use non-string keys for resources, other techniques for establishing or specifying the keys exist, so using an object key is not necessary.</span></span>  
  
- <span data-ttu-id="93805-167">*keyObject*也可以是物件元素表單中的標記延伸使用方式，而不是直接物件實例。</span><span class="sxs-lookup"><span data-stu-id="93805-167">*keyObject* could also be a markup extension usage in object element form, rather than a direct object instance.</span></span>  
  
## <a name="silverlight-usage-notes"></a><span data-ttu-id="93805-168">Silverlight 使用方式備註</span><span class="sxs-lookup"><span data-stu-id="93805-168">Silverlight Usage Notes</span></span>  
 <span data-ttu-id="93805-169">Silverlight 的 `x:Key` 會在其他篇幅中做說明。</span><span class="sxs-lookup"><span data-stu-id="93805-169">`x:Key` for Silverlight is documented separately.</span></span> <span data-ttu-id="93805-170">如需詳細資訊，請參閱[XAML 命名空間（x：）語言功能（Silverlight）](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。</span><span class="sxs-lookup"><span data-stu-id="93805-170">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93805-171">請參閱</span><span class="sxs-lookup"><span data-stu-id="93805-171">See also</span></span>

- [<span data-ttu-id="93805-172">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="93805-172">XAML Resources</span></span>](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="93805-173">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="93805-173">Resources and Code</span></span>](../wpf/advanced/resources-and-code.md)
- [<span data-ttu-id="93805-174">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="93805-174">StaticResource Markup Extension</span></span>](../wpf/advanced/staticresource-markup-extension.md)
