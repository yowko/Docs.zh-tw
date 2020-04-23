---
title: XAML 中的泛型
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 9354f74b978652c36df28a91a6b9db5cfff4bb1e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071735"
---
# <a name="generics-in-xaml"></a><span data-ttu-id="dffb9-102">XAML 中的泛型</span><span class="sxs-lookup"><span data-stu-id="dffb9-102">Generics in XAML</span></span>

<span data-ttu-id="dffb9-103">.NET XAML<xref:System.Xaml?displayProperty=fullName>服務( 如實現)支援使用通用 CLR 類型。</span><span class="sxs-lookup"><span data-stu-id="dffb9-103">.NET XAML Services as implemented in <xref:System.Xaml?displayProperty=fullName> provides support for using generic CLR types.</span></span> <span data-ttu-id="dffb9-104">此支援包括指定泛型的約束作為類型參數,並通過調用泛型集合案例的適當`Add`方法來強制執行約束。</span><span class="sxs-lookup"><span data-stu-id="dffb9-104">This support includes specifying the constraints of generics as a type argument and enforcing the constraint by calling the appropriate `Add` method for generic collection cases.</span></span> <span data-ttu-id="dffb9-105">本主題介紹在 XAML 中使用和引用泛型類型的方面。</span><span class="sxs-lookup"><span data-stu-id="dffb9-105">This topic describes aspects of using and referencing generic types in XAML.</span></span>

## <a name="xtypearguments"></a><span data-ttu-id="dffb9-106">x:類型參數</span><span class="sxs-lookup"><span data-stu-id="dffb9-106">x:TypeArguments</span></span>

