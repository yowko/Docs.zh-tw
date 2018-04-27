---
title: XAML 中的泛型
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e64224edcb49d5040332b7cef9649c98cf26798b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="generics-in-xaml"></a><span data-ttu-id="00b9d-102">XAML 中的泛型</span><span class="sxs-lookup"><span data-stu-id="00b9d-102">Generics in XAML</span></span>
<span data-ttu-id="00b9d-103">.NET Framework XAML 服務實作於 System.Xaml 中提供支援使用泛型的 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="00b9d-103">The .NET Framework XAML Services as implemented in System.Xaml provides support for using generic CLR types.</span></span> <span data-ttu-id="00b9d-104">這項支援包括指定的條件約束的泛型型別引數，並強制執行條件約束，藉由呼叫適當`Add`泛型集合的情況下的方法。</span><span class="sxs-lookup"><span data-stu-id="00b9d-104">This support includes specifying the constraints of generics as a type argument and enforcing the constraint by calling the appropriate `Add` method for generic collection cases.</span></span> <span data-ttu-id="00b9d-105">本主題描述使用，並參考 XAML 中的泛型類型的層面。</span><span class="sxs-lookup"><span data-stu-id="00b9d-105">This topic describes aspects of using and referencing generic types in XAML.</span></span>  
  
