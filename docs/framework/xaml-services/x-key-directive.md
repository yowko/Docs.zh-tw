---
title: x:Key 指示詞
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
caps.latest.revision: 25
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f28ed1e4077a48016ddd8d9b5eeb45d6ba25d8e5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="xkey-directive"></a><span data-ttu-id="3b4e0-102">x:Key 指示詞</span><span class="sxs-lookup"><span data-stu-id="3b4e0-102">x:Key Directive</span></span>
<span data-ttu-id="3b4e0-103">可唯一識別所建立和定義 XAML 的字典中所參考的項目。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-103">Uniquely identifies elements that are created and referenced in a XAML-defined dictionary.</span></span> <span data-ttu-id="3b4e0-104">加入`x:Key`XAML 物件項目值是最常見的方式來識別資源字典，例如在 WPF 中的資源<xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-104">Adding an `x:Key` value to a XAML object element is the most common way to identify a resource in a resource dictionary, for example in a WPF <xref:System.Windows.ResourceDictionary>.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3b4e0-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="3b4e0-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a><span data-ttu-id="3b4e0-106">XAML 屬性使用方式 （特定 WPF）</span><span class="sxs-lookup"><span data-stu-id="3b4e0-106">XAML Attribute Usage (WPF-specific)</span></span>  
  
