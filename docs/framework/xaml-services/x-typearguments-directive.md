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
ms.openlocfilehash: 2e64c716ee85934bf02c016ee408b8e5f612a819
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837190"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="11a35-102">x:TypeArguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="11a35-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="11a35-103">將泛型的條件約束類型引數傳遞至泛型型別的處理函式。</span><span class="sxs-lookup"><span data-stu-id="11a35-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="11a35-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="11a35-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="11a35-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="11a35-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="11a35-106">XAML 類型的物件元素宣告，由 CLR 泛型型別支援。</span><span class="sxs-lookup"><span data-stu-id="11a35-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="11a35-107">如果 `object` 參考的 XAML 型別不是來自預設的 XAML 命名空間，`object` 需要前置詞來表示 `object` 存在的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="11a35-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="11a35-108">將一個或多個 XAML 類型名稱宣告為字串的字串，可提供 CLR 泛型型別的類型引數。</span><span class="sxs-lookup"><span data-stu-id="11a35-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="11a35-109">如需其他語法注意事項，請參閱備註。</span><span class="sxs-lookup"><span data-stu-id="11a35-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11a35-110">備註</span><span class="sxs-lookup"><span data-stu-id="11a35-110">Remarks</span></span>  
 <span data-ttu-id="11a35-111">在大部分情況下，做為 `typeString` 字串中的資訊專案使用的 XAML 型別會加上前置詞。</span><span class="sxs-lookup"><span data-stu-id="11a35-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="11a35-112">典型的 CLR 泛型條件約束類型（例如，<xref:System.Int32> 和 <xref:System.String>）來自 CLR 基類庫。</span><span class="sxs-lookup"><span data-stu-id="11a35-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="11a35-113">這些程式庫不會對應到一般架構特定的預設 XAML 命名空間，因此需要 XAML 用法的前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="11a35-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="11a35-114">您可以使用逗號分隔符號來指定一個以上的 XAML 類型名稱。</span><span class="sxs-lookup"><span data-stu-id="11a35-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="11a35-115">如果泛型條件約束本身使用泛型型別，則嵌套的條件約束類型引數可以包含在括弧（）內。</span><span class="sxs-lookup"><span data-stu-id="11a35-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="11a35-116">請注意，這項 `x:TypeArguments` 定義是 .NET Framework XAML 服務和使用 CLR 支援所特有。</span><span class="sxs-lookup"><span data-stu-id="11a35-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="11a35-117">您可以在[\[MS-XAML\] 區段 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))中找到語言層級定義。</span><span class="sxs-lookup"><span data-stu-id="11a35-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="11a35-118">使用方式範例</span><span class="sxs-lookup"><span data-stu-id="11a35-118">Usage Examples</span></span>  
 <span data-ttu-id="11a35-119">在這些範例中，假設已宣告下列 XAML 命名空間定義：</span><span class="sxs-lookup"><span data-stu-id="11a35-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="11a35-120">列出\<字串 ></span><span class="sxs-lookup"><span data-stu-id="11a35-120">List\<String></span></span>  
 <span data-ttu-id="11a35-121">`<scg:List x:TypeArguments="sys:String" ...>` 使用 <xref:System.String> 型別引數具現化新的 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="11a35-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="11a35-122">字典\<字串，字串 ></span><span class="sxs-lookup"><span data-stu-id="11a35-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="11a35-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` 使用兩個 <xref:System.String> 型別引數具現化新的 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="11a35-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="11a35-124">佇列 < KeyValuePair\<字串，字串 > ></span><span class="sxs-lookup"><span data-stu-id="11a35-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="11a35-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` 具現化具有內部條件約束類型引數 <xref:System.String> 和 <xref:System.String>之 <xref:System.Collections.Generic.KeyValuePair%602> 條件約束的新 <xref:System.Collections.Generic.Queue%601>。</span><span class="sxs-lookup"><span data-stu-id="11a35-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="11a35-126">XAML 2006 和 WPF 一般 XAML 用法</span><span class="sxs-lookup"><span data-stu-id="11a35-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="11a35-127">針對 XAML 2006 用法和 WPF 應用程式所使用的 XAML，一般會有下列限制： XAML 中的 `x:TypeArguments` 和一般類型使用方式。</span><span class="sxs-lookup"><span data-stu-id="11a35-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
- <span data-ttu-id="11a35-128">只有 XAML 檔案的根項目可以支援參考泛型型別的泛型 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="11a35-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
- <span data-ttu-id="11a35-129">根項目必須對應至具有至少一個型別引數的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="11a35-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="11a35-130">例如 <xref:System.Windows.Navigation.PageFunction%601>。</span><span class="sxs-lookup"><span data-stu-id="11a35-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="11a35-131">頁面函式是 WPF 中 XAML 一般使用方式支援的主要案例。</span><span class="sxs-lookup"><span data-stu-id="11a35-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
- <span data-ttu-id="11a35-132">泛型的根項目 XAML 物件元素也必須使用 `x:Class`宣告部分類別。</span><span class="sxs-lookup"><span data-stu-id="11a35-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="11a35-133">即使定義 WPF 組建動作也是如此。</span><span class="sxs-lookup"><span data-stu-id="11a35-133">This is true even if defining a WPF build action.</span></span>  
  
- <span data-ttu-id="11a35-134">`x:TypeArguments` 無法參考嵌套的泛型條件約束。</span><span class="sxs-lookup"><span data-stu-id="11a35-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="11a35-135">不含 WPF 3.0 或 WPF 3.5 相依性的 XAML 2009 或 XAML 2006</span><span class="sxs-lookup"><span data-stu-id="11a35-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="11a35-136">在 XAML 2006 或 XAML 2009 .NET Framework XAML 服務中，泛型 XAML 使用方式的 WPF 相關限制是寬鬆的。</span><span class="sxs-lookup"><span data-stu-id="11a35-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="11a35-137">您可以在 XAML 標記中，將泛型物件專案具現化，以支援型別系統和物件模型。</span><span class="sxs-lookup"><span data-stu-id="11a35-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="11a35-138">如果您使用 XAML 2009，而不是對應 CLR 基底型別來取得通用語言基本類型的 XAML 型別，您可以使用[通用 XAML 語言基本類型的內建型](built-in-types-for-common-xaml-language-primitives.md)別做為 `typeString`中的資訊專案。</span><span class="sxs-lookup"><span data-stu-id="11a35-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="11a35-139">例如，您可以宣告下列（未顯示前置詞對應，但 x 是 xaml 2009 的 xaml 語言 XAML 命名空間）：</span><span class="sxs-lookup"><span data-stu-id="11a35-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="11a35-140">在 WPF 中，以 .NET Framework 4 為目標時，您可以搭配 `x:TypeArguments` 使用 XAML 2009 功能，但僅適用于鬆散的 XAML （不是以標記編譯的 XAML）。</span><span class="sxs-lookup"><span data-stu-id="11a35-140">In WPF and when targeting .NET Framework 4, you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="11a35-141">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="11a35-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="11a35-142">如果您需要標記編譯 XAML，您必須在「XAML 2006 和 WPF 一般 XAML 使用方式」一節中所述的限制下操作。</span><span class="sxs-lookup"><span data-stu-id="11a35-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a35-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="11a35-143">See also</span></span>

- [<span data-ttu-id="11a35-144">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="11a35-144">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="11a35-145">x:Type 標記延伸模組</span><span class="sxs-lookup"><span data-stu-id="11a35-145">x:Type Markup Extension</span></span>](x-type-markup-extension.md)
- [<span data-ttu-id="11a35-146">通用 XAML 語言基本類型的內建類型</span><span class="sxs-lookup"><span data-stu-id="11a35-146">Built-in Types for Common XAML Language Primitives</span></span>](built-in-types-for-common-xaml-language-primitives.md)
- [<span data-ttu-id="11a35-147">XAML 中的泛型</span><span class="sxs-lookup"><span data-stu-id="11a35-147">Generics in XAML</span></span>](generics-in-xaml.md)