<span data-ttu-id="dffb9-107">`x:TypeArguments`是由 XAML 語言定義的指令。</span><span class="sxs-lookup"><span data-stu-id="dffb9-107">`x:TypeArguments` is a directive defined by the XAML language.</span></span> <span data-ttu-id="dffb9-108">當它用作由泛型類型支援的 XAML 類型的成員`x:TypeArguments`時, 將泛型的約束類型參數傳遞給支援構造函數。</span><span class="sxs-lookup"><span data-stu-id="dffb9-108">When it is used as a member of a XAML type that is backed by a generic type, `x:TypeArguments` passes constraining type arguments of the generic to the backing constructor.</span></span> <span data-ttu-id="dffb9-109">有關 與 .NET XAML`x:TypeArguments`服務使用 相關的引用語法,其中包括語法範例,請參閱[x:TypeArguments 指令](xtypearguments-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="dffb9-109">For reference syntax that pertains to .NET XAML Services use of `x:TypeArguments`, which includes syntax examples, see [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

<span data-ttu-id="dffb9-110">由於`x:TypeArguments`採用字串,並且具有類型轉換器支援,因此通常在 XAML 用法中聲明為屬性。</span><span class="sxs-lookup"><span data-stu-id="dffb9-110">Because `x:TypeArguments` takes a string, and has type converter backing, it is typically declared in XAML usage as an attribute.</span></span>

<span data-ttu-id="dffb9-111">在 XAML 節點流中,可以`x:TypeArguments`從節點`StartObject`流<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>中 的位置獲取聲明的資訊。</span><span class="sxs-lookup"><span data-stu-id="dffb9-111">In the XAML node stream, the information declared by `x:TypeArguments` can be obtained from <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> at a `StartObject` position in the node stream.</span></span> <span data-ttu-id="dffb9-112">的傳回<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>值 是值<xref:System.Xaml.XamlType>的清單 。</span><span class="sxs-lookup"><span data-stu-id="dffb9-112">The return value of <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> is a list of <xref:System.Xaml.XamlType> values.</span></span> <span data-ttu-id="dffb9-113">可以通過調<xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>用 確定 XAML 類型是否表示泛型類型。</span><span class="sxs-lookup"><span data-stu-id="dffb9-113">Determination of whether a XAML type represents a generic type can be made by calling <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.</span></span>

## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a><span data-ttu-id="dffb9-114">XAML 中泛型的規則和語法約定</span><span class="sxs-lookup"><span data-stu-id="dffb9-114">Rules and Syntax Conventions for Generics in XAML</span></span>

<span data-ttu-id="dffb9-115">在 XAML 中,泛型類型必須始終表示為受約束的泛型。</span><span class="sxs-lookup"><span data-stu-id="dffb9-115">In XAML, a generic type must always be represented as a constrained generic.</span></span> <span data-ttu-id="dffb9-116">無約束泛型永遠不會存在於 XAML 類型系統或 XAML 節點流中,並且不能在 XAML 標記中表示。</span><span class="sxs-lookup"><span data-stu-id="dffb9-116">An unconstrained generic is never present in the XAML type system or a XAML node stream and cannot be represented in XAML markup.</span></span> <span data-ttu-id="dffb9-117">泛型可以在 XAML 屬性語法中引用,用於對於泛型`x:TypeArguments`是 被引用的泛型的嵌套類型約束的情況`x:Type`,或者對於為泛型類型提供 CLR 類型引用的情況。</span><span class="sxs-lookup"><span data-stu-id="dffb9-117">A generic can be referenced within XAML attribute syntax for cases where it is a nested type constraint of a generic being referenced by `x:TypeArguments`, or for cases where `x:Type` supplies a CLR type reference for a generic type.</span></span> <span data-ttu-id="dffb9-118">通過 .NET XAML<xref:System.Xaml.Schema.XamlTypeTypeConverter>服務定義的類支援引用泛型。</span><span class="sxs-lookup"><span data-stu-id="dffb9-118">Referencing generics is supported through the <xref:System.Xaml.Schema.XamlTypeTypeConverter> class defined by .NET XAML Services.</span></span>

<span data-ttu-id="dffb9-119">XAML 屬性語法窗體<xref:System.Xaml.Schema.XamlTypeTypeConverter>通過 更改典型的 MSIL/ CLR 語法約定而啟用,該約定使用角度括弧來表示泛型的類型和約束,而是替換約束容器的括弧。</span><span class="sxs-lookup"><span data-stu-id="dffb9-119">The XAML attribute syntax form enabled by <xref:System.Xaml.Schema.XamlTypeTypeConverter> alters the typical MSIL / CLR syntax convention that uses angle brackets for types and constraints of generics, and instead substitutes parentheses for the constraint container.</span></span> <span data-ttu-id="dffb9-120">例如,請參閱[x:Type 參數指令](xtypearguments-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="dffb9-120">For an example, see [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

## <a name="generics-and-xaml-2009-features"></a><span data-ttu-id="dffb9-121">泛型和 XAML 2009 功能</span><span class="sxs-lookup"><span data-stu-id="dffb9-121">Generics and XAML 2009 Features</span></span>

<span data-ttu-id="dffb9-122">如果使用 XAML 2009 而不是映射 CLR 基類型以獲取通用語言基元中的 XAML 類型,則可以使用[XAML 2009 內置類型](types-for-primitives.md)作為中的`x:TypeArguments`資訊項。</span><span class="sxs-lookup"><span data-stu-id="dffb9-122">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [XAML 2009 built-in types](types-for-primitives.md) as information items in `x:TypeArguments`.</span></span> <span data-ttu-id="dffb9-123">例如,您可以聲明以下內容(未顯示前置碼映射,但`x`XAML 語言 XAML 2009 的命名空間):</span><span class="sxs-lookup"><span data-stu-id="dffb9-123">For example, you could declare the following (prefix mappings not shown, but `x` is the XAML language XAML namespace for XAML 2009):</span></span>

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

## <a name="generics-support-in-wpf"></a><span data-ttu-id="dffb9-124">WPF 中的統般支援</span><span class="sxs-lookup"><span data-stu-id="dffb9-124">Generics Support in WPF</span></span>

<span data-ttu-id="dffb9-125">對於專門針對 WPF 的 XAML 2006 用法,x:class 還必須[x:Class](xclass-directive.md)提供`x:TypeArguments`與的元素,並且該元素必須是 XAML 文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="dffb9-125">For XAML 2006 usage when specifically targeting WPF, [x:Class](xclass-directive.md) must also be provided on the same element as `x:TypeArguments`, and that element must be the root element in a XAML document.</span></span> <span data-ttu-id="dffb9-126">根元素必須映射到具有至少一個類型參數的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="dffb9-126">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="dffb9-127">例如 <xref:System.Windows.Navigation.PageFunction%601>。</span><span class="sxs-lookup"><span data-stu-id="dffb9-127">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span>

<span data-ttu-id="dffb9-128">支援泛型用法的可能解決方法包括定義可以返回泛型類型的自定義標記擴展,或提供從泛型類型派生但在其自己的類定義中平展泛型約束的換行類定義。</span><span class="sxs-lookup"><span data-stu-id="dffb9-128">Possible workarounds to support generic usages include defining a custom markup extension that can return generic types, or providing a wrapping class definition that derives from a generic type but flattens the generic constraint in its own class definition.</span></span>

<span data-ttu-id="dffb9-129">在 WPF 中,您可以將 XAML 2009`x:TypeArguments`功能與 一起使用 ,但僅適用於鬆散的 XAML(未標記編譯的 XAML)。</span><span class="sxs-lookup"><span data-stu-id="dffb9-129">In WPF you can use XAML 2009 features together with `x:TypeArguments`, but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="dffb9-130">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="dffb9-130">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

<span data-ttu-id="dffb9-131">.NET 框架 3.5 的 Windows 工作流基礎中的自定義工作流不支援通用的 XAML 使用。</span><span class="sxs-lookup"><span data-stu-id="dffb9-131">Custom workflows in Windows Workflow Foundation for .NET Framework 3.5 do not support generic XAML usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="dffb9-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dffb9-132">See also</span></span>

- [<span data-ttu-id="dffb9-133">x:TypeArguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="dffb9-133">x:TypeArguments Directive</span></span>](xtypearguments-directive.md)
- [<span data-ttu-id="dffb9-134">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="dffb9-134">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="dffb9-135">通用 XAML 語言基本類型的內建類型</span><span class="sxs-lookup"><span data-stu-id="dffb9-135">Built-in Types for Common XAML Language Primitives</span></span>](types-for-primitives.md)