```  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3b4e0-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="3b4e0-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`stringKeyValue`|<span data-ttu-id="3b4e0-108">文字字串做為索引鍵使用。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-108">A text string to use as a key.</span></span> <span data-ttu-id="3b4e0-109">文字字串必須符合[XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-109">The text string must conform to the [XamlName Grammar](../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span>|  
|`markupExtensionUsage`|<span data-ttu-id="3b4e0-110">標記延伸分隔符號內{}，標記延伸使用方式，提供要用做為索引鍵的物件。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-110">Within the markup extension delimiters {}, a markup extension usage that provides an object to use as a key.</span></span> <span data-ttu-id="3b4e0-111">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-111">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b4e0-112">備註</span><span class="sxs-lookup"><span data-stu-id="3b4e0-112">Remarks</span></span>  
 <span data-ttu-id="3b4e0-113">`x:Key` 支援 XAML 資源字典的概念。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-113">`x:Key` supports the XAML resource dictionary concept.</span></span> <span data-ttu-id="3b4e0-114">XAML 語言未定義的資源字典實作，會保留給特定的 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-114">XAML as a language doesn't define a resource dictionary implementation, that is left to specific UI frameworks.</span></span> <span data-ttu-id="3b4e0-115">若要深入了解如何在 WPF 中實作 XAML 資源字典，請參閱[XAML 資源](../../../docs/framework/wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-115">To learn more about how XAML resource dictionaries are implemented in WPF, see [XAML Resources](../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="3b4e0-116">在 XAML 2006 和 WPF，`x:Key`必須提供做為屬性。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-116">In XAML 2006 and WPF, `x:Key` must be provided as an attribute.</span></span> <span data-ttu-id="3b4e0-117">您仍然可以使用非索引鍵，但這需要的標記延伸使用方式，才能提供以屬性形式的非字串值。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-117">You can still use nonstring keys, but this requires a markup extension usage in order to provide the nonstring value in attribute form.</span></span> <span data-ttu-id="3b4e0-118">如果您使用 XAML 2009`x:Key`都可以指定為項目，以明確地支援為索引鍵的物件類型以外的字典字串而不需要中繼標記延伸。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-118">If you are using XAML 2009, `x:Key` can be specified as an element, to explicitly support dictionaries keyed by object types other than strings without requiring a markup extension intermediate.</span></span> <span data-ttu-id="3b4e0-119">請參閱本主題的 < XAML 2009 > 一節。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-119">See the "XAML 2009" section in this topic.</span></span> <span data-ttu-id="3b4e0-120">< 備註 > 一節的其餘部分特別適用於 XAML 2006 實作。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-120">The remainder of the Remarks section applies specifically to the XAML 2006 implementation.</span></span>  
  
 <span data-ttu-id="3b4e0-121">屬性值的`x:Key`可以任何字串中定義[XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)或可以是標記延伸評估的物件。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-121">The attribute value of `x:Key` can be any string defined in the [XamlName Grammar](../../../docs/framework/xaml-services/xamlname-grammar.md) or can be an object evaluated through a markup extension.</span></span> <span data-ttu-id="3b4e0-122">如需從 WPF 範例，請參閱 < WPF 使用量注意事項 >。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-122">See "WPF Usage Notes" for an example from WPF.</span></span>  
  
 <span data-ttu-id="3b4e0-123">是父項目的子項目<xref:System.Collections.IDictionary>實作通常必須包含`x:Key`屬性來指定該字典內的唯一索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-123">Child elements of a parent element that is an <xref:System.Collections.IDictionary> implementation must typically include an `x:Key` attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="3b4e0-124">架構可能會實作具有別名的索引鍵屬性來替代`x:Key`應該具有屬性這類屬性所定義類型，針對特定類型; <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-124">Frameworks might implement aliased key properties to substitute for `x:Key` on particular types; types that define such properties should be attributed with <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span></span>  
  
 <span data-ttu-id="3b4e0-125">程式碼相當於指定`x:Key`是用於基礎的索引鍵<xref:System.Collections.IDictionary>。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-125">The code equivalent of specifying `x:Key` is the key that is used for the underlying <xref:System.Collections.IDictionary>.</span></span> <span data-ttu-id="3b4e0-126">例如， `x:Key` WPF 中的資源是相等的值套用在標記中`key`參數<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>當您將資源加入至 WPF<xref:System.Windows.ResourceDictionary>程式碼中。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-126">For example, an `x:Key` that is applied in markup for a resource in WPF is equivalent to the value of the `key` parameter of <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> when you add the resource to a WPF <xref:System.Windows.ResourceDictionary> in code.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="3b4e0-127">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="3b4e0-127">WPF Usage Notes</span></span>  
 <span data-ttu-id="3b4e0-128">也就是物件的父代的子物件<xref:System.Collections.IDictionary>實作，例如 WPF <xref:System.Windows.ResourceDictionary>，通常必須包含`x:Key`屬性及金鑰值內必須是唯一的字典。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-128">Child objects of a parent object that is an <xref:System.Collections.IDictionary> implementation, such as the WPF <xref:System.Windows.ResourceDictionary>, must typically include an `x:Key` attribute, and the key value must be unique within that dictionary.</span></span> <span data-ttu-id="3b4e0-129">有兩個值得注意的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="3b4e0-129">There are two notable exceptions:</span></span>  
  
-   <span data-ttu-id="3b4e0-130">某些 WPF 類型宣告字典使用量隱含索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-130">Some WPF types declare an implicit key for dictionary usage.</span></span> <span data-ttu-id="3b4e0-131">例如，<xref:System.Windows.Style>與<xref:System.Windows.Style.TargetType%2A>，或<xref:System.Windows.DataTemplate>與<xref:System.Windows.DataTemplate.DataType%2A>，可以採用<xref:System.Windows.ResourceDictionary>並使用隱含索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-131">For example, a <xref:System.Windows.Style> with a <xref:System.Windows.Style.TargetType%2A>, or a <xref:System.Windows.DataTemplate> with a <xref:System.Windows.DataTemplate.DataType%2A>, can be  in a <xref:System.Windows.ResourceDictionary> and use the implicit key.</span></span>  
  
-   <span data-ttu-id="3b4e0-132">WPF 支援合併的資源字典概念。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-132">WPF supports a merged resource dictionary concept.</span></span> <span data-ttu-id="3b4e0-133">合併的字典，間無法共用金鑰和共用索引鍵的行為可以使用存取<xref:System.Windows.FrameworkContentElement.FindResource%2A>。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-133">Keys can be shared between the merged dictionaries, and the shared key behavior can be accessed using <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span></span> <span data-ttu-id="3b4e0-134">如需詳細資訊，請參閱[合併的資源字典](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-134">For more information, see [Merged Resource Dictionaries](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
 <span data-ttu-id="3b4e0-135">在整體 WPF XAML 實作和應用程式模型中，XAML 標記編譯器不會檢查金鑰的唯一性。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-135">In the overall WPF XAML implementation and application model, key uniqueness is not checked by the XAML markup compiler.</span></span> <span data-ttu-id="3b4e0-136">相反地，遺漏或非唯一`x:Key`值會導致載入時間 XAML 剖析器錯誤。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-136">Instead, missing or nonunique `x:Key` values cause load-time XAML parser errors.</span></span> <span data-ttu-id="3b4e0-137">不過，WPF 字典的 Visual Studio 處理通常可以注意這類錯誤在設計階段。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-137">However, Visual Studio handling of dictionaries for WPF can often note such errors in the design phase.</span></span>  
  
 <span data-ttu-id="3b4e0-138">請注意，在語法中所示，<xref:System.Windows.ResourceDictionary>物件是在 WPF XAML 處理器會填入集合的產生隱含<xref:System.Windows.FrameworkElement.Resources%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-138">Note that in the syntax shown, the <xref:System.Windows.ResourceDictionary> object is implicit in how the WPF XAML processor produces a collection to populate a <xref:System.Windows.FrameworkElement.Resources%2A> collection.</span></span> <span data-ttu-id="3b4e0-139">A<xref:System.Windows.ResourceDictionary>通常並非明確做為項目在標記中，不過如果想更清楚，所以可能會在某些情況下 (將集合物件的項目之間<xref:System.Windows.FrameworkElement.Resources%2A>屬性項目和項目中，填入字典）。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-139">A <xref:System.Windows.ResourceDictionary> is not typically provided explicitly as an element in markup, although it can be in some cases if wanted for clarity (it would be a collection object element between the <xref:System.Windows.FrameworkElement.Resources%2A> property element and the items within that populate the dictionary).</span></span> <span data-ttu-id="3b4e0-140">如需為什麼集合物件幾乎都是在標記中的隱含項目資訊，請參閱[XAML 語法的詳細資料](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-140">For information about why a collection object is almost always an implicit element in markup, see [XAML Syntax In Detail](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
 <span data-ttu-id="3b4e0-141">在 WPF XAML 實作中，所定義的資源字典索引鍵處理<xref:System.Windows.ResourceKey>抽象類別。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-141">In the WPF XAML implementation, the handling for resource dictionary keys is defined by the <xref:System.Windows.ResourceKey> abstract class.</span></span> <span data-ttu-id="3b4e0-142">不過，WPF XAML 處理器會產生不同及其使用方法為基礎的金鑰為基礎的擴充功能類型。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-142">However the WPF XAML processor produces different underlying extension types for keys based on their usages.</span></span> <span data-ttu-id="3b4e0-143">例如，索引鍵<xref:System.Windows.DataTemplate>或任何衍生的類別會分別處理，並會產生相異<xref:System.Windows.DataTemplateKey>物件。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-143">For example, the key for a <xref:System.Windows.DataTemplate> or any derived class is handled separately, and produces a distinct <xref:System.Windows.DataTemplateKey> object.</span></span>  
  
 <span data-ttu-id="3b4e0-144">索引鍵和名稱使用不同的指示詞和語言項目 (`x:Key`與`x:Name`) 中的基本 XAML 定義。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-144">Keys and names use different directives and language elements (`x:Key` versus `x:Name`) in the basic XAML definition.</span></span> <span data-ttu-id="3b4e0-145">索引鍵和名稱也會使用在不同情況下的 WPF 定義與這些概念的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-145">Keys and names are also used in different situations by the WPF definition and application of these concepts.</span></span> <span data-ttu-id="3b4e0-146">如需詳細資訊，請參閱[WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-146">For details, see [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).</span></span>  
  
 <span data-ttu-id="3b4e0-147">如先前所述，索引鍵的值可以透過標記延伸來提供，而且可以以外的字串值。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-147">As stated previously, the value of a key can be supplied through a markup extension and can be other than a string value.</span></span> <span data-ttu-id="3b4e0-148">WPF 即為一例，值`x:Key`可能[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-148">An example WPF scenario is that the value of `x:Key` may be a[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).</span></span> <span data-ttu-id="3b4e0-149">某些控制項公開該類型之自訂樣式資源的影響而不會完全取代樣式的組件的外觀和行為，該控制項的樣式索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-149">Certain controls expose a style key of that type for a custom style resource that influences part of the appearance and behavior of that control without totally replacing the style.</span></span> <span data-ttu-id="3b4e0-150">舉例來說，這類金鑰是<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-150">An example of such a key is <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span></span>  
  
 <span data-ttu-id="3b4e0-151">WPF 合併的字典功能導入了索引鍵唯一性和索引鍵查閱行為的其他考量。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-151">The WPF merged dictionary feature introduces additional considerations for key uniqueness and key lookup behavior.</span></span> <span data-ttu-id="3b4e0-152">如需詳細資訊，請參閱[合併的資源字典](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-152">For more information, see [Merged Resource Dictionaries](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="3b4e0-153">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="3b4e0-153">XAML 2009</span></span>  
 <span data-ttu-id="3b4e0-154">XAML 2009 會放寬這項限制，`x:Key`一定會以屬性形式提供。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-154">XAML 2009 relaxes the restriction that `x:Key` always be provided in attribute form.</span></span>  
  
 <span data-ttu-id="3b4e0-155">在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未標記編譯 XAML。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-155">In WPF, you can use XAML 2009 features, but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="3b4e0-156">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-156">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="3b4e0-157">在 XAML 2009 中，您可以指定`x:Key`透過使用下列項目：</span><span class="sxs-lookup"><span data-stu-id="3b4e0-157">Under XAML 2009, you can specify `x:Key` elements through the following usage:</span></span>  
  
### <a name="xaml-element-usage-xaml-2009-only"></a><span data-ttu-id="3b4e0-158">XAML (XAML 2009) 的項目用法</span><span class="sxs-lookup"><span data-stu-id="3b4e0-158">XAML Element Usage (XAML 2009 only)</span></span>  
  
```  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a><span data-ttu-id="3b4e0-159">XAML 值</span><span class="sxs-lookup"><span data-stu-id="3b4e0-159">XAML Values</span></span>  
  
