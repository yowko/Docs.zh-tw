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
ms.openlocfilehash: 23c483daed0156dd29134b255e9da2f7922980ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492778"
---
# <a name="xkey-directive"></a><span data-ttu-id="dbe9a-102">x:Key 指示詞</span><span class="sxs-lookup"><span data-stu-id="dbe9a-102">x:Key Directive</span></span>
<span data-ttu-id="dbe9a-103">可唯一識別建立和參考 XAML 定義的字典中的項目。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-103">Uniquely identifies elements that are created and referenced in a XAML-defined dictionary.</span></span> <span data-ttu-id="dbe9a-104">新增`x:Key`XAML 物件元素的值是最常見的方式，來識別資源字典中，例如在 WPF 中的資源<xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-104">Adding an `x:Key` value to a XAML object element is the most common way to identify a resource in a resource dictionary, for example in a WPF <xref:System.Windows.ResourceDictionary>.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="dbe9a-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="dbe9a-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a><span data-ttu-id="dbe9a-106">XAML 屬性使用方式 （特定於 WPF）</span><span class="sxs-lookup"><span data-stu-id="dbe9a-106">XAML Attribute Usage (WPF-specific)</span></span>  
  
```  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="dbe9a-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="dbe9a-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`stringKeyValue`|<span data-ttu-id="dbe9a-108">文字字串做為索引鍵使用。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-108">A text string to use as a key.</span></span> <span data-ttu-id="dbe9a-109">文字字串必須符合[XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-109">The text string must conform to the [XamlName Grammar](../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span>|  
|`markupExtensionUsage`|<span data-ttu-id="dbe9a-110">標記延伸分隔符號內{}，標記延伸使用方式，提供做為索引鍵的物件。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-110">Within the markup extension delimiters {}, a markup extension usage that provides an object to use as a key.</span></span> <span data-ttu-id="dbe9a-111">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-111">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbe9a-112">備註</span><span class="sxs-lookup"><span data-stu-id="dbe9a-112">Remarks</span></span>  
 <span data-ttu-id="dbe9a-113">`x:Key` 支援 XAML 資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-113">`x:Key` supports the XAML resource dictionary concept.</span></span> <span data-ttu-id="dbe9a-114">XAML 作為語言未定義的資源字典實作，保留給特定的 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-114">XAML as a language doesn't define a resource dictionary implementation, that is left to specific UI frameworks.</span></span> <span data-ttu-id="dbe9a-115">若要深入了解如何在 WPF 中實作 XAML 資源字典，請參閱[XAML 資源](../../../docs/framework/wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-115">To learn more about how XAML resource dictionaries are implemented in WPF, see [XAML Resources](../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="dbe9a-116">在 XAML 2006 和 WPF，`x:Key`必須提供做為屬性。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-116">In XAML 2006 and WPF, `x:Key` must be provided as an attribute.</span></span> <span data-ttu-id="dbe9a-117">您仍然可以使用非字串索引鍵，但這需要標記延伸使用方式，才能提供以屬性形式的非字串值。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-117">You can still use nonstring keys, but this requires a markup extension usage in order to provide the nonstring value in attribute form.</span></span> <span data-ttu-id="dbe9a-118">如果您使用 XAML 2009`x:Key`都可以指定為項目，以明確支援以外的其他索引的物件類型的字典字串而不需要標記延伸中繼。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-118">If you are using XAML 2009, `x:Key` can be specified as an element, to explicitly support dictionaries keyed by object types other than strings without requiring a markup extension intermediate.</span></span> <span data-ttu-id="dbe9a-119">請參閱本主題的 < XAML 2009 > 一節。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-119">See the "XAML 2009" section in this topic.</span></span> <span data-ttu-id="dbe9a-120">< 備註 > 一節的其餘部分專門適用於 XAML 2006 實作。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-120">The remainder of the Remarks section applies specifically to the XAML 2006 implementation.</span></span>  
  
 <span data-ttu-id="dbe9a-121">屬性值`x:Key`可以任何字串中定義[XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)也可以是透過標記延伸評估的物件。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-121">The attribute value of `x:Key` can be any string defined in the [XamlName Grammar](../../../docs/framework/xaml-services/xamlname-grammar.md) or can be an object evaluated through a markup extension.</span></span> <span data-ttu-id="dbe9a-122">如需 WPF 的範例，請參閱 < WPF 使用方式附註 >。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-122">See "WPF Usage Notes" for an example from WPF.</span></span>  
  
 <span data-ttu-id="dbe9a-123">是父項目的子項目<xref:System.Collections.IDictionary>通常必須包含實作`x:Key`指定該字典內的唯一索引鍵值的屬性。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-123">Child elements of a parent element that is an <xref:System.Collections.IDictionary> implementation must typically include an `x:Key` attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="dbe9a-124">架構可能會實作別名索引鍵屬性，來替代`x:Key`特定類型上定義這類屬性的類型應該屬性具有<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-124">Frameworks might implement aliased key properties to substitute for `x:Key` on particular types; types that define such properties should be attributed with <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span></span>  
  
 <span data-ttu-id="dbe9a-125">指定的相同程式碼`x:Key`是用於基礎的索引鍵<xref:System.Collections.IDictionary>。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-125">The code equivalent of specifying `x:Key` is the key that is used for the underlying <xref:System.Collections.IDictionary>.</span></span> <span data-ttu-id="dbe9a-126">例如， `x:Key` WPF 中的資源是相當於值套用在標記中`key`參數<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>當您將資源加入 WPF<xref:System.Windows.ResourceDictionary>在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-126">For example, an `x:Key` that is applied in markup for a resource in WPF is equivalent to the value of the `key` parameter of <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> when you add the resource to a WPF <xref:System.Windows.ResourceDictionary> in code.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="dbe9a-127">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="dbe9a-127">WPF Usage Notes</span></span>  
 <span data-ttu-id="dbe9a-128">也就是物件的父系的子物件<xref:System.Collections.IDictionary>實作，例如 WPF <xref:System.Windows.ResourceDictionary>，通常必須包含`x:Key`屬性，而且索引鍵值內必須是唯一的字典。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-128">Child objects of a parent object that is an <xref:System.Collections.IDictionary> implementation, such as the WPF <xref:System.Windows.ResourceDictionary>, must typically include an `x:Key` attribute, and the key value must be unique within that dictionary.</span></span> <span data-ttu-id="dbe9a-129">有兩個值得注意的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="dbe9a-129">There are two notable exceptions:</span></span>  
  
-   <span data-ttu-id="dbe9a-130">一些 WPF 類型宣告字典使用方式的隱含索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-130">Some WPF types declare an implicit key for dictionary usage.</span></span> <span data-ttu-id="dbe9a-131">比方說，<xref:System.Windows.Style>具有<xref:System.Windows.Style.TargetType%2A>，或<xref:System.Windows.DataTemplate>具有<xref:System.Windows.DataTemplate.DataType%2A>，可以是<xref:System.Windows.ResourceDictionary>，並使用隱含的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-131">For example, a <xref:System.Windows.Style> with a <xref:System.Windows.Style.TargetType%2A>, or a <xref:System.Windows.DataTemplate> with a <xref:System.Windows.DataTemplate.DataType%2A>, can be  in a <xref:System.Windows.ResourceDictionary> and use the implicit key.</span></span>  
  
-   <span data-ttu-id="dbe9a-132">WPF 支援合併的資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-132">WPF supports a merged resource dictionary concept.</span></span> <span data-ttu-id="dbe9a-133">金鑰可以共用之間合併的字典和可存取的共用金鑰的行為，使用<xref:System.Windows.FrameworkContentElement.FindResource%2A>。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-133">Keys can be shared between the merged dictionaries, and the shared key behavior can be accessed using <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span></span> <span data-ttu-id="dbe9a-134">如需詳細資訊，請參閱[合併的資源字典](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-134">For more information, see [Merged Resource Dictionaries](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
 <span data-ttu-id="dbe9a-135">在整體 WPF XAML 實作和應用程式模型中，XAML 標記編譯器不會檢查索引鍵唯一性。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-135">In the overall WPF XAML implementation and application model, key uniqueness is not checked by the XAML markup compiler.</span></span> <span data-ttu-id="dbe9a-136">相反地，缺少或非唯一`x:Key`值會導致載入時間 XAML 剖析器錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-136">Instead, missing or nonunique `x:Key` values cause load-time XAML parser errors.</span></span> <span data-ttu-id="dbe9a-137">不過，Visual Studio 的字典中的處理 wpf 可以通常在設計階段注意這類錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-137">However, Visual Studio handling of dictionaries for WPF can often note such errors in the design phase.</span></span>  
  
 <span data-ttu-id="dbe9a-138">請注意，在顯示的語法<xref:System.Windows.ResourceDictionary>物件是隱含在 WPF XAML 處理器如何產生集合以填入<xref:System.Windows.FrameworkElement.Resources%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-138">Note that in the syntax shown, the <xref:System.Windows.ResourceDictionary> object is implicit in how the WPF XAML processor produces a collection to populate a <xref:System.Windows.FrameworkElement.Resources%2A> collection.</span></span> <span data-ttu-id="dbe9a-139">A<xref:System.Windows.ResourceDictionary>通常並非明確為項目在標記中，但如果想為了清楚起見，也可以是在某些情況下 (它會是集合物件項目之間<xref:System.Windows.FrameworkElement.Resources%2A>屬性項目並在其中的項目填入字典）。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-139">A <xref:System.Windows.ResourceDictionary> is not typically provided explicitly as an element in markup, although it can be in some cases if wanted for clarity (it would be a collection object element between the <xref:System.Windows.FrameworkElement.Resources%2A> property element and the items within that populate the dictionary).</span></span> <span data-ttu-id="dbe9a-140">如需為什麼集合物件幾乎都是隱含的項目在標記中的資訊，請參閱[XAML 語法詳細資料](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-140">For information about why a collection object is almost always an implicit element in markup, see [XAML Syntax In Detail](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
 <span data-ttu-id="dbe9a-141">在 WPF XAML 實作中，資源字典索引鍵的處理由定義<xref:System.Windows.ResourceKey>抽象類別。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-141">In the WPF XAML implementation, the handling for resource dictionary keys is defined by the <xref:System.Windows.ResourceKey> abstract class.</span></span> <span data-ttu-id="dbe9a-142">不過，WPF XAML 處理器會產生不同的基礎擴充類型，根據其使用方式索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-142">However the WPF XAML processor produces different underlying extension types for keys based on their usages.</span></span> <span data-ttu-id="dbe9a-143">例如，索引鍵<xref:System.Windows.DataTemplate>或任何衍生的類別處理分開，而且會產生不同<xref:System.Windows.DataTemplateKey>物件。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-143">For example, the key for a <xref:System.Windows.DataTemplate> or any derived class is handled separately, and produces a distinct <xref:System.Windows.DataTemplateKey> object.</span></span>  
  
 <span data-ttu-id="dbe9a-144">索引鍵和名稱使用不同的指示詞和語言項目 (`x:Key`與`x:Name`) 基本 XAML 定義中。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-144">Keys and names use different directives and language elements (`x:Key` versus `x:Name`) in the basic XAML definition.</span></span> <span data-ttu-id="dbe9a-145">索引鍵和名稱也會在不同的情況下由 WPF 定義和這些概念的應用程式。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-145">Keys and names are also used in different situations by the WPF definition and application of these concepts.</span></span> <span data-ttu-id="dbe9a-146">如需詳細資訊，請參閱 < [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-146">For details, see [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).</span></span>  
  
 <span data-ttu-id="dbe9a-147">如先前所述，機碼的值可以透過標記延伸提供，並可以是字串值以外的值。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-147">As stated previously, the value of a key can be supplied through a markup extension and can be other than a string value.</span></span> <span data-ttu-id="dbe9a-148">WPF 即為一例，值`x:Key`可能[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-148">An example WPF scenario is that the value of `x:Key` may be a [ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).</span></span> <span data-ttu-id="dbe9a-149">特定控制項會公開該類型的樣式索引鍵，而不取代樣式影響組件的外觀和行為，該控制項的自訂樣式資源。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-149">Certain controls expose a style key of that type for a custom style resource that influences part of the appearance and behavior of that control without totally replacing the style.</span></span> <span data-ttu-id="dbe9a-150">舉例來說，這類金鑰<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-150">An example of such a key is <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span></span>  
  
 <span data-ttu-id="dbe9a-151">WPF 合併的字典功能導入了索引鍵唯一性和索引鍵查閱行為的其他考量。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-151">The WPF merged dictionary feature introduces additional considerations for key uniqueness and key lookup behavior.</span></span> <span data-ttu-id="dbe9a-152">如需詳細資訊，請參閱[合併的資源字典](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-152">For more information, see [Merged Resource Dictionaries](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="dbe9a-153">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="dbe9a-153">XAML 2009</span></span>  
 <span data-ttu-id="dbe9a-154">XAML 2009 放寬了這項限制，`x:Key`一律會以屬性形式提供。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-154">XAML 2009 relaxes the restriction that `x:Key` always be provided in attribute form.</span></span>  
  
 <span data-ttu-id="dbe9a-155">在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未標記編譯的 XAML。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-155">In WPF, you can use XAML 2009 features, but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="dbe9a-156">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-156">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="dbe9a-157">在 XAML 2009 中，您可以指定`x:Key`透過下列的使用方式的項目：</span><span class="sxs-lookup"><span data-stu-id="dbe9a-157">Under XAML 2009, you can specify `x:Key` elements through the following usage:</span></span>  
  
### <a name="xaml-element-usage-xaml-2009-only"></a><span data-ttu-id="dbe9a-158">XAML 項目使用方式 (XAML 2009)</span><span class="sxs-lookup"><span data-stu-id="dbe9a-158">XAML Element Usage (XAML 2009 only)</span></span>  
  
```  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a><span data-ttu-id="dbe9a-159">XAML 值</span><span class="sxs-lookup"><span data-stu-id="dbe9a-159">XAML Values</span></span>  
  
