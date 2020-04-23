---
title: x:TypeArguments 指示詞
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071350"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="1d013-102">x:TypeArguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="1d013-102">x:TypeArguments Directive</span></span>

<span data-ttu-id="1d013-103">將泛型的約束類型參數傳遞給泛型類型的構造函數。</span><span class="sxs-lookup"><span data-stu-id="1d013-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="1d013-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="1d013-104">XAML Attribute Usage</span></span>

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="1d013-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="1d013-105">XAML Values</span></span>

|||
|-|-|
|`object`|<span data-ttu-id="1d013-106">XAML 類型的物件元素聲明,由CLR泛型類型支援。</span><span class="sxs-lookup"><span data-stu-id="1d013-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="1d013-107">如果`object`引用的 XAML 類型不是來自預設的 XAML 命名空間`object`,則需要一個前`object`綴來指示存在存在的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="1d013-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|
|`typeString`|<span data-ttu-id="1d013-108">將一個或多個 XAML 類型名稱聲明為字串的字串,該字串提供 CLR 泛型類型的類型參數。</span><span class="sxs-lookup"><span data-stu-id="1d013-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="1d013-109">有關其他語法註釋,請參閱備註。</span><span class="sxs-lookup"><span data-stu-id="1d013-109">See Remarks for additional syntax notes.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1d013-110">備註</span><span class="sxs-lookup"><span data-stu-id="1d013-110">Remarks</span></span>

<span data-ttu-id="1d013-111">在大多數情況下,用作字串中的資訊項目的 XAML 型態是預`typeString`固定的 。</span><span class="sxs-lookup"><span data-stu-id="1d013-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="1d013-112">CLR 泛型約束的典型類型(<xref:System.Int32>例如<xref:System.String>和 ) 來自CLR基類庫。</span><span class="sxs-lookup"><span data-stu-id="1d013-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="1d013-113">這些庫不映射到典型的特定於框架的預設 XAML 命名空間,因此需要 XAML 用法的前置碼映射。</span><span class="sxs-lookup"><span data-stu-id="1d013-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>

<span data-ttu-id="1d013-114">可以使用逗號分隔符指定多個 XAML 類型名稱。</span><span class="sxs-lookup"><span data-stu-id="1d013-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>

<span data-ttu-id="1d013-115">如果泛型約束本身使用泛型類型,則嵌套約束類型參數可以由括弧 () 包含。</span><span class="sxs-lookup"><span data-stu-id="1d013-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>

<span data-ttu-id="1d013-116">請注意,此`x:TypeArguments`定義特定於 .NET XAML 服務並使用 CLR 支援。</span><span class="sxs-lookup"><span data-stu-id="1d013-116">Note that this definition of `x:TypeArguments` is specific to .NET XAML Services and using CLR backing.</span></span> <span data-ttu-id="1d013-117">可在[\[MS-XAML\]第 5.3.11 節中](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))找到語言級別的定義。</span><span class="sxs-lookup"><span data-stu-id="1d013-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="usage-examples"></a><span data-ttu-id="1d013-118">使用方式範例</span><span class="sxs-lookup"><span data-stu-id="1d013-118">Usage Examples</span></span>

<span data-ttu-id="1d013-119">對於這些範例,假定聲明了以下 XAML 命名空間定義:</span><span class="sxs-lookup"><span data-stu-id="1d013-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a><span data-ttu-id="1d013-120">清單\<字串></span><span class="sxs-lookup"><span data-stu-id="1d013-120">List\<String></span></span>

<span data-ttu-id="1d013-121">`<scg:List x:TypeArguments="sys:String" ...>`實體化具有類型參數的新<xref:System.Collections.Generic.List%601><xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="1d013-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>

### <a name="dictionarystringstring"></a><span data-ttu-id="1d013-122">字典\<字串,字串></span><span class="sxs-lookup"><span data-stu-id="1d013-122">Dictionary\<String,String></span></span>

<span data-ttu-id="1d013-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`實例化具有兩<xref:System.Collections.Generic.Dictionary%602><xref:System.String>個類型參數的新參數。</span><span class="sxs-lookup"><span data-stu-id="1d013-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>

### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="1d013-124">佇列<鍵值字串\<,字串>></span><span class="sxs-lookup"><span data-stu-id="1d013-124">Queue<KeyValuePair\<String,String>></span></span>

<span data-ttu-id="1d013-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`實例化具有 內部<xref:System.Collections.Generic.Queue%601>約束<xref:System.String>類型<xref:System.String><xref:System.Collections.Generic.KeyValuePair%602>參數和約束的新。</span><span class="sxs-lookup"><span data-stu-id="1d013-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="1d013-126">XAML 2006 與 WPF 通用 XAML 用法</span><span class="sxs-lookup"><span data-stu-id="1d013-126">XAML 2006 and WPF Generic XAML Usages</span></span>

