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
ms.openlocfilehash: eb9f9cc1dfdb802e340123d0d39e9c9ebaa457f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053753"
---
# <a name="xkey-directive"></a><span data-ttu-id="66cf6-102">x:Key 指示詞</span><span class="sxs-lookup"><span data-stu-id="66cf6-102">x:Key Directive</span></span>
<span data-ttu-id="66cf6-103">唯一識別在 XAML 定義的字典中所建立和參考的元素。</span><span class="sxs-lookup"><span data-stu-id="66cf6-103">Uniquely identifies elements that are created and referenced in a XAML-defined dictionary.</span></span> <span data-ttu-id="66cf6-104">將值加入至 XAML 物件專案是在資源字典中識別資源的最常見方式，例如在 WPF <xref:System.Windows.ResourceDictionary>中。 `x:Key`</span><span class="sxs-lookup"><span data-stu-id="66cf6-104">Adding an `x:Key` value to a XAML object element is the most common way to identify a resource in a resource dictionary, for example in a WPF <xref:System.Windows.ResourceDictionary>.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="66cf6-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="66cf6-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a><span data-ttu-id="66cf6-106">XAML 屬性使用方式（WPF 特定）</span><span class="sxs-lookup"><span data-stu-id="66cf6-106">XAML Attribute Usage (WPF-specific)</span></span>  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="66cf6-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="66cf6-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`stringKeyValue`|<span data-ttu-id="66cf6-108">要當做索引鍵使用的文字字串。</span><span class="sxs-lookup"><span data-stu-id="66cf6-108">A text string to use as a key.</span></span> <span data-ttu-id="66cf6-109">文字字串必須符合[XamlName 文法](xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="66cf6-109">The text string must conform to the [XamlName Grammar](xamlname-grammar.md).</span></span>|  
|`markupExtensionUsage`|<span data-ttu-id="66cf6-110">在標記延伸的分隔符號{}內，標記延伸使用方式會提供物件當做索引鍵使用。</span><span class="sxs-lookup"><span data-stu-id="66cf6-110">Within the markup extension delimiters {}, a markup extension usage that provides an object to use as a key.</span></span> <span data-ttu-id="66cf6-111">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="66cf6-111">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66cf6-112">備註</span><span class="sxs-lookup"><span data-stu-id="66cf6-112">Remarks</span></span>  
 <span data-ttu-id="66cf6-113">`x:Key`支援 XAML 資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="66cf6-113">`x:Key` supports the XAML resource dictionary concept.</span></span> <span data-ttu-id="66cf6-114">XAML 做為語言並不會定義資源字典的執行，而是留給特定的 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="66cf6-114">XAML as a language doesn't define a resource dictionary implementation, that is left to specific UI frameworks.</span></span> <span data-ttu-id="66cf6-115">若要深入瞭解如何在 WPF 中執行 XAML 資源字典，請參閱[Xaml 資源](../wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="66cf6-115">To learn more about how XAML resource dictionaries are implemented in WPF, see [XAML Resources](../wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="66cf6-116">在 XAML 2006 和 WPF 中`x:Key` ，必須以屬性的形式提供。</span><span class="sxs-lookup"><span data-stu-id="66cf6-116">In XAML 2006 and WPF, `x:Key` must be provided as an attribute.</span></span> <span data-ttu-id="66cf6-117">您仍然可以使用非字串索引鍵，但這需要標記延伸使用方式，才能在屬性格式中提供非字串值。</span><span class="sxs-lookup"><span data-stu-id="66cf6-117">You can still use nonstring keys, but this requires a markup extension usage in order to provide the nonstring value in attribute form.</span></span> <span data-ttu-id="66cf6-118">如果您使用 XAML 2009， `x:Key`可以指定為元素，以明確支援字串以外的物件類型所建立的字典，而不需要標記延伸的中繼。</span><span class="sxs-lookup"><span data-stu-id="66cf6-118">If you are using XAML 2009, `x:Key` can be specified as an element, to explicitly support dictionaries keyed by object types other than strings without requiring a markup extension intermediate.</span></span> <span data-ttu-id="66cf6-119">請參閱本主題中的「XAML 2009」一節。</span><span class="sxs-lookup"><span data-stu-id="66cf6-119">See the "XAML 2009" section in this topic.</span></span> <span data-ttu-id="66cf6-120">[備註] 區段的其餘部分會特別適用于 XAML 2006 的執行。</span><span class="sxs-lookup"><span data-stu-id="66cf6-120">The remainder of the Remarks section applies specifically to the XAML 2006 implementation.</span></span>  
  
 <span data-ttu-id="66cf6-121">的屬性值`x:Key`可以是[XamlName 文法](xamlname-grammar.md)中定義的任何字串，或者可以是透過標記延伸評估的物件。</span><span class="sxs-lookup"><span data-stu-id="66cf6-121">The attribute value of `x:Key` can be any string defined in the [XamlName Grammar](xamlname-grammar.md) or can be an object evaluated through a markup extension.</span></span> <span data-ttu-id="66cf6-122">如需 WPF 的範例，請參閱「WPF 使用方式附注」。</span><span class="sxs-lookup"><span data-stu-id="66cf6-122">See "WPF Usage Notes" for an example from WPF.</span></span>  
  
 <span data-ttu-id="66cf6-123">做為<xref:System.Collections.IDictionary>實作為執行之父元素的子項目，通常必須`x:Key`包含屬性，以指定該字典中的唯一索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="66cf6-123">Child elements of a parent element that is an <xref:System.Collections.IDictionary> implementation must typically include an `x:Key` attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="66cf6-124">架構可能會實作為`x:Key`別名索引鍵屬性，以替代特定型別，定義這類屬性的型別應該以<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>屬性化。</span><span class="sxs-lookup"><span data-stu-id="66cf6-124">Frameworks might implement aliased key properties to substitute for `x:Key` on particular types; types that define such properties should be attributed with <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span></span>  
  
 <span data-ttu-id="66cf6-125">與指定`x:Key`相等的程式碼是用於基礎<xref:System.Collections.IDictionary>的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="66cf6-125">The code equivalent of specifying `x:Key` is the key that is used for the underlying <xref:System.Collections.IDictionary>.</span></span> <span data-ttu-id="66cf6-126">例如， <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>當您`x:Key`在程式碼中將資源新增至 wpf <xref:System.Windows.ResourceDictionary>時，在 wpf 中針對資源的`key`標記所套用的會相當於的參數值。</span><span class="sxs-lookup"><span data-stu-id="66cf6-126">For example, an `x:Key` that is applied in markup for a resource in WPF is equivalent to the value of the `key` parameter of <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> when you add the resource to a WPF <xref:System.Windows.ResourceDictionary> in code.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="66cf6-127">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="66cf6-127">WPF Usage Notes</span></span>  
 <span data-ttu-id="66cf6-128">做<xref:System.Collections.IDictionary>為執行之父物件的子物件（例如 WPF <xref:System.Windows.ResourceDictionary> `x:Key` ），通常必須包含屬性，而且索引鍵值在該字典內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="66cf6-128">Child objects of a parent object that is an <xref:System.Collections.IDictionary> implementation, such as the WPF <xref:System.Windows.ResourceDictionary>, must typically include an `x:Key` attribute, and the key value must be unique within that dictionary.</span></span> <span data-ttu-id="66cf6-129">有兩個值得注意的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="66cf6-129">There are two notable exceptions:</span></span>  
  
- <span data-ttu-id="66cf6-130">某些 WPF 類型會宣告字典使用的隱含索引鍵。</span><span class="sxs-lookup"><span data-stu-id="66cf6-130">Some WPF types declare an implicit key for dictionary usage.</span></span> <span data-ttu-id="66cf6-131"><xref:System.Windows.Style>例如，具有的<xref:System.Windows.Style.TargetType%2A>或<xref:System.Windows.DataTemplate>具有<xref:System.Windows.DataTemplate.DataType%2A>的可以在中<xref:System.Windows.ResourceDictionary> ，並使用隱含索引鍵。</span><span class="sxs-lookup"><span data-stu-id="66cf6-131">For example, a <xref:System.Windows.Style> with a <xref:System.Windows.Style.TargetType%2A>, or a <xref:System.Windows.DataTemplate> with a <xref:System.Windows.DataTemplate.DataType%2A>, can be  in a <xref:System.Windows.ResourceDictionary> and use the implicit key.</span></span>  
  
- <span data-ttu-id="66cf6-132">WPF 支援合併的資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="66cf6-132">WPF supports a merged resource dictionary concept.</span></span> <span data-ttu-id="66cf6-133">金鑰可以在合併的字典之間共用，而且共用金鑰行為可以使用<xref:System.Windows.FrameworkContentElement.FindResource%2A>來存取。</span><span class="sxs-lookup"><span data-stu-id="66cf6-133">Keys can be shared between the merged dictionaries, and the shared key behavior can be accessed using <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span></span> <span data-ttu-id="66cf6-134">如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="66cf6-134">For more information, see [Merged Resource Dictionaries](../wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
 <span data-ttu-id="66cf6-135">在整體 WPF XAML 執行和應用程式模型中，XAML 標記編譯器不會檢查索引鍵的唯一性。</span><span class="sxs-lookup"><span data-stu-id="66cf6-135">In the overall WPF XAML implementation and application model, key uniqueness is not checked by the XAML markup compiler.</span></span> <span data-ttu-id="66cf6-136">相反地，遺漏或`x:Key`非唯一的值會導致載入時間 XAML 剖析器錯誤。</span><span class="sxs-lookup"><span data-stu-id="66cf6-136">Instead, missing or nonunique `x:Key` values cause load-time XAML parser errors.</span></span> <span data-ttu-id="66cf6-137">不過，Visual Studio WPF 的字典處理，通常可以在設計階段中注意這類錯誤。</span><span class="sxs-lookup"><span data-stu-id="66cf6-137">However, Visual Studio handling of dictionaries for WPF can often note such errors in the design phase.</span></span>  
  
 <span data-ttu-id="66cf6-138">請注意，在顯示的語法中<xref:System.Windows.ResourceDictionary> ，物件在 WPF XAML 處理器如何產生集合以<xref:System.Windows.FrameworkElement.Resources%2A>填入集合中是隱含的。</span><span class="sxs-lookup"><span data-stu-id="66cf6-138">Note that in the syntax shown, the <xref:System.Windows.ResourceDictionary> object is implicit in how the WPF XAML processor produces a collection to populate a <xref:System.Windows.FrameworkElement.Resources%2A> collection.</span></span> <span data-ttu-id="66cf6-139">通常不<xref:System.Windows.FrameworkElement.Resources%2A>會明確地提供為標記中的專案，不過，如果想要清楚起見，它可能在某些情況下（在屬性專案與內填入<xref:System.Windows.ResourceDictionary>字典）。</span><span class="sxs-lookup"><span data-stu-id="66cf6-139">A <xref:System.Windows.ResourceDictionary> is not typically provided explicitly as an element in markup, although it can be in some cases if wanted for clarity (it would be a collection object element between the <xref:System.Windows.FrameworkElement.Resources%2A> property element and the items within that populate the dictionary).</span></span> <span data-ttu-id="66cf6-140">如需集合物件幾乎一律是標記中隱含元素的原因資訊，請參閱[XAML 語法詳細資料](../wpf/advanced/xaml-syntax-in-detail.md)。</span><span class="sxs-lookup"><span data-stu-id="66cf6-140">For information about why a collection object is almost always an implicit element in markup, see [XAML Syntax In Detail](../wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
 <span data-ttu-id="66cf6-141">在 WPF XAML 執行中，資源字典索引鍵的處理是由<xref:System.Windows.ResourceKey>抽象類別所定義。</span><span class="sxs-lookup"><span data-stu-id="66cf6-141">In the WPF XAML implementation, the handling for resource dictionary keys is defined by the <xref:System.Windows.ResourceKey> abstract class.</span></span> <span data-ttu-id="66cf6-142">不過，WPF XAML 處理器會根據其使用方式，為金鑰產生不同的基礎延伸模組類型。</span><span class="sxs-lookup"><span data-stu-id="66cf6-142">However the WPF XAML processor produces different underlying extension types for keys based on their usages.</span></span> <span data-ttu-id="66cf6-143">例如， <xref:System.Windows.DataTemplate>或任何衍生類別的索引鍵會分別處理，並產生不同<xref:System.Windows.DataTemplateKey>的物件。</span><span class="sxs-lookup"><span data-stu-id="66cf6-143">For example, the key for a <xref:System.Windows.DataTemplate> or any derived class is handled separately, and produces a distinct <xref:System.Windows.DataTemplateKey> object.</span></span>  
  
 <span data-ttu-id="66cf6-144">索引鍵和名稱會在基本 XAML 定義中`x:Key`使用`x:Name`不同的指示詞和語言專案（與）。</span><span class="sxs-lookup"><span data-stu-id="66cf6-144">Keys and names use different directives and language elements (`x:Key` versus `x:Name`) in the basic XAML definition.</span></span> <span data-ttu-id="66cf6-145">在不同的情況下，索引鍵和名稱也會用於 WPF 定義和應用程式的這些概念。</span><span class="sxs-lookup"><span data-stu-id="66cf6-145">Keys and names are also used in different situations by the WPF definition and application of these concepts.</span></span> <span data-ttu-id="66cf6-146">如需詳細資訊，請參閱[WPF XAML 名稱範圍](../wpf/advanced/wpf-xaml-namescopes.md)。</span><span class="sxs-lookup"><span data-stu-id="66cf6-146">For details, see [WPF XAML Namescopes](../wpf/advanced/wpf-xaml-namescopes.md).</span></span>  
  
 <span data-ttu-id="66cf6-147">如先前所述，索引鍵的值可以透過標記延伸提供，而且可以不是字串值。</span><span class="sxs-lookup"><span data-stu-id="66cf6-147">As stated previously, the value of a key can be supplied through a markup extension and can be other than a string value.</span></span> <span data-ttu-id="66cf6-148">WPF 案例的範例是，的值`x:Key`可能是[ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="66cf6-148">An example WPF scenario is that the value of `x:Key` may be a [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md).</span></span> <span data-ttu-id="66cf6-149">某些控制項會公開該類型的樣式索引鍵，以影響該控制項的部分外觀和行為，而不會完全取代該樣式。</span><span class="sxs-lookup"><span data-stu-id="66cf6-149">Certain controls expose a style key of that type for a custom style resource that influences part of the appearance and behavior of that control without totally replacing the style.</span></span> <span data-ttu-id="66cf6-150">這類索引鍵的範例是<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="66cf6-150">An example of such a key is <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span></span>  
  
 <span data-ttu-id="66cf6-151">WPF 合併字典功能導入了索引鍵唯一性和索引鍵查閱行為的其他考慮。</span><span class="sxs-lookup"><span data-stu-id="66cf6-151">The WPF merged dictionary feature introduces additional considerations for key uniqueness and key lookup behavior.</span></span> <span data-ttu-id="66cf6-152">如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="66cf6-152">For more information, see [Merged Resource Dictionaries](../wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="66cf6-153">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="66cf6-153">XAML 2009</span></span>  
 <span data-ttu-id="66cf6-154">XAML 2009 放寬`x:Key`一律在屬性表單中提供的限制。</span><span class="sxs-lookup"><span data-stu-id="66cf6-154">XAML 2009 relaxes the restriction that `x:Key` always be provided in attribute form.</span></span>  
  
 <span data-ttu-id="66cf6-155">在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于未編譯標記的 XAML。</span><span class="sxs-lookup"><span data-stu-id="66cf6-155">In WPF, you can use XAML 2009 features, but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="66cf6-156">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="66cf6-156">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="66cf6-157">在 XAML 2009 底下，您可以`x:Key`透過下列用法指定元素：</span><span class="sxs-lookup"><span data-stu-id="66cf6-157">Under XAML 2009, you can specify `x:Key` elements through the following usage:</span></span>  
  
### <a name="xaml-element-usage-xaml-2009-only"></a><span data-ttu-id="66cf6-158">XAML 元素使用方式（僅限 XAML 2009）</span><span class="sxs-lookup"><span data-stu-id="66cf6-158">XAML Element Usage (XAML 2009 only)</span></span>  
  
```  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a><span data-ttu-id="66cf6-159">XAML 值</span><span class="sxs-lookup"><span data-stu-id="66cf6-159">XAML Values</span></span>  
  
|||  
|-|-|  
|`keyObject`|<span data-ttu-id="66cf6-160">物件的物件專案，這個專案會當做特定字典中指定`object`的索引鍵使用。</span><span class="sxs-lookup"><span data-stu-id="66cf6-160">Object element for the object that is used as the key for a given `object` in a specialized dictionary.</span></span>|  
  
- <span data-ttu-id="66cf6-161">這種用法的容器/父系不會顯示在這裡。</span><span class="sxs-lookup"><span data-stu-id="66cf6-161">The container/parent for this kind of use is not shown here.</span></span> <span data-ttu-id="66cf6-162">`object`應該是物件專案的子系，代表特製化的字典執行。</span><span class="sxs-lookup"><span data-stu-id="66cf6-162">`object` is expected to be a child of an object element that represents a specialized dictionary implementation.</span></span> <span data-ttu-id="66cf6-163">`keyObject`應該是物件實例（或實數值型別的值），適合做為該特定特製化字典執行的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="66cf6-163">`keyObject` is expected to be an object instance (or a value of a value type) that is appropriate as the key for that particular specialized dictionary implementation.</span></span>  
  
- <span data-ttu-id="66cf6-164">WPF 不會執行需要此用法的字典。</span><span class="sxs-lookup"><span data-stu-id="66cf6-164">WPF does not implement dictionaries that require this usage.</span></span> <span data-ttu-id="66cf6-165">物件索引鍵是 XAML 語言的一般功能，可能適用于在 XAML 中建立字典的特定自訂字典案例。</span><span class="sxs-lookup"><span data-stu-id="66cf6-165">Object keys is more a general feature of the XAML language, possibly useful for certain custom dictionary scenarios where creating the dictionary in XAML is desirable.</span></span> <span data-ttu-id="66cf6-166">針對 WPF 功能（例如使用非字串索引鍵的資源），有其他用來建立或指定索引鍵的方法存在，因此不需要使用物件索引鍵。</span><span class="sxs-lookup"><span data-stu-id="66cf6-166">For WPF features such as implicit styles that use non-string keys for resources, other techniques for establishing or specifying the keys exist, so using an object key is not necessary.</span></span>  
  
- <span data-ttu-id="66cf6-167">*keyObject*也可以是物件元素表單中的標記延伸使用方式，而不是直接物件實例。</span><span class="sxs-lookup"><span data-stu-id="66cf6-167">*keyObject* could also be a markup extension usage in object element form, rather than a direct object instance.</span></span>  
  
## <a name="silverlight-usage-notes"></a><span data-ttu-id="66cf6-168">Silverlight 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="66cf6-168">Silverlight Usage Notes</span></span>  
 <span data-ttu-id="66cf6-169">`x:Key`針對 Silverlight, 會分別記載。</span><span class="sxs-lookup"><span data-stu-id="66cf6-169">`x:Key` for Silverlight is documented separately.</span></span> <span data-ttu-id="66cf6-170">如需詳細資訊, [請參閱 XAML 命名空間 (x:)語言功能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)。</span><span class="sxs-lookup"><span data-stu-id="66cf6-170">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66cf6-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66cf6-171">See also</span></span>

- [<span data-ttu-id="66cf6-172">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="66cf6-172">XAML Resources</span></span>](../wpf/advanced/xaml-resources.md)
- [<span data-ttu-id="66cf6-173">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="66cf6-173">Resources and Code</span></span>](../wpf/advanced/resources-and-code.md)
- [<span data-ttu-id="66cf6-174">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="66cf6-174">StaticResource Markup Extension</span></span>](../wpf/advanced/staticresource-markup-extension.md)
