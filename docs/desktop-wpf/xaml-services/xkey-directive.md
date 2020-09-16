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
ms.openlocfilehash: 7e4e9cbded01297818f9f01df01e95e94d7dc4af
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548269"
---
# <a name="xkey-directive"></a><span data-ttu-id="69f05-102">x:Key 指示詞</span><span class="sxs-lookup"><span data-stu-id="69f05-102">x:Key Directive</span></span>
<span data-ttu-id="69f05-103">唯一識別在 XAML 定義字典中建立及參考的元素。</span><span class="sxs-lookup"><span data-stu-id="69f05-103">Uniquely identifies elements that are created and referenced in a XAML-defined dictionary.</span></span> <span data-ttu-id="69f05-104">將 `x:Key` 值新增至 XAML 物件專案是在資源字典中識別資源的最常見方式，例如在 WPF 中 <xref:System.Windows.ResourceDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="69f05-104">Adding an `x:Key` value to a XAML object element is the most common way to identify a resource in a resource dictionary, for example in a WPF <xref:System.Windows.ResourceDictionary>.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="69f05-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="69f05-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a><span data-ttu-id="69f05-106">XAML 屬性使用方式 (WPF 特定的) </span><span class="sxs-lookup"><span data-stu-id="69f05-106">XAML Attribute Usage (WPF-specific)</span></span>  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="69f05-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="69f05-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`stringKeyValue`|<span data-ttu-id="69f05-108">要做為索引鍵使用的文字字串。</span><span class="sxs-lookup"><span data-stu-id="69f05-108">A text string to use as a key.</span></span> <span data-ttu-id="69f05-109">文字字串必須符合 [XamlName 文法](xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="69f05-109">The text string must conform to the [XamlName Grammar](xamlname-grammar.md).</span></span>|  
|`markupExtensionUsage`|<span data-ttu-id="69f05-110">在標記延伸分隔符號內 {} ，標記延伸使用方式會提供要作為索引鍵使用的物件。</span><span class="sxs-lookup"><span data-stu-id="69f05-110">Within the markup extension delimiters {}, a markup extension usage that provides an object to use as a key.</span></span> <span data-ttu-id="69f05-111">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="69f05-111">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69f05-112">備註</span><span class="sxs-lookup"><span data-stu-id="69f05-112">Remarks</span></span>  
 <span data-ttu-id="69f05-113">`x:Key` 支援 XAML 資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="69f05-113">`x:Key` supports the XAML resource dictionary concept.</span></span> <span data-ttu-id="69f05-114">XAML 做為語言不會定義資源字典的執行，而是留給特定的 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="69f05-114">XAML as a language doesn't define a resource dictionary implementation, that is left to specific UI frameworks.</span></span> <span data-ttu-id="69f05-115">若要深入瞭解如何在 WPF 中執行 XAML 資源字典，請參閱 [Xaml 資源](../fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="69f05-115">To learn more about how XAML resource dictionaries are implemented in WPF, see [XAML Resources](../fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="69f05-116">在 XAML 2006 和 WPF 中， `x:Key` 必須提供為屬性。</span><span class="sxs-lookup"><span data-stu-id="69f05-116">In XAML 2006 and WPF, `x:Key` must be provided as an attribute.</span></span> <span data-ttu-id="69f05-117">您仍然可以使用非字串索引鍵，但這需要標記延伸使用方式，才能在屬性表單中提供非字串值。</span><span class="sxs-lookup"><span data-stu-id="69f05-117">You can still use nonstring keys, but this requires a markup extension usage in order to provide the nonstring value in attribute form.</span></span> <span data-ttu-id="69f05-118">如果您使用 XAML 2009， `x:Key` 可以指定為專案，以明確支援字串以外的物件類型，而不需要標記延伸的中間。</span><span class="sxs-lookup"><span data-stu-id="69f05-118">If you are using XAML 2009, `x:Key` can be specified as an element, to explicitly support dictionaries keyed by object types other than strings without requiring a markup extension intermediate.</span></span> <span data-ttu-id="69f05-119">請參閱本主題中的「XAML 2009」一節。</span><span class="sxs-lookup"><span data-stu-id="69f05-119">See the "XAML 2009" section in this topic.</span></span> <span data-ttu-id="69f05-120">[備註] 區段的其餘部分特別適用于 XAML 2006 的執行。</span><span class="sxs-lookup"><span data-stu-id="69f05-120">The remainder of the Remarks section applies specifically to the XAML 2006 implementation.</span></span>  
  
 <span data-ttu-id="69f05-121">的屬性值 `x:Key` 可以是 [XamlName 文法](xamlname-grammar.md) 中定義的任何字串，也可以是透過標記延伸評估的物件。</span><span class="sxs-lookup"><span data-stu-id="69f05-121">The attribute value of `x:Key` can be any string defined in the [XamlName Grammar](xamlname-grammar.md) or can be an object evaluated through a markup extension.</span></span> <span data-ttu-id="69f05-122">如需 WPF 的範例，請參閱「WPF 使用注意事項」。</span><span class="sxs-lookup"><span data-stu-id="69f05-122">See "WPF Usage Notes" for an example from WPF.</span></span>  
  
 <span data-ttu-id="69f05-123">實作為實作為父項目的子專案 <xref:System.Collections.IDictionary> 通常必須包含 `x:Key` 屬性，該屬性會指定該字典內的唯一索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="69f05-123">Child elements of a parent element that is an <xref:System.Collections.IDictionary> implementation must typically include an `x:Key` attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="69f05-124">架構可能會執行別名索引鍵屬性來替代 `x:Key` 特定類型; 定義這類屬性的類型應使用屬性 <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="69f05-124">Frameworks might implement aliased key properties to substitute for `x:Key` on particular types; types that define such properties should be attributed with <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span></span>  
  
 <span data-ttu-id="69f05-125">指定的程式碼對等專案 `x:Key` 是用於基礎的索引鍵 <xref:System.Collections.IDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="69f05-125">The code equivalent of specifying `x:Key` is the key that is used for the underlying <xref:System.Collections.IDictionary>.</span></span> <span data-ttu-id="69f05-126">例如，在 `x:Key` wpf 的資源標記中套用的會相當於 `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> 當您 <xref:System.Windows.ResourceDictionary> 在程式碼中將資源新增至 WPF 時的參數值。</span><span class="sxs-lookup"><span data-stu-id="69f05-126">For example, an `x:Key` that is applied in markup for a resource in WPF is equivalent to the value of the `key` parameter of <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> when you add the resource to a WPF <xref:System.Windows.ResourceDictionary> in code.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="69f05-127">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="69f05-127">WPF Usage Notes</span></span>  
 <span data-ttu-id="69f05-128">父物件的子物件（ <xref:System.Collections.IDictionary> 例如 WPF <xref:System.Windows.ResourceDictionary> ）通常必須包含 `x:Key` 屬性，而且索引鍵值在該字典中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="69f05-128">Child objects of a parent object that is an <xref:System.Collections.IDictionary> implementation, such as the WPF <xref:System.Windows.ResourceDictionary>, must typically include an `x:Key` attribute, and the key value must be unique within that dictionary.</span></span> <span data-ttu-id="69f05-129">有兩個值得注意的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="69f05-129">There are two notable exceptions:</span></span>  
  
- <span data-ttu-id="69f05-130">某些 WPF 類型會宣告隱含索引鍵以供字典使用。</span><span class="sxs-lookup"><span data-stu-id="69f05-130">Some WPF types declare an implicit key for dictionary usage.</span></span> <span data-ttu-id="69f05-131">例如， <xref:System.Windows.Style> 具有的 <xref:System.Windows.Style.TargetType%2A> 或 <xref:System.Windows.DataTemplate> 具有的 <xref:System.Windows.DataTemplate.DataType%2A> 可在中， <xref:System.Windows.ResourceDictionary> 並使用隱含索引鍵。</span><span class="sxs-lookup"><span data-stu-id="69f05-131">For example, a <xref:System.Windows.Style> with a <xref:System.Windows.Style.TargetType%2A>, or a <xref:System.Windows.DataTemplate> with a <xref:System.Windows.DataTemplate.DataType%2A>, can be  in a <xref:System.Windows.ResourceDictionary> and use the implicit key.</span></span>  
  
- <span data-ttu-id="69f05-132">WPF 支援合併的資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="69f05-132">WPF supports a merged resource dictionary concept.</span></span> <span data-ttu-id="69f05-133">您可以在合併的字典之間共用索引鍵，而且可以使用來存取共用金鑰行為 <xref:System.Windows.FrameworkContentElement.FindResource%2A> 。</span><span class="sxs-lookup"><span data-stu-id="69f05-133">Keys can be shared between the merged dictionaries, and the shared key behavior can be accessed using <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span></span> <span data-ttu-id="69f05-134">如需詳細資訊，請參閱[合併的資源字典](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries)。</span><span class="sxs-lookup"><span data-stu-id="69f05-134">For more information, see [Merged Resource Dictionaries](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).</span></span>  
  
 <span data-ttu-id="69f05-135">在整體 WPF XAML 的執行和應用程式模型中，XAML 標記編譯器不會檢查金鑰唯一性。</span><span class="sxs-lookup"><span data-stu-id="69f05-135">In the overall WPF XAML implementation and application model, key uniqueness is not checked by the XAML markup compiler.</span></span> <span data-ttu-id="69f05-136">相反地，遺漏或非唯一的 `x:Key` 值會造成載入時間 XAML 剖析器錯誤。</span><span class="sxs-lookup"><span data-stu-id="69f05-136">Instead, missing or nonunique `x:Key` values cause load-time XAML parser errors.</span></span> <span data-ttu-id="69f05-137">不過，WPF 的字典 Visual Studio 處理通常可以在設計階段中注意這類錯誤。</span><span class="sxs-lookup"><span data-stu-id="69f05-137">However, Visual Studio handling of dictionaries for WPF can often note such errors in the design phase.</span></span>  
  
 <span data-ttu-id="69f05-138">請注意，在顯示的語法中， <xref:System.Windows.ResourceDictionary> 物件在 WPF XAML 處理器如何產生集合以填入集合中是隱含的 <xref:System.Windows.FrameworkElement.Resources%2A> 。</span><span class="sxs-lookup"><span data-stu-id="69f05-138">Note that in the syntax shown, the <xref:System.Windows.ResourceDictionary> object is implicit in how the WPF XAML processor produces a collection to populate a <xref:System.Windows.FrameworkElement.Resources%2A> collection.</span></span> <span data-ttu-id="69f05-139"><xref:System.Windows.ResourceDictionary>通常不會明確地以標記中的元素形式提供，雖然在某些情況下，如果需要清楚起見 (它會是 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性專案與在中填入字典) 內之專案之間的 collection 物件專案。</span><span class="sxs-lookup"><span data-stu-id="69f05-139">A <xref:System.Windows.ResourceDictionary> is not typically provided explicitly as an element in markup, although it can be in some cases if wanted for clarity (it would be a collection object element between the <xref:System.Windows.FrameworkElement.Resources%2A> property element and the items within that populate the dictionary).</span></span> <span data-ttu-id="69f05-140">如需集合物件在標記中幾乎一律是隱含元素的詳細資訊，請參閱 [XAML 語法詳細資料](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail)。</span><span class="sxs-lookup"><span data-stu-id="69f05-140">For information about why a collection object is almost always an implicit element in markup, see [XAML Syntax In Detail](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail).</span></span>  
  
 <span data-ttu-id="69f05-141">在 WPF XAML 的執行中，資源字典索引鍵的處理是由 <xref:System.Windows.ResourceKey> 抽象類別所定義。</span><span class="sxs-lookup"><span data-stu-id="69f05-141">In the WPF XAML implementation, the handling for resource dictionary keys is defined by the <xref:System.Windows.ResourceKey> abstract class.</span></span> <span data-ttu-id="69f05-142">不過，WPF XAML 處理器會根據其使用方式，為索引鍵產生不同的基礎延伸類型。</span><span class="sxs-lookup"><span data-stu-id="69f05-142">However the WPF XAML processor produces different underlying extension types for keys based on their usages.</span></span> <span data-ttu-id="69f05-143">例如， <xref:System.Windows.DataTemplate> 或任何衍生類別的索引鍵會分開處理，並產生不同的 <xref:System.Windows.DataTemplateKey> 物件。</span><span class="sxs-lookup"><span data-stu-id="69f05-143">For example, the key for a <xref:System.Windows.DataTemplate> or any derived class is handled separately, and produces a distinct <xref:System.Windows.DataTemplateKey> object.</span></span>  
  
 <span data-ttu-id="69f05-144">`x:Key`在基本 XAML 定義中，索引鍵和名稱會使用不同的指示詞和語言元素 (與 `x:Name`) 。</span><span class="sxs-lookup"><span data-stu-id="69f05-144">Keys and names use different directives and language elements (`x:Key` versus `x:Name`) in the basic XAML definition.</span></span> <span data-ttu-id="69f05-145">WPF 定義和這些概念的應用程式也會在不同的情況下使用金鑰和名稱。</span><span class="sxs-lookup"><span data-stu-id="69f05-145">Keys and names are also used in different situations by the WPF definition and application of these concepts.</span></span> <span data-ttu-id="69f05-146">如需詳細資訊，請參閱 [WPF XAML 名稱範圍](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes)。</span><span class="sxs-lookup"><span data-stu-id="69f05-146">For details, see [WPF XAML Namescopes](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes).</span></span>  
  
 <span data-ttu-id="69f05-147">如先前所述，您可以透過標記延伸來提供索引鍵的值，而且可以是字串值以外的值。</span><span class="sxs-lookup"><span data-stu-id="69f05-147">As stated previously, the value of a key can be supplied through a markup extension and can be other than a string value.</span></span> <span data-ttu-id="69f05-148">WPF 案例的範例是，的值 `x:Key` 可能是 [ComponentResourceKey](/dotnet/desktop/wpf/advanced/componentresourcekey-markup-extension)。</span><span class="sxs-lookup"><span data-stu-id="69f05-148">An example WPF scenario is that the value of `x:Key` may be a [ComponentResourceKey](/dotnet/desktop/wpf/advanced/componentresourcekey-markup-extension).</span></span> <span data-ttu-id="69f05-149">某些控制項會公開自訂樣式資源的樣式索引鍵，該類型會影響該控制項的部分外觀和行為，而不會完全取代樣式。</span><span class="sxs-lookup"><span data-stu-id="69f05-149">Certain controls expose a style key of that type for a custom style resource that influences part of the appearance and behavior of that control without totally replacing the style.</span></span> <span data-ttu-id="69f05-150">這類索引鍵的範例為 <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A> 。</span><span class="sxs-lookup"><span data-stu-id="69f05-150">An example of such a key is <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span></span>  
  
 <span data-ttu-id="69f05-151">「WPF 合併的字典」功能會介紹索引鍵唯一性和索引鍵查閱行為的其他考慮。</span><span class="sxs-lookup"><span data-stu-id="69f05-151">The WPF merged dictionary feature introduces additional considerations for key uniqueness and key lookup behavior.</span></span> <span data-ttu-id="69f05-152">如需詳細資訊，請參閱[合併的資源字典](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries)。</span><span class="sxs-lookup"><span data-stu-id="69f05-152">For more information, see [Merged Resource Dictionaries](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="69f05-153">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="69f05-153">XAML 2009</span></span>  
 <span data-ttu-id="69f05-154">XAML 2009 放寬 `x:Key` 屬性表單中一律提供的限制。</span><span class="sxs-lookup"><span data-stu-id="69f05-154">XAML 2009 relaxes the restriction that `x:Key` always be provided in attribute form.</span></span>  
  
 <span data-ttu-id="69f05-155">在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于不是標記編譯的 XAML。</span><span class="sxs-lookup"><span data-stu-id="69f05-155">In WPF, you can use XAML 2009 features, but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="69f05-156">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="69f05-156">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="69f05-157">在 XAML 2009 下，您可以 `x:Key` 透過下列使用方式指定元素：</span><span class="sxs-lookup"><span data-stu-id="69f05-157">Under XAML 2009, you can specify `x:Key` elements through the following usage:</span></span>  
  
### <a name="xaml-element-usage-xaml-2009-only"></a><span data-ttu-id="69f05-158">XAML 元素使用 (僅限 XAML 2009) </span><span class="sxs-lookup"><span data-stu-id="69f05-158">XAML Element Usage (XAML 2009 only)</span></span>  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a><span data-ttu-id="69f05-159">XAML 值</span><span class="sxs-lookup"><span data-stu-id="69f05-159">XAML Values</span></span>  
  
|||  
|-|-|  
|`keyObject`|<span data-ttu-id="69f05-160">物件的物件專案，用來做為特製化字典中所指定的索引鍵 `object` 。</span><span class="sxs-lookup"><span data-stu-id="69f05-160">Object element for the object that is used as the key for a given `object` in a specialized dictionary.</span></span>|  
  
- <span data-ttu-id="69f05-161">這裡不會顯示這類使用的容器/父系。</span><span class="sxs-lookup"><span data-stu-id="69f05-161">The container/parent for this kind of use is not shown here.</span></span> <span data-ttu-id="69f05-162">`object` 必須是代表特製化字典之物件元素的子系。</span><span class="sxs-lookup"><span data-stu-id="69f05-162">`object` is expected to be a child of an object element that represents a specialized dictionary implementation.</span></span> <span data-ttu-id="69f05-163">`keyObject` 應該是物件實例 (或實數值型別的值，) ，適合做為該特定特製化字典的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="69f05-163">`keyObject` is expected to be an object instance (or a value of a value type) that is appropriate as the key for that particular specialized dictionary implementation.</span></span>  
  
- <span data-ttu-id="69f05-164">WPF 不會執行需要這種用法的字典。</span><span class="sxs-lookup"><span data-stu-id="69f05-164">WPF does not implement dictionaries that require this usage.</span></span> <span data-ttu-id="69f05-165">物件索引鍵是 XAML 語言的一般功能，對於在 XAML 中建立字典的特定自訂字典案例可能很有用。</span><span class="sxs-lookup"><span data-stu-id="69f05-165">Object keys is more a general feature of the XAML language, possibly useful for certain custom dictionary scenarios where creating the dictionary in XAML is desirable.</span></span> <span data-ttu-id="69f05-166">針對使用資源之非字串索引鍵的隱含樣式等 WPF 功能，有其他用來建立或指定索引鍵的技巧，因此不需要使用物件索引鍵。</span><span class="sxs-lookup"><span data-stu-id="69f05-166">For WPF features such as implicit styles that use non-string keys for resources, other techniques for establishing or specifying the keys exist, so using an object key is not necessary.</span></span>  
  
- <span data-ttu-id="69f05-167">`keyObject` 也可以是物件元素表單中的標記延伸使用方式，而不是直接物件實例。</span><span class="sxs-lookup"><span data-stu-id="69f05-167">`keyObject` could also be a markup extension usage in object element form, rather than a direct object instance.</span></span>  
  
## <a name="silverlight-usage-notes"></a><span data-ttu-id="69f05-168">Silverlight 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="69f05-168">Silverlight Usage Notes</span></span>  
 <span data-ttu-id="69f05-169">`x:Key` Silverlight 會另外記載。</span><span class="sxs-lookup"><span data-stu-id="69f05-169">`x:Key` for Silverlight is documented separately.</span></span> <span data-ttu-id="69f05-170">如需詳細資訊，請參閱 [XAML 命名空間 (x： ) 語言功能 (Silverlight) ](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。</span><span class="sxs-lookup"><span data-stu-id="69f05-170">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f05-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69f05-171">See also</span></span>

- [<span data-ttu-id="69f05-172">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="69f05-172">XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="69f05-173">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="69f05-173">Resources and Code</span></span>](/dotnet/desktop/wpf/advanced/resources-and-code)
- [<span data-ttu-id="69f05-174">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="69f05-174">StaticResource Markup Extension</span></span>](/dotnet/desktop/wpf/advanced/staticresource-markup-extension)