<span data-ttu-id="1d013-127">對於用於 WPF 應用程式的 XAML 2006 用法和`x:TypeArguments`XAML,一般 對 XAML 和泛型類型用法存在以下限制:</span><span class="sxs-lookup"><span data-stu-id="1d013-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>

- <span data-ttu-id="1d013-128">只有 XAML 檔的根元素才能支援引用泛型類型的泛型 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="1d013-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>

- <span data-ttu-id="1d013-129">根元素必須映射到具有至少一個類型參數的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="1d013-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="1d013-130">例如 <xref:System.Windows.Navigation.PageFunction%601>。</span><span class="sxs-lookup"><span data-stu-id="1d013-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="1d013-131">頁面函數是 WPF 中 XAML 通用使用支援的主要方案。</span><span class="sxs-lookup"><span data-stu-id="1d013-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>

- <span data-ttu-id="1d013-132">泛型的根元素 XAML 物件元素還`x:Class`必須使用 聲明部分類。</span><span class="sxs-lookup"><span data-stu-id="1d013-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="1d013-133">即使定義 WPF 生成操作也是如此。</span><span class="sxs-lookup"><span data-stu-id="1d013-133">This is true even if defining a WPF build action.</span></span>

- <span data-ttu-id="1d013-134">`x:TypeArguments`不能引用嵌套的泛型約束。</span><span class="sxs-lookup"><span data-stu-id="1d013-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="1d013-135">XAML 2009 或 XAML 2006,沒有 WPF 3.0 或 WPF 3.5 依賴項</span><span class="sxs-lookup"><span data-stu-id="1d013-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>

<span data-ttu-id="1d013-136">在 .NET XAML 服務中,XAML 2006 或 XAML 2009 中,放寬了與 WPF 相關的通用 XAML 使用限制。</span><span class="sxs-lookup"><span data-stu-id="1d013-136">In .NET XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="1d013-137">您可以在支援類型系統和物件模型可以支援的任何位置實例化 XAML 標記中的任何位置的泛型物件元素。</span><span class="sxs-lookup"><span data-stu-id="1d013-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>

<span data-ttu-id="1d013-138">如果使用 XAML 2009 而不是映射 CLR 基類型以獲取通用語言基元中的 XAML 類型,則可以[將通用 XAML 語言基元的內置類型](types-for-primitives.md)用作 中的`typeString`資訊項。</span><span class="sxs-lookup"><span data-stu-id="1d013-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](types-for-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="1d013-139">例如,您可以聲明以下內容(未顯示前置碼映射,但 x 是 XAML 2009 的 XAML 語言 XAML 命名空間):</span><span class="sxs-lookup"><span data-stu-id="1d013-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

<span data-ttu-id="1d013-140">在 WPF 中,當定位 .NET 框架 4 或 .NET Core 3.0(或更高版本)時,`x:TypeArguments`您可以將 XAML 2009 功能與鬆散的 XAML(未標記編譯的 XAML)一起使用,但僅限於這些功能。</span><span class="sxs-lookup"><span data-stu-id="1d013-140">In WPF and when targeting .NET Framework 4 or .NET Core 3.0 (or later), you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="1d013-141">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="1d013-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="1d013-142">如果需要標記編譯 XAML,則必須在[XAML 2006 和 WPF 通用 XAML 用法](#xaml-2006-and-wpf-generic-xaml-usages)部分中所述的限制下操作。</span><span class="sxs-lookup"><span data-stu-id="1d013-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the [XAML 2006 and WPF Generic XAML Usages](#xaml-2006-and-wpf-generic-xaml-usages) section.</span></span> <span data-ttu-id="1d013-143">BAML 僅在 .NET 框架中受支援。</span><span class="sxs-lookup"><span data-stu-id="1d013-143">BAML is only supported in .NET Framework.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d013-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d013-144">See also</span></span>

- [<span data-ttu-id="1d013-145">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="1d013-145">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="1d013-146">x:Type 標記延伸</span><span class="sxs-lookup"><span data-stu-id="1d013-146">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="1d013-147">通用 XAML 語言基本類型的內建類型</span><span class="sxs-lookup"><span data-stu-id="1d013-147">Built-in Types for Common XAML Language Primitives</span></span>](types-for-primitives.md)
- [<span data-ttu-id="1d013-148">XAML 中的泛型</span><span class="sxs-lookup"><span data-stu-id="1d013-148">Generics in XAML</span></span>](generics.md)
