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
ms.openlocfilehash: 430ab65af52282ccb1d429cd2523efe213f13609
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543547"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="541ad-102">x:TypeArguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="541ad-102">x:TypeArguments Directive</span></span>

<span data-ttu-id="541ad-103">將泛型的條件約束類型引數傳遞至泛型型別的函式。</span><span class="sxs-lookup"><span data-stu-id="541ad-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="541ad-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="541ad-104">XAML Attribute Usage</span></span>

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="541ad-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="541ad-105">XAML Values</span></span>

|||
|-|-|
|`object`|<span data-ttu-id="541ad-106">XAML 型別的物件元素宣告，由 CLR 泛型型別支援。</span><span class="sxs-lookup"><span data-stu-id="541ad-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="541ad-107">如果 `object` 參考不是來自預設 xaml 命名空間的 xaml 型別，則 `object` 需要前置詞來表示 xaml 命名空間（如果 `object` 有的話）。</span><span class="sxs-lookup"><span data-stu-id="541ad-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|
|`typeString`|<span data-ttu-id="541ad-108">將一或多個 XAML 型別名稱宣告為字串的字串，它會提供 CLR 泛型型別的型別引數。</span><span class="sxs-lookup"><span data-stu-id="541ad-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="541ad-109">如需其他語法注意事項，請參閱備註。</span><span class="sxs-lookup"><span data-stu-id="541ad-109">See Remarks for additional syntax notes.</span></span>|

## <a name="remarks"></a><span data-ttu-id="541ad-110">備註</span><span class="sxs-lookup"><span data-stu-id="541ad-110">Remarks</span></span>

<span data-ttu-id="541ad-111">在大部分的情況下，當做字串中的資訊專案使用的 XAML 型別會加上前置詞 `typeString` 。</span><span class="sxs-lookup"><span data-stu-id="541ad-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="541ad-112">例如，CLR 泛型條件約束的一般類型 (， <xref:System.Int32> 而 <xref:System.String>) 來自 CLR 基類庫。</span><span class="sxs-lookup"><span data-stu-id="541ad-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="541ad-113">這些程式庫不會對應至一般架構特定的預設 XAML 命名空間，因此需要 XAML 使用的前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="541ad-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>

<span data-ttu-id="541ad-114">您可以使用逗號分隔符號指定一個以上的 XAML 類型名稱。</span><span class="sxs-lookup"><span data-stu-id="541ad-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>

