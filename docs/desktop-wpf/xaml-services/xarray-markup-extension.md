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
ms.openlocfilehash: b332c43d7f9ffe2117c9afe1ed625c3e3c869813
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072043"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="ddfb4-102">x:Array 標記延伸</span><span class="sxs-lookup"><span data-stu-id="ddfb4-102">x:Array Markup Extension</span></span>

<span data-ttu-id="ddfb4-103">通過標記擴展為 XAML 中的物件數位提供常規支援。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="ddfb4-104">這對應於 [MS-XAML]`x:ArrayExtension`中的 XAML 類型。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="ddfb4-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="ddfb4-105">XAML Object Element Usage</span></span>

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a><span data-ttu-id="ddfb4-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="ddfb4-106">XAML Values</span></span>

|||
|-|-|
|`typeName`|<span data-ttu-id="ddfb4-107">將`x:Array`包含的類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="ddfb4-108">`typeName`對於包含 XAML 類型定義的 XAML 命名空間,可能(而且通常是)預固定。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|
|`arrayContents`|<span data-ttu-id="ddfb4-109">分配給內部`ArrayExtension.Items`屬性的項內容。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="ddfb4-110">通常,這些專案被指定為`x:Array`打開和關閉標記中包含的一個或多個物件元素。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="ddfb4-111">此處指定的物件應可分配給`typeName`中指定的 XAML 類型。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ddfb4-112">備註</span><span class="sxs-lookup"><span data-stu-id="ddfb4-112">Remarks</span></span>

<span data-ttu-id="ddfb4-113">`Type`是所有`x:Array`物件元素的必需屬性。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="ddfb4-114">參數`Type`值不需要`x:Type`使用 標記擴展,因此參數值不需要使用標記擴展。類型的短名稱是 XAML 類型,可以指定為字串。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>

<span data-ttu-id="ddfb4-115">在 .NET XAML 服務實現中,輸入 XAML<xref:System.Type>類型和創建陣列的輸出 CLR 之間的關係受標記擴展的服務上下文的影響。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-115">In .NET XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="ddfb4-116">輸出<xref:System.Type><xref:System.Xaml.XamlType.UnderlyingType%2A>是輸入 XAML 類型的輸出,在根據<xref:System.Xaml.XamlType>XAML<xref:System.Windows.Markup.IXamlTypeResolver>架構上下文和 上下文提供的服務查找所需的結果後。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="ddfb4-117">處理時,數位內容將分配給`ArrayExtension.Items`內部屬性。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="ddfb4-118">在實現中<xref:System.Windows.Markup.ArrayExtension>,這由<xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>表示 。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ddfb4-119">在 .NET XAML 服務實現中,此標記擴展<xref:System.Windows.Markup.ArrayExtension>的處理由 類定義。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-119">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="ddfb4-120"><xref:System.Windows.Markup.ArrayExtension>不密封,可用作自定義數位類型的標記擴展實現的基礎。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>

<span data-ttu-id="ddfb4-121">`x:Array`更適用於 XAML 中的一般語言擴充性。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="ddfb4-122">但是`x:Array`,對於指定某些屬性的 XAML 值也很有用,這些屬性將 XAML 支援的集合作為其結構化屬性內容。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="ddfb4-123">例如,可以指定具有<xref:System.Collections.IEnumerable>`x:Array`用法的屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>

<span data-ttu-id="ddfb4-124">`x:Array` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="ddfb4-125">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="ddfb4-126">`x:Array`部分是該規則的一個例外,因為不提供替代屬性值處理,`x:Array`而是提供對其內部文本內容的替代處理。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="ddfb4-127">此行為允許將現有內容模型可能不支援的類型分組到陣列中,並在稍後通過訪問命名陣列在代碼後面引用;您可以呼叫<xref:System.Array>方法來取得單個陣列項目。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>

<span data-ttu-id="ddfb4-128">XAML 中的所有標記擴展都使用大括弧{,}`)`( 在其屬性語法中,這是 XAML 處理器識別標記擴展必須處理屬性值的約定)。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="ddfb4-129">有關標記延伸的詳細資訊,請參考[XAML 的類型轉換器與標記延伸](type-converters-and-markup-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).</span></span>

<span data-ttu-id="ddfb4-130">在 XAML 2009`x:Array`中, 定義為語言基元而不是標記擴展。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="ddfb4-131">有關詳細資訊,請參閱常見[XAML 語言基元的內建類型](types-for-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-131">For more information, see [Built-in Types for Common XAML Language Primitives](types-for-primitives.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="ddfb4-132">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="ddfb4-132">WPF Usage Notes</span></span>

<span data-ttu-id="ddfb4-133">通常,填充的物件元素`x:Array`[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]不是 XAML 命名空間中存在的元素,需要前置碼映射到非預設 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>

<span data-ttu-id="ddfb4-134">例如,下面是兩個字串的簡單陣列,`sys`前置字串(和`x`也) 在陣列的級別上定義。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

<span data-ttu-id="ddfb4-135">對於用作陣列元素的自定義類型,類還必須支援在 XAML 中實例化為物件元素的要求。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="ddfb4-136">有關詳細資訊,請參閱[WPF 的 XAML 和自訂類別](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="ddfb4-136">For more information, see [XAML and Custom Classes for WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ddfb4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddfb4-137">See also</span></span>

- [<span data-ttu-id="ddfb4-138">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="ddfb4-138">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="ddfb4-139">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="ddfb4-139">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
