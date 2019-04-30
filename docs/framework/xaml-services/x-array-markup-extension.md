---
title: x:Array 標記延伸
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: 4f4e26eb3e5ccaf66b2173c7fc9952375c5f2a58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025401"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="beb56-102">x:Array 標記延伸</span><span class="sxs-lookup"><span data-stu-id="beb56-102">x:Array Markup Extension</span></span>
<span data-ttu-id="beb56-103">支援一般的 XAML 中透過標記延伸的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="beb56-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="beb56-104">這會對應至`x:ArrayExtension`[MS-XAML] 中的 XAML 型別。</span><span class="sxs-lookup"><span data-stu-id="beb56-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="beb56-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="beb56-105">XAML Object Element Usage</span></span>  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="beb56-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="beb56-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`typeName`|<span data-ttu-id="beb56-107">型別的名稱，您`x:Array`會包含。</span><span class="sxs-lookup"><span data-stu-id="beb56-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="beb56-108">`typeName` 可能 （而且通常是） 做為前置詞的 XAML 命名空間包含的 XAML 型別定義。</span><span class="sxs-lookup"><span data-stu-id="beb56-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|  
|`arrayContents`|<span data-ttu-id="beb56-109">指派給內建函式的項目內容`ArrayExtension.Items`屬性。</span><span class="sxs-lookup"><span data-stu-id="beb56-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="beb56-110">一般而言，這些項目會指定為中所包含的一或多個物件元素`x:Array`開頭和結尾標記。</span><span class="sxs-lookup"><span data-stu-id="beb56-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="beb56-111">物件可讓您指定這裡預期要在指定的 XAML 型別指派`typeName`。</span><span class="sxs-lookup"><span data-stu-id="beb56-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="beb56-112">備註</span><span class="sxs-lookup"><span data-stu-id="beb56-112">Remarks</span></span>  
 <span data-ttu-id="beb56-113">`Type` 為所有的必要的屬性`x:Array`物件項目。</span><span class="sxs-lookup"><span data-stu-id="beb56-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="beb56-114">A`Type`參數值就不需要使用`x:Type`標記延伸，短期的型別名稱是 XAML 型別，可指定為字串。</span><span class="sxs-lookup"><span data-stu-id="beb56-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>  
  
 <span data-ttu-id="beb56-115">在.NET Framework XAML 服務實作中，輸入的 XAML 型別與 CLR 的輸出之間的關係<xref:System.Type>的建立的陣列會影響標記延伸的服務內容。</span><span class="sxs-lookup"><span data-stu-id="beb56-115">In the .NET Framework XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="beb56-116">輸出<xref:System.Type>是<xref:System.Xaml.XamlType.UnderlyingType%2A>輸入 XAML 型別之後尋找必要,<xref:System.Xaml.XamlType>根據 XAML 結構描述內容和<xref:System.Windows.Markup.IXamlTypeResolver>內容提供的服務。</span><span class="sxs-lookup"><span data-stu-id="beb56-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="beb56-117">陣列內容處理時，會指派給`ArrayExtension.Items`內建屬性。</span><span class="sxs-lookup"><span data-stu-id="beb56-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="beb56-118">在 <xref:System.Windows.Markup.ArrayExtension>實作，這由<xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="beb56-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="beb56-119">在.NET Framework XAML 服務實作中，這個標記延伸的處理由定義<xref:System.Windows.Markup.ArrayExtension>類別。</span><span class="sxs-lookup"><span data-stu-id="beb56-119">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="beb56-120"><xref:System.Windows.Markup.ArrayExtension> 不密封格式，而且無法用於做為基礎標記延伸實作自訂的陣列類型。</span><span class="sxs-lookup"><span data-stu-id="beb56-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>  
  
 <span data-ttu-id="beb56-121">`x:Array` 是多個適用於一般 XAML 中的語言擴充性。</span><span class="sxs-lookup"><span data-stu-id="beb56-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="beb56-122">但`x:Array`也可用於指定 XAML 的採用，XAML 支援集合做為其結構化的屬性內容的特定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="beb56-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="beb56-123">例如，您可以在其中指定的內容<xref:System.Collections.IEnumerable>屬性與`x:Array`使用量。</span><span class="sxs-lookup"><span data-stu-id="beb56-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>  
  
 <span data-ttu-id="beb56-124">`x:Array` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="beb56-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="beb56-125">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="beb56-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="beb56-126">`x:Array` 有一部分是該規則的例外狀況因為而不是提供替代的屬性值的處理，`x:Array`提供替代處理其內部文字內容。</span><span class="sxs-lookup"><span data-stu-id="beb56-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="beb56-127">此行為可讓現有的內容模型分組為陣列，並存取具名的陣列; 稍後在程式碼後置中參考可能不支援的類型您可以呼叫<xref:System.Array>方法，以取得個別的陣列項目。</span><span class="sxs-lookup"><span data-stu-id="beb56-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>  
  
 <span data-ttu-id="beb56-128">在 XAML 中的所有標記延伸都使用大括號 ({,} `)`在其屬性語法中，這是用的 XAML 處理器知道某個標記延伸必須處理的屬性值的慣例。</span><span class="sxs-lookup"><span data-stu-id="beb56-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="beb56-129">如需一般的標記延伸的詳細資訊，請參閱[Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions-for-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="beb56-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions-for-xaml.md).</span></span>  
  
 <span data-ttu-id="beb56-130">在 XAML 2009`x:Array`定義為基本，而不是標記延伸的語言。</span><span class="sxs-lookup"><span data-stu-id="beb56-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="beb56-131">如需詳細資訊，請參閱 <<c0> [ 通用 XAML 語言基本類型的內建類型](built-in-types-for-common-xaml-language-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="beb56-131">For more information, see [Built-in Types for Common XAML Language Primitives](built-in-types-for-common-xaml-language-primitives.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="beb56-132">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="beb56-132">WPF Usage Notes</span></span>  
 <span data-ttu-id="beb56-133">通常，填入的物件項目`x:Array`不存在於的項目[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]XAML 命名空間，而且需要非預設 XAML 命名空間的前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="beb56-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>  
  
 <span data-ttu-id="beb56-134">例如，以下是簡單陣列的兩個字串，與`sys`前置詞 (以及`x`) 定義層級的陣列。</span><span class="sxs-lookup"><span data-stu-id="beb56-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>  
  
 <span data-ttu-id="beb56-135">[xaml]</span><span class="sxs-lookup"><span data-stu-id="beb56-135">[xaml]</span></span>  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 <span data-ttu-id="beb56-136">對於自訂類型做為陣列項目，此類別也必須支援的需求在 XAML 中具現化為物件項目。</span><span class="sxs-lookup"><span data-stu-id="beb56-136">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="beb56-137">如需詳細資訊，請參閱 < [XAML 和自訂類別，如 WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="beb56-137">For more information, see [XAML and Custom Classes for WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb56-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="beb56-138">See also</span></span>

- [<span data-ttu-id="beb56-139">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="beb56-139">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="beb56-140">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="beb56-140">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
