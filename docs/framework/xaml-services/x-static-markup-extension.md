---
title: "x:Static 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
caps.latest.revision: "25"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d006c8d0937a454dcbe092dcc3e35c4644088e59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="0e465-102">x:Static 標記延伸</span><span class="sxs-lookup"><span data-stu-id="0e465-102">x:Static Markup Extension</span></span>
<span data-ttu-id="0e465-103">參考任何靜態值的程式碼實體中定義[!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– 相容的方式。</span><span class="sxs-lookup"><span data-stu-id="0e465-103">References any static by-value code entity that is defined in a [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]–compliant way.</span></span> <span data-ttu-id="0e465-104">參考的靜態屬性可以用來提供屬性，以在 XAML 中的值。</span><span class="sxs-lookup"><span data-stu-id="0e465-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="0e465-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="0e465-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="0e465-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="0e465-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`prefix`|<span data-ttu-id="0e465-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0e465-107">Optional.</span></span> <span data-ttu-id="0e465-108">是指對應、 非預設 XAML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="0e465-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="0e465-109">`prefix`顯示明確使用因為您很少會參考來自預設 XAML 命名空間的靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="0e465-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="0e465-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="0e465-110">See Remarks.</span></span>|  
|`typeName`|<span data-ttu-id="0e465-111">必要項。</span><span class="sxs-lookup"><span data-stu-id="0e465-111">Required.</span></span> <span data-ttu-id="0e465-112">定義所需的靜態成員的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0e465-112">The name of the type that defines the desired static member.</span></span>|  
|`staticMemberName`|<span data-ttu-id="0e465-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="0e465-113">Required.</span></span> <span data-ttu-id="0e465-114">（常數、 靜態屬性、 欄位或列舉值） 所需的靜態值成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="0e465-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e465-115">備註</span><span class="sxs-lookup"><span data-stu-id="0e465-115">Remarks</span></span>  
 <span data-ttu-id="0e465-116">參考的程式碼實體必須是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0e465-116">The code entity that is referenced must be one of the following:</span></span>  
  
-   <span data-ttu-id="0e465-117">常數</span><span class="sxs-lookup"><span data-stu-id="0e465-117">A constant</span></span>  
  
-   <span data-ttu-id="0e465-118">靜態屬性</span><span class="sxs-lookup"><span data-stu-id="0e465-118">A static property</span></span>  
  
-   <span data-ttu-id="0e465-119">欄位</span><span class="sxs-lookup"><span data-stu-id="0e465-119">A field</span></span>  
  
-   <span data-ttu-id="0e465-120">列舉值</span><span class="sxs-lookup"><span data-stu-id="0e465-120">An enumeration value</span></span>  
  
 <span data-ttu-id="0e465-121">指定任何其他程式碼的實體，例如非靜態屬性，會導致編譯時期錯誤，如果在 XAML 標記編譯或 XAML 的載入時間分析例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0e465-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>  
  
 <span data-ttu-id="0e465-122">您可以進行`x:Static`參考靜態欄位或屬性不在目前的 XAML 文件; 的預設 XAML 命名空間，然而，您需要的前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="0e465-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="0e465-123">XAML 命名空間幾乎一定會定義在 XAML 文件的根項目。</span><span class="sxs-lookup"><span data-stu-id="0e465-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>  
  
 <span data-ttu-id="0e465-124">靜態屬性的查閱作業只能由.NET Framework XAML 服務和 XAML 讀取器和 XAML 寫入器，在執行時都會與預設 XAML 結構描述內容。</span><span class="sxs-lookup"><span data-stu-id="0e465-124">The lookup operations for static properties can be performed by .NET Framework XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="0e465-125">此 XAML 結構描述內容可以使用 CLR 反映提供的物件圖形建構必要的靜態值。</span><span class="sxs-lookup"><span data-stu-id="0e465-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="0e465-126">`typeName`您指定實際上是 XAML 型別名稱，不是 CLR 型別名稱，雖然這些是基本上相同的名稱，或使用所有現有以 CLR 為基礎實作 XAML 的架構時使用的預設 XAML 結構描述內容。</span><span class="sxs-lookup"><span data-stu-id="0e465-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>  
  
 <span data-ttu-id="0e465-127">當您進行時請特別小心`x:Static`參考不會直接是屬性值的型別。</span><span class="sxs-lookup"><span data-stu-id="0e465-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="0e465-128">在 XAML 中處理順序，提供從標記延伸的值不會叫用其他值的轉換。</span><span class="sxs-lookup"><span data-stu-id="0e465-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="0e465-129">也是如此即使您`x:Static`參考建立文字字串，並針對該特定成員或成員的任何值傳回型別，就會發生值的轉換通常根據文字字串的屬性值。</span><span class="sxs-lookup"><span data-stu-id="0e465-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>  
  
 <span data-ttu-id="0e465-130">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="0e465-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="0e465-131">`x:Static` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.StaticExtension.Member%2A> 延伸類別的 <xref:System.Windows.Markup.StaticExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="0e465-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>  
  
 <span data-ttu-id="0e465-132">有兩個其他是可行的 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="0e465-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="0e465-133">不過，這些使用方式的較不常見，因為它們是必要的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="0e465-133">However, these usages are less common because they are unnecessarily verbose:</span></span>  
  
 <span data-ttu-id="0e465-134">**物件項目語法：** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName``" .../>`</span><span class="sxs-lookup"><span data-stu-id="0e465-134">**Object element syntax:** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName` `" .../>`</span></span>  
  
 <span data-ttu-id="0e465-135">**屬性具有明確的初始化字串的成員屬性的語法：** `<` `object`  ``  `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName``}" .../>`</span><span class="sxs-lookup"><span data-stu-id="0e465-135">**Attribute syntax with explicit Member property for initialization string:** `<` `object` `` `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName` `}" .../>`</span></span>  
  
 <span data-ttu-id="0e465-136">在.NET Framework XAML 服務實作中，這個標記延伸的處理由定義<xref:System.Windows.Markup.StaticExtension>類別。</span><span class="sxs-lookup"><span data-stu-id="0e465-136">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>  
  
 <span data-ttu-id="0e465-137">`x:Static` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="0e465-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="0e465-138">所有標記延伸在 XAML 使用`{`和`}`字元在其屬性語法中，也就是，XAML 處理器會辨識標記延伸必須提供值的慣例。</span><span class="sxs-lookup"><span data-stu-id="0e465-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="0e465-139">如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0e465-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="0e465-140">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="0e465-140">WPF Usage Notes</span></span>  
 <span data-ttu-id="0e465-141">您使用 WPF 程式設計的預設 XAML 命名空間不包含許多實用的靜態屬性，而且大部分的有用的靜態屬性會有支援，例如類型轉換器，以便使用方式，而不需要`{x:Static}`。</span><span class="sxs-lookup"><span data-stu-id="0e465-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="0e465-142">靜態屬性，您必須對應 XAML 命名空間前置詞，如果下列其中一項成立：</span><span class="sxs-lookup"><span data-stu-id="0e465-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>  
  
-   <span data-ttu-id="0e465-143">您所參考的類型存在於 WPF 中，但不是 WPF 的預設 XAML 命名空間的一部分 ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="0e465-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]).</span></span> <span data-ttu-id="0e465-144">這是很常見的案例使用`x:Static`。</span><span class="sxs-lookup"><span data-stu-id="0e465-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="0e465-145">例如，您可能會使用`x:Static`XAML 命名空間對應至參考<xref:System>CLR 命名空間和 mscorlib 組件參考的靜態屬性才能<xref:System.Environment>類別。</span><span class="sxs-lookup"><span data-stu-id="0e465-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>  
  
-   <span data-ttu-id="0e465-146">您從自訂組件參考類型。</span><span class="sxs-lookup"><span data-stu-id="0e465-146">You are referencing a type from a custom assembly.</span></span>  
  
-   <span data-ttu-id="0e465-147">但該型別是 WPF 預設 XAML 命名空間的一部分未對應的 CLR 命名空間內參考存在於 WPF 組件的類型。</span><span class="sxs-lookup"><span data-stu-id="0e465-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="0e465-148">定義各種不同的 WPF 組件中所執行之 CLR 命名空間可到預設 XAML 命名空間對應 wpf (如需有關這個概念的詳細資訊，請參閱[XAML 命名空間和 WPF XAML 命名空間對應](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md))。</span><span class="sxs-lookup"><span data-stu-id="0e465-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="0e465-149">如果大部分的類別定義通常不適用於 XAML 中，例如組成該 CLR 命名空間，可以存在非對應的 CLR 命名空間<xref:System.Windows.Threading>。</span><span class="sxs-lookup"><span data-stu-id="0e465-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>  
  
 <span data-ttu-id="0e465-150">如需有關如何使用前置詞和 XAML 命名空間的 WPF 的詳細資訊，請參閱[XAML 命名空間和 WPF XAML 命名空間對應](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="0e465-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e465-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e465-151">See Also</span></span>  
 [<span data-ttu-id="0e465-152">x:Type 標記延伸模組</span><span class="sxs-lookup"><span data-stu-id="0e465-152">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [<span data-ttu-id="0e465-153">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="0e465-153">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