|||  
|-|-|  
|`keyObject`|<span data-ttu-id="dbe9a-160">用做為索引鍵之物件的物件項目指定`object`特殊字典中。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-160">Object element for the object that is used as the key for a given `object` in a specialized dictionary.</span></span>|  
  
-   <span data-ttu-id="dbe9a-161">此處未顯示這種使用容器/父代。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-161">The container/parent for this kind of use is not shown here.</span></span> <span data-ttu-id="dbe9a-162">`object` 應該是代表特殊的字典實作之物件項目的子系。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-162">`object` is expected to be a child of an object element that represents a specialized dictionary implementation.</span></span> <span data-ttu-id="dbe9a-163">`keyObject` 必須是物件執行個體 （或實值類型的值），而且適當做該特定特殊的字典實作的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-163">`keyObject` is expected to be an object instance (or a value of a value type) that is appropriate as the key for that particular specialized dictionary implementation.</span></span>  
  
-   <span data-ttu-id="dbe9a-164">WPF 不會實作需要這種使用方式的字典。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-164">WPF does not implement dictionaries that require this usage.</span></span> <span data-ttu-id="dbe9a-165">物件索引鍵是更一般 XAML 語言，可能會需要在 XAML 中建立字典某些自訂字典案例很實用的功能。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-165">Object keys is more a general feature of the XAML language, possibly useful for certain custom dictionary scenarios where creating the dictionary in XAML is desirable.</span></span> <span data-ttu-id="dbe9a-166">WPF 功能，例如使用資源非字串索引鍵的隱含樣式，其他技術，建立或指定之索引鍵存在，因此不需要使用物件索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-166">For WPF features such as implicit styles that use non-string keys for resources, other techniques for establishing or specifying the keys exist, so using an object key is not necessary.</span></span>  
  
