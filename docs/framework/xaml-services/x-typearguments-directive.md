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
ms.openlocfilehash: 28eda94914125f2c5849a471671c8e283475c82c
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268821"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="e8107-102">x:TypeArguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="e8107-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="e8107-103">限制的傳遞類型泛型型別之建構函式的泛型引的數。</span><span class="sxs-lookup"><span data-stu-id="e8107-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="e8107-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="e8107-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e8107-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="e8107-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="e8107-106">物件項目宣告的 XAML 型別，而由 CLR 的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="e8107-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="e8107-107">如果`object`不是來自預設 XAML 命名空間中，XAML 型別是指`object`需要指出 XAML 命名空間的前置詞其中`object`存在。</span><span class="sxs-lookup"><span data-stu-id="e8107-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="e8107-108">字串，其中會宣告一個或多個 XAML 類型名稱為字串，提供 CLR 的泛型類型的類型引數。</span><span class="sxs-lookup"><span data-stu-id="e8107-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="e8107-109">如需其他的語法資訊，請參閱 < 備註 >。</span><span class="sxs-lookup"><span data-stu-id="e8107-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8107-110">備註</span><span class="sxs-lookup"><span data-stu-id="e8107-110">Remarks</span></span>  
 <span data-ttu-id="e8107-111">在大部分情況下，XAML 類型做為中的資訊項目`typeString`前置詞字串。</span><span class="sxs-lookup"><span data-stu-id="e8107-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="e8107-112">一般類型的 CLR 的泛型條件約束 (例如<xref:System.Int32>和<xref:System.String>) 來自 CLR 基底類別庫。</span><span class="sxs-lookup"><span data-stu-id="e8107-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="e8107-113">這些程式庫不對應至典型架構專屬的預設 XAML 命名空間，且因此，如果需要前置詞對應的 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="e8107-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="e8107-114">您可以使用逗號分隔符號來指定一個以上的 XAML 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="e8107-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="e8107-115">如果泛型條件約束本身會使用泛型型別，可以包含巢狀條件約束的型別引數的括號 （）。</span><span class="sxs-lookup"><span data-stu-id="e8107-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="e8107-116">請注意，此定義`x:TypeArguments`專屬於.NET Framework XAML 服務，使用 CLR 支援。</span><span class="sxs-lookup"><span data-stu-id="e8107-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="e8107-117">語言層級定義可在[ \[MS XAML\]一節 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="e8107-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="e8107-118">使用範例</span><span class="sxs-lookup"><span data-stu-id="e8107-118">Usage Examples</span></span>  
 <span data-ttu-id="e8107-119">如需這些範例中，假設宣告 XAML 命名空間定義如下：</span><span class="sxs-lookup"><span data-stu-id="e8107-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="e8107-120">清單\<字串 ></span><span class="sxs-lookup"><span data-stu-id="e8107-120">List\<String></span></span>  
 <span data-ttu-id="e8107-121">`<scg:List x:TypeArguments="sys:String" ...>` 新具現化<xref:System.Collections.Generic.List%601>與<xref:System.String>型別引數。</span><span class="sxs-lookup"><span data-stu-id="e8107-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="e8107-122">字典\<字串，字串 ></span><span class="sxs-lookup"><span data-stu-id="e8107-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="e8107-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` 新具現化<xref:System.Collections.Generic.Dictionary%602>具有兩個<xref:System.String>型別引數。</span><span class="sxs-lookup"><span data-stu-id="e8107-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="e8107-124">佇列 < KeyValuePair\<String，String >></span><span class="sxs-lookup"><span data-stu-id="e8107-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="e8107-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` 新具現化<xref:System.Collections.Generic.Queue%601>具有條件約束<xref:System.Collections.Generic.KeyValuePair%602>使用內部條件約束的型別引數<xref:System.String>和<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="e8107-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="e8107-126">XAML 2006 和 WPF XAML 的一般使用方式</span><span class="sxs-lookup"><span data-stu-id="e8107-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="e8107-127">如需 XAML 2006 使用量和用於 WPF 應用程式的 XAML，有下列限制`x:TypeArguments`以及從 XAML 中一般的泛型型別使用方式：</span><span class="sxs-lookup"><span data-stu-id="e8107-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
-   <span data-ttu-id="e8107-128">只有 XAML 檔案的根項目可以支援一般的 XAML 用途，參考泛型型別。</span><span class="sxs-lookup"><span data-stu-id="e8107-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
-   <span data-ttu-id="e8107-129">根項目必須對應到至少一個類型引數的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="e8107-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="e8107-130">例如， <xref:System.Windows.Navigation.PageFunction%601>。</span><span class="sxs-lookup"><span data-stu-id="e8107-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="e8107-131">頁面函式會將一般用途支援 XAML 在 WPF 中的主要案例。</span><span class="sxs-lookup"><span data-stu-id="e8107-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
-   <span data-ttu-id="e8107-132">泛型的根項目的 XAML 物件項目也必須宣告部分類別，使用`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="e8107-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="e8107-133">這是 true，即使定義 WPF 建置動作。</span><span class="sxs-lookup"><span data-stu-id="e8107-133">This is true even if defining a WPF build action.</span></span>  
  
-   <span data-ttu-id="e8107-134">`x:TypeArguments` 不能參考巢狀的泛型條件約束。</span><span class="sxs-lookup"><span data-stu-id="e8107-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="e8107-135">XAML 2009 或不含 WPF 3.0 或 3.5 WPF 的 XAML 2006 相依性</span><span class="sxs-lookup"><span data-stu-id="e8107-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="e8107-136">在.NET Framework XAML 服務 XAML 2006 或 XAML 2009，一般 XAML 用途的 WPF 相關限制比較不嚴謹。</span><span class="sxs-lookup"><span data-stu-id="e8107-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="e8107-137">您可以具現化的支援型別系統和物件模型可支援 XAML 標記中的任何位置的一般物件項目。</span><span class="sxs-lookup"><span data-stu-id="e8107-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="e8107-138">如果您使用 XAML 2009 而不是將 CLR 對應基底型別，以取得通用語言基本類型的 XAML 型別，您可以使用[通用 XAML 語言基本類型的內建型別](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)中的資訊項目`typeString`。</span><span class="sxs-lookup"><span data-stu-id="e8107-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="e8107-139">例如，您可以宣告下列 （前置詞對應不會顯示，而 x 是 XAML 2009 的 XAML 語言 XAML 命名空間）：</span><span class="sxs-lookup"><span data-stu-id="e8107-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="e8107-140">在 WPF 中，並為目標時[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用 XAML 2009 功能，並搭配`x:TypeArguments`但只在鬆散的 XAML (未標記編譯的 XAML)。</span><span class="sxs-lookup"><span data-stu-id="e8107-140">In WPF and when targeting [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="e8107-141">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="e8107-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="e8107-142">如果您需要以標記編譯 XAML，您必須在 「 XAML 2006 和 WPF 泛型 XAML 使用方式 」 一節所述的限制下進行操作。</span><span class="sxs-lookup"><span data-stu-id="e8107-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8107-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8107-143">See Also</span></span>  
 [<span data-ttu-id="e8107-144">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="e8107-144">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="e8107-145">x:Type 標記延伸模組</span><span class="sxs-lookup"><span data-stu-id="e8107-145">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [<span data-ttu-id="e8107-146">通用 XAML 語言基本類型的內建類型</span><span class="sxs-lookup"><span data-stu-id="e8107-146">Built-in Types for Common XAML Language Primitives</span></span>](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [<span data-ttu-id="e8107-147">XAML 中的泛型</span><span class="sxs-lookup"><span data-stu-id="e8107-147">Generics in XAML</span></span>](../../../docs/framework/xaml-services/generics-in-xaml.md)