## <a name="xtypearguments"></a><span data-ttu-id="00b9d-106">x: TypeArguments</span><span class="sxs-lookup"><span data-stu-id="00b9d-106">x:TypeArguments</span></span>  
 <span data-ttu-id="00b9d-107">`x:TypeArguments` XAML 語言所定義的指示詞。</span><span class="sxs-lookup"><span data-stu-id="00b9d-107">`x:TypeArguments` is a directive defined by the XAML language.</span></span> <span data-ttu-id="00b9d-108">使用泛型類型，支援將 XAML 類型的成員時`x:TypeArguments`類型引數的泛型支援建構函式的條件約束的傳遞。</span><span class="sxs-lookup"><span data-stu-id="00b9d-108">When it is used as a member of a XAML type that is backed by a generic type, `x:TypeArguments` passes constraining type arguments of the generic to the backing constructor.</span></span> <span data-ttu-id="00b9d-109">適用於.NET Framework XAML 服務的參考語法使用`x:TypeArguments`，其中包括語法範例，請參閱[X:typearguments 指示詞](../../../docs/framework/xaml-services/x-typearguments-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="00b9d-109">For reference syntax that pertains to .NET Framework XAML Services use of `x:TypeArguments`, which includes syntax examples, see [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
 <span data-ttu-id="00b9d-110">因為`x:TypeArguments`取用一個字串，且具有類型轉換子的支援，它通常在做為屬性的 XAML 用法中宣告。</span><span class="sxs-lookup"><span data-stu-id="00b9d-110">Because `x:TypeArguments` takes a string, and has type converter backing, it is typically declared in XAML usage as an attribute.</span></span>  
  
 <span data-ttu-id="00b9d-111">XAML 節點資料流中的資訊則是由宣告`x:TypeArguments`可以取自<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>在`StartObject`節點資料流中的位置。</span><span class="sxs-lookup"><span data-stu-id="00b9d-111">In the XAML node stream, the information declared by `x:TypeArguments` can be obtained from <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> at a `StartObject` position in the node stream.</span></span> <span data-ttu-id="00b9d-112">傳回值<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>是一份<xref:System.Xaml.XamlType>值。</span><span class="sxs-lookup"><span data-stu-id="00b9d-112">The return value of <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> is a list of <xref:System.Xaml.XamlType> values.</span></span> <span data-ttu-id="00b9d-113">判斷 XAML 型別是否代表泛型型別可透過呼叫<xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="00b9d-113">Determination of whether a XAML type represents a generic type can be made by calling <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a><span data-ttu-id="00b9d-114">規則和 XAML 的泛用的語法慣例</span><span class="sxs-lookup"><span data-stu-id="00b9d-114">Rules and Syntax Conventions for Generics in XAML</span></span>  
 <span data-ttu-id="00b9d-115">在 XAML 中，泛型型別必須永遠會表示為受條件約束的泛型;受條件約束的泛型永遠不會在 XAML 類型系統或 XAML 節點資料流中且無法在 XAML 標記中。</span><span class="sxs-lookup"><span data-stu-id="00b9d-115">In XAML, a generic type must always be represented as a constrained generic; an unconstrained generic is never present in the XAML type system or a XAML node stream and cannot be represented in XAML markup.</span></span> <span data-ttu-id="00b9d-116">XAML 屬性語法的情況，它所參考的泛型的巢狀的類型條件約束內可以參考泛型`x:TypeArguments`，或者是其中`x:Type`提供泛型型別的 CLR 型別參考。</span><span class="sxs-lookup"><span data-stu-id="00b9d-116">A generic can be referenced within XAML attribute syntax, for cases where it is a nested type constraint of a generic being referenced by `x:TypeArguments`, or for cases where `x:Type` supplies a CLR type reference for a generic type.</span></span> <span data-ttu-id="00b9d-117">這透過支援<xref:System.Xaml.Schema.XamlTypeTypeConverter>.NET Framework XAML 服務所定義的類別。</span><span class="sxs-lookup"><span data-stu-id="00b9d-117">This is supported through the <xref:System.Xaml.Schema.XamlTypeTypeConverter> class defined by .NET Framework XAML Services.</span></span>  
  
 <span data-ttu-id="00b9d-118">XAML 屬性語法形式啟用<xref:System.Xaml.Schema.XamlTypeTypeConverter>改變一般 MSIL CLR 語法慣例，會使用角括號的類型和條件約束的泛型，並改為替代條件約束的容器的括號。</span><span class="sxs-lookup"><span data-stu-id="00b9d-118">The XAML attribute syntax form enabled by <xref:System.Xaml.Schema.XamlTypeTypeConverter> alters the typical MSIL / CLR syntax convention that uses angle brackets for types and constraints of generics, and instead substitutes parentheses for the constraint container.</span></span> <span data-ttu-id="00b9d-119">如需範例，請參閱[X:typearguments 指示詞](../../../docs/framework/xaml-services/x-typearguments-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="00b9d-119">For an example, see [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
## <a name="generics-and-xaml-2009-features"></a><span data-ttu-id="00b9d-120">泛型和 XAML 2009 功能</span><span class="sxs-lookup"><span data-stu-id="00b9d-120">Generics and XAML 2009 Features</span></span>  
 <span data-ttu-id="00b9d-121">如果您使用 XAML 2009 而不是將 CLR 對應基底類型，以取得通用語言基本類型的 XAML 型別，您可以使用[XAML 2009 的內建型別](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)為中的資訊項目`x:TypeArguments`。</span><span class="sxs-lookup"><span data-stu-id="00b9d-121">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [XAML 2009 built-in types](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) as information items in `x:TypeArguments`.</span></span> <span data-ttu-id="00b9d-122">例如，您可以宣告下列 (前置詞對應不會顯示，但`x`是 XAML 2009 的 XAML 語言 XAML 命名空間):</span><span class="sxs-lookup"><span data-stu-id="00b9d-122">For example, you could declare the following (prefix mappings not shown, but `x` is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a><span data-ttu-id="00b9d-123">WPF 和其他 v3.5 架構中的泛型支援</span><span class="sxs-lookup"><span data-stu-id="00b9d-123">Generics Support in WPF and Other v3.5 Frameworks</span></span>  
 <span data-ttu-id="00b9d-124">特別以 WPF 為目標時，XAML 2006 使用量[X:class](../../../docs/framework/xaml-services/x-class-directive.md)也必須在相同的項目，做為提供`x:TypeArguments`，與該項目必須是 XAML 文件中的根項目。</span><span class="sxs-lookup"><span data-stu-id="00b9d-124">For XAML 2006 usage when specifically targeting WPF, [x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element as `x:TypeArguments`, and that element must be the root element in a XAML document.</span></span> <span data-ttu-id="00b9d-125">根項目必須具有至少一個型別引數的泛型型別對應。</span><span class="sxs-lookup"><span data-stu-id="00b9d-125">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="00b9d-126">範例是<xref:System.Windows.Navigation.PageFunction%601>。</span><span class="sxs-lookup"><span data-stu-id="00b9d-126">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span>  
  
 <span data-ttu-id="00b9d-127">可能的因應措施，以支援一般用法包括定義自訂標記延伸可傳回泛型型別，或提供換行類別衍生自泛型型別，但將在類別定義中的泛型條件約束的定義。</span><span class="sxs-lookup"><span data-stu-id="00b9d-127">Possible workarounds to support generic usages include defining a custom markup extension that can return generic types, or providing a wrapping class definition that derives from a generic type but flattens the generic constraint in its own class definition.</span></span>  
  
 <span data-ttu-id="00b9d-128">在 WPF 和目標[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，您可以使用 XAML 2009 功能與搭配`x:TypeArguments`，但僅針對鬆散的 XAML (未標記編譯 XAML)。</span><span class="sxs-lookup"><span data-stu-id="00b9d-128">In WPF and targeting [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], you can use XAML 2009 features together with `x:TypeArguments`, but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="00b9d-129">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="00b9d-129">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="00b9d-130">自訂工作流程中的 Windows Workflow Foundation[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]不支援泛型的 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="00b9d-130">Custom workflows in Windows Workflow Foundation for [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] do not support generic XAML usage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b9d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00b9d-131">See Also</span></span>  
 [<span data-ttu-id="00b9d-132">x:TypeArguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="00b9d-132">x:TypeArguments Directive</span></span>](../../../docs/framework/xaml-services/x-typearguments-directive.md)  
 [<span data-ttu-id="00b9d-133">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="00b9d-133">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="00b9d-134">通用 XAML 語言基本類型的內建類型</span><span class="sxs-lookup"><span data-stu-id="00b9d-134">Built-in Types for Common XAML Language Primitives</span></span>](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