-   <span data-ttu-id="dbe9a-167">*keyObject*也可能是物件項目表單，而不是直接物件執行個體中的標記延伸使用方式。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-167">*keyObject* could also be a markup extension usage in object element form, rather than a direct object instance.</span></span>  
  
## <a name="silverlight-usage-notes"></a><span data-ttu-id="dbe9a-168">Silverlight 使用方式附註</span><span class="sxs-lookup"><span data-stu-id="dbe9a-168">Silverlight Usage Notes</span></span>  
 <span data-ttu-id="dbe9a-169">`x:Key` silverlight 會另外記載。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-169">`x:Key` for Silverlight is documented separately.</span></span> <span data-ttu-id="dbe9a-170">如需詳細資訊，請參閱[XAML 命名空間 （x:）語言功能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)。</span><span class="sxs-lookup"><span data-stu-id="dbe9a-170">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe9a-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbe9a-171">See also</span></span>
- [<span data-ttu-id="dbe9a-172">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="dbe9a-172">XAML Resources</span></span>](../../../docs/framework/wpf/advanced/xaml-resources.md)
- [<span data-ttu-id="dbe9a-173">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="dbe9a-173">Resources and Code</span></span>](../../../docs/framework/wpf/advanced/resources-and-code.md)
- [<span data-ttu-id="dbe9a-174">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="dbe9a-174">StaticResource Markup Extension</span></span>](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