<span data-ttu-id="541ad-115">如果泛型條件約束本身使用泛型型別，則可以使用括弧 ( # A1 來包含嵌套的條件約束型別引數。</span><span class="sxs-lookup"><span data-stu-id="541ad-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>

<span data-ttu-id="541ad-116">請注意，這個定義 `x:TypeArguments` 是 .NET XAML 服務和使用 CLR 支援的特定。</span><span class="sxs-lookup"><span data-stu-id="541ad-116">Note that this definition of `x:TypeArguments` is specific to .NET XAML Services and using CLR backing.</span></span> <span data-ttu-id="541ad-117">您可以在[ \[ 5.3.11 的 MS XAML \] 區段](/previous-versions/msp-n-p/ff650760(v=pandp.10))中找到語言層級定義。</span><span class="sxs-lookup"><span data-stu-id="541ad-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="usage-examples"></a><span data-ttu-id="541ad-118">使用方式範例</span><span class="sxs-lookup"><span data-stu-id="541ad-118">Usage Examples</span></span>

<span data-ttu-id="541ad-119">在這些範例中，假設已宣告下列 XAML 命名空間定義：</span><span class="sxs-lookup"><span data-stu-id="541ad-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a><span data-ttu-id="541ad-120">清單\<String></span><span class="sxs-lookup"><span data-stu-id="541ad-120">List\<String></span></span>

<span data-ttu-id="541ad-121">`<scg:List x:TypeArguments="sys:String" ...>`<xref:System.Collections.Generic.List%601>使用型別引數具現化新的 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="541ad-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>

### <a name="dictionarystringstring"></a><span data-ttu-id="541ad-122">字典\<String,String></span><span class="sxs-lookup"><span data-stu-id="541ad-122">Dictionary\<String,String></span></span>

<span data-ttu-id="541ad-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`<xref:System.Collections.Generic.Dictionary%602>以兩個型別引數具現化新的 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="541ad-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>

### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="541ad-124">佇列<KeyValuePair\<String,String>></span><span class="sxs-lookup"><span data-stu-id="541ad-124">Queue<KeyValuePair\<String,String>></span></span>

<span data-ttu-id="541ad-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`<xref:System.Collections.Generic.Queue%601>具現化具有 <xref:System.Collections.Generic.KeyValuePair%602> 具有內部條件約束類型引數和之條件約束的新 <xref:System.String> <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="541ad-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="541ad-126">XAML 2006 和 WPF 泛型 XAML 用法</span><span class="sxs-lookup"><span data-stu-id="541ad-126">XAML 2006 and WPF Generic XAML Usages</span></span>

<span data-ttu-id="541ad-127">針對 WPF 應用程式使用的 XAML 2006 使用方式和 XAML，通常會對 `x:TypeArguments` xaml 和泛型型別用法有下列限制：</span><span class="sxs-lookup"><span data-stu-id="541ad-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>

- <span data-ttu-id="541ad-128">只有 XAML 檔案的根項目可以支援參考泛型型別的一般 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="541ad-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>

- <span data-ttu-id="541ad-129">根項目必須對應至具有至少一個型別引數的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="541ad-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="541ad-130">例如 <xref:System.Windows.Navigation.PageFunction%601>。</span><span class="sxs-lookup"><span data-stu-id="541ad-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="541ad-131">頁面函式是 WPF 中 XAML 一般使用方式支援的主要案例。</span><span class="sxs-lookup"><span data-stu-id="541ad-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>

- <span data-ttu-id="541ad-132">泛型的根項目 XAML 物件元素也必須使用宣告部分類別 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="541ad-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="541ad-133">即使定義 WPF 組建動作也是如此。</span><span class="sxs-lookup"><span data-stu-id="541ad-133">This is true even if defining a WPF build action.</span></span>

- <span data-ttu-id="541ad-134">`x:TypeArguments` 無法參考嵌套泛型條件約束。</span><span class="sxs-lookup"><span data-stu-id="541ad-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="541ad-135">XAML 2009 或 XAML 2006，沒有 WPF 3.0 或 WPF 3.5 的相依性</span><span class="sxs-lookup"><span data-stu-id="541ad-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>

<span data-ttu-id="541ad-136">在 XAML 2006 或 XAML 2009 的 .NET XAML 服務中，會放寬對泛型 XAML 用法的 WPF 相關限制。</span><span class="sxs-lookup"><span data-stu-id="541ad-136">In .NET XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="541ad-137">您可以在支援型別系統和物件模型可支援的 XAML 標記中，于任何位置具現化泛型物件元素。</span><span class="sxs-lookup"><span data-stu-id="541ad-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>

<span data-ttu-id="541ad-138">如果您使用 XAML 2009，而不是對應 CLR 基底型別來取得通用語言基本類型的 XAML 型別，您可以使用 [通用 XAML 語言基本類型的內建類型](types-for-primitives.md) 作為中的資訊專案 `typeString` 。</span><span class="sxs-lookup"><span data-stu-id="541ad-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](types-for-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="541ad-139">例如，您可以宣告下列未顯示的 (前置詞對應，但 x 是 xaml 2009) 的 XAML 語言 XAML 命名空間：</span><span class="sxs-lookup"><span data-stu-id="541ad-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

<span data-ttu-id="541ad-140">在 WPF 中，以 .NET Framework 4 或 .NET Core 3.0 (或更新版本的) 為目標時，您可以搭配使用 XAML 2009 功能與， `x:TypeArguments` 但僅適用于不是標記編譯) 的鬆散 xaml (xaml。</span><span class="sxs-lookup"><span data-stu-id="541ad-140">In WPF and when targeting .NET Framework 4 or .NET Core 3.0 (or later), you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="541ad-141">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="541ad-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="541ad-142">如果您需要標記編譯 XAML，您必須依照 [xaml 2006 和 WPF 泛型 XAML 使用](#xaml-2006-and-wpf-generic-xaml-usages) 方式一節中所述的限制來操作。</span><span class="sxs-lookup"><span data-stu-id="541ad-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the [XAML 2006 and WPF Generic XAML Usages](#xaml-2006-and-wpf-generic-xaml-usages) section.</span></span> <span data-ttu-id="541ad-143">只有 .NET Framework 才支援 BAML。</span><span class="sxs-lookup"><span data-stu-id="541ad-143">BAML is only supported in .NET Framework.</span></span>

## <a name="see-also"></a><span data-ttu-id="541ad-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="541ad-144">See also</span></span>

- [<span data-ttu-id="541ad-145">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="541ad-145">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="541ad-146">x:Type 標記延伸</span><span class="sxs-lookup"><span data-stu-id="541ad-146">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="541ad-147">通用 XAML 語言基本類型的內建類型</span><span class="sxs-lookup"><span data-stu-id="541ad-147">Built-in Types for Common XAML Language Primitives</span></span>](types-for-primitives.md)
- [<span data-ttu-id="541ad-148">XAML 中的泛型</span><span class="sxs-lookup"><span data-stu-id="541ad-148">Generics in XAML</span></span>](generics.md)