|||  
|-|-|  
|`keyObject`|<span data-ttu-id="3b4e0-160">用做為索引鍵之物件的物件項目指定`object`特製化的字典中。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-160">Object element for the object that is used as the key for a given `object` in a specialized dictionary.</span></span>|  
  
-   <span data-ttu-id="3b4e0-161">此處未顯示這種使用容器/父系。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-161">The container/parent for this kind of use is not shown here.</span></span> <span data-ttu-id="3b4e0-162">`object` 必須是代表特定的字典實作物件元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-162">`object` is expected to be a child of an object element that represents a specialized dictionary implementation.</span></span> <span data-ttu-id="3b4e0-163">`keyObject` 必須是物件執行個體 （或實值類型的值），是適當的索引鍵，該特定的特殊的字典實作。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-163">`keyObject` is expected to be an object instance (or a value of a value type) that is appropriate as the key for that particular specialized dictionary implementation.</span></span>  
  
-   <span data-ttu-id="3b4e0-164">WPF 未實作需要這種使用方式的字典。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-164">WPF does not implement dictionaries that require this usage.</span></span> <span data-ttu-id="3b4e0-165">物件索引鍵是更一般 XAML 語言，可能是適用於特定的自訂字典的情況下在 XAML 中建立字典想要的功能。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-165">Object keys is more a general feature of the XAML language, possibly useful for certain custom dictionary scenarios where creating the dictionary in XAML is desirable.</span></span> <span data-ttu-id="3b4e0-166">WPF 功能，例如使用資源的非字串索引鍵的隱含樣式，其他技術在建立或指定之索引鍵存在，因此不需要使用物件的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-166">For WPF features such as implicit styles that use non-string keys for resources, other techniques for establishing or specifying the keys exist, so using an object key is not necessary.</span></span>  
  
-   <span data-ttu-id="3b4e0-167">*keyObject*也可能是物件項目表單，而不是直接物件執行個體中的標記延伸使用方式。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-167">*keyObject* could also be a markup extension usage in object element form, rather than a direct object instance.</span></span>  
  
## <a name="silverlight-usage-notes"></a><span data-ttu-id="3b4e0-168">Silverlight 的使用方式附註</span><span class="sxs-lookup"><span data-stu-id="3b4e0-168">Silverlight Usage Notes</span></span>  
 <span data-ttu-id="3b4e0-169">`x:Key` silverlight 被說明文件。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-169">`x:Key` for Silverlight is documented separately.</span></span> <span data-ttu-id="3b4e0-170">如需詳細資訊，請參閱[XAML 命名空間 （x:）語言功能 (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081)。</span><span class="sxs-lookup"><span data-stu-id="3b4e0-170">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b4e0-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b4e0-171">See Also</span></span>  
 [<span data-ttu-id="3b4e0-172">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="3b4e0-172">XAML Resources</span></span>](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="3b4e0-173">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="3b4e0-173">Resources and Code</span></span>](../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [<span data-ttu-id="3b4e0-174">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="3b4e0-174">StaticResource Markup Extension</span></span>](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
