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
ms.openlocfilehash: b812939cbaa74576361de534c0d39ba45536cbcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555168"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="0278d-102">x:Array 標記延伸</span><span class="sxs-lookup"><span data-stu-id="0278d-102">x:Array Markup Extension</span></span>

<span data-ttu-id="0278d-103">透過標記延伸，在 XAML 中提供物件陣列的一般支援。</span><span class="sxs-lookup"><span data-stu-id="0278d-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="0278d-104">這會對應至 `x:ArrayExtension` [MS-xaml] 中的 XAML 類型。</span><span class="sxs-lookup"><span data-stu-id="0278d-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="0278d-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="0278d-105">XAML Object Element Usage</span></span>

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a><span data-ttu-id="0278d-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="0278d-106">XAML Values</span></span>

|||
|-|-|
|`typeName`|<span data-ttu-id="0278d-107">您將包含的型別名稱 `x:Array` 。</span><span class="sxs-lookup"><span data-stu-id="0278d-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="0278d-108">`typeName` 可能 (，且通常會) 包含 XAML 型別定義之 XAML 命名空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="0278d-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|
|`arrayContents`|<span data-ttu-id="0278d-109">指派給內部屬性的專案內容 `ArrayExtension.Items` 。</span><span class="sxs-lookup"><span data-stu-id="0278d-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="0278d-110">一般而言，這些專案會指定為 `x:Array` 開頭和結束記號中包含的一個或多個物件元素。</span><span class="sxs-lookup"><span data-stu-id="0278d-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="0278d-111">在此指定的物件應可指派給中指定的 XAML 型別 `typeName` 。</span><span class="sxs-lookup"><span data-stu-id="0278d-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0278d-112">備註</span><span class="sxs-lookup"><span data-stu-id="0278d-112">Remarks</span></span>

<span data-ttu-id="0278d-113">`Type` 是所有物件元素的必要屬性 `x:Array` 。</span><span class="sxs-lookup"><span data-stu-id="0278d-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="0278d-114">`Type`參數值不需要使用 `x:Type` 標記延伸; 類型的簡短名稱是 XAML 型別，可以指定為字串。</span><span class="sxs-lookup"><span data-stu-id="0278d-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>

<span data-ttu-id="0278d-115">在 .NET XAML 服務執行中， <xref:System.Type> 標記延伸的服務內容會影響輸入 XAML 類型與所建立陣列的輸出 CLR 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="0278d-115">In .NET XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="0278d-116"><xref:System.Type> <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType> 根據 XAML 架構內容和內容所提供的服務，查詢所需的結果之後，輸出就是輸入 XAML 型別的 <xref:System.Windows.Markup.IXamlTypeResolver> 。</span><span class="sxs-lookup"><span data-stu-id="0278d-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="0278d-117">處理時，會將陣列內容指派給內建 `ArrayExtension.Items` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0278d-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="0278d-118">在 <xref:System.Windows.Markup.ArrayExtension> 執行時，這是以表示 <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0278d-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0278d-119">在 .NET XAML 服務執行中，這個標記延伸的處理是由類別所定義 <xref:System.Windows.Markup.ArrayExtension> 。</span><span class="sxs-lookup"><span data-stu-id="0278d-119">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="0278d-120"><xref:System.Windows.Markup.ArrayExtension> 不是密封的，而且可以當做自訂陣列類型的標記延伸實作為基礎使用。</span><span class="sxs-lookup"><span data-stu-id="0278d-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>

<span data-ttu-id="0278d-121">`x:Array` 更適合 XAML 的一般語言擴充性。</span><span class="sxs-lookup"><span data-stu-id="0278d-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="0278d-122">但是 `x:Array` ，也可以用來指定特定屬性的 xaml 值，這些屬性會採用支援 xaml 的集合做為其結構化屬性內容。</span><span class="sxs-lookup"><span data-stu-id="0278d-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="0278d-123">例如，您可以使用使用方式來指定屬性的內容 <xref:System.Collections.IEnumerable> `x:Array` 。</span><span class="sxs-lookup"><span data-stu-id="0278d-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>

<span data-ttu-id="0278d-124">`x:Array` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="0278d-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="0278d-125">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="0278d-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="0278d-126">`x:Array` 部分是該規則的例外狀況，因為它不會提供替代的屬性值處理，而是會 `x:Array` 提供其內部文字內容的替代處理。</span><span class="sxs-lookup"><span data-stu-id="0278d-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="0278d-127">此行為可讓現有的內容模型不支援的型別組成陣列，並于稍後透過存取命名陣列以在程式碼後端參考該類型;您可以呼叫 <xref:System.Array> 方法來取得個別的陣列專案。</span><span class="sxs-lookup"><span data-stu-id="0278d-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>

<span data-ttu-id="0278d-128">XAML 中的所有標記延伸 {,} `)` 都會在其屬性語法中使用括弧 (，這是 xaml 處理器辨識出標記延伸必須處理屬性值的慣例。</span><span class="sxs-lookup"><span data-stu-id="0278d-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="0278d-129">如需標記延伸的一般詳細資訊，請參閱 [XAML 的類型轉換器和標記延伸](type-converters-and-markup-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="0278d-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).</span></span>

<span data-ttu-id="0278d-130">在 XAML 2009 中， `x:Array` 是定義為語言基本類型，而不是標記延伸。</span><span class="sxs-lookup"><span data-stu-id="0278d-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="0278d-131">如需詳細資訊，請參閱 [通用 XAML 語言基本類型的內建類型](types-for-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="0278d-131">For more information, see [Built-in Types for Common XAML Language Primitives](types-for-primitives.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="0278d-132">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="0278d-132">WPF Usage Notes</span></span>

<span data-ttu-id="0278d-133">一般而言，填入的物件專案 `x:Array` 不是存在於 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] xaml 命名空間中的元素，而且需要非預設 XAML 命名空間的前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="0278d-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>

<span data-ttu-id="0278d-134">例如，以下是兩個字串的簡單陣列，其中 `sys` (前置詞，也) 在 `x` 陣列層級定義。</span><span class="sxs-lookup"><span data-stu-id="0278d-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

<span data-ttu-id="0278d-135">針對當做陣列元素使用的自訂類型，類別也必須支援將 XAML 中的具現化為物件元素的需求。</span><span class="sxs-lookup"><span data-stu-id="0278d-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="0278d-136">如需詳細資訊，請參閱 [WPF 的 XAML 和自訂類別](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)。</span><span class="sxs-lookup"><span data-stu-id="0278d-136">For more information, see [XAML and Custom Classes for WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).</span></span>

## <a name="see-also"></a><span data-ttu-id="0278d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0278d-137">See also</span></span>

- [<span data-ttu-id="0278d-138">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="0278d-138">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [<span data-ttu-id="0278d-139">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="0278d-139">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
