---
title: x:ClassModifier 指示詞
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: ef55549b43ecbef539d7e84a7281fa704a328938
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507586"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="b183c-102">x:ClassModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="b183c-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="b183c-103">修改 XAML 編譯行為時`x:Class`也會提供。</span><span class="sxs-lookup"><span data-stu-id="b183c-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="b183c-104">具體來說，而不是建立在部分`class`具有`Public`存取層級 （預設值），提供`x:Class`會透過`NotPublic`存取層級。</span><span class="sxs-lookup"><span data-stu-id="b183c-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="b183c-105">此行為會影響產生的組件中的類別的存取層級。</span><span class="sxs-lookup"><span data-stu-id="b183c-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b183c-106">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="b183c-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b183c-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="b183c-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b183c-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="b183c-108">*NotPublic*</span></span>|<span data-ttu-id="b183c-109">要傳遞至指定的確切字串<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>與<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>各有不同，根據您所使用的程式碼後置程式語言。</span><span class="sxs-lookup"><span data-stu-id="b183c-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="b183c-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="b183c-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="b183c-111">相依性</span><span class="sxs-lookup"><span data-stu-id="b183c-111">Dependencies</span></span>  
 <span data-ttu-id="b183c-112">[X:class](../../../docs/framework/xaml-services/x-class-directive.md)也必須提供相同的項目，且該項目必須是在網頁中的根項目。</span><span class="sxs-lookup"><span data-stu-id="b183c-112">[x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="b183c-113">如需詳細資訊，請參閱 < [ \[MS XAML\]一節 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="b183c-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b183c-114">備註</span><span class="sxs-lookup"><span data-stu-id="b183c-114">Remarks</span></span>  
 <span data-ttu-id="b183c-115">值`x:ClassModifier`在.NET Framework XAML 服務使用方式會因程式語言。</span><span class="sxs-lookup"><span data-stu-id="b183c-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="b183c-116">要使用的字串取決於各種語言的實作方式及其<xref:System.CodeDom.Compiler.CodeDomProvider>和類型轉換器，它會傳回定義的意義<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>和<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>，以及該語言是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b183c-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="b183c-117">適用於 C#，要傳遞至指定的字串<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是`internal`。</span><span class="sxs-lookup"><span data-stu-id="b183c-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
-   <span data-ttu-id="b183c-118">適用於 Microsoft Visual Basic.NET，要傳遞至指定的字串<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是`Friend`。</span><span class="sxs-lookup"><span data-stu-id="b183c-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
-   <span data-ttu-id="b183c-119">針對[!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]，任何目標存在編譯 XAML 支援; 因此，要傳遞的值未指定。</span><span class="sxs-lookup"><span data-stu-id="b183c-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="b183c-120">您也可以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>(`public`在 C#`Public`在 Visual Basic 中); 不過，指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>不常這樣做，因為<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>已經是預設行為。</span><span class="sxs-lookup"><span data-stu-id="b183c-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="b183c-121">其他值，與對等的使用者程式碼存取層級的限制，例如`private`在 C# 中，不相關的`x:ClassModifier`因為 XAML，不支援巢狀的類別的參考，因此，<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>修飾詞具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="b183c-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="b183c-122">安全性注意事項</span><span class="sxs-lookup"><span data-stu-id="b183c-122">Security Notes</span></span>  
 <span data-ttu-id="b183c-123">存取層級中宣告`x:ClassModifier`仍受限於特定的架構和其功能的解譯。</span><span class="sxs-lookup"><span data-stu-id="b183c-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="b183c-124">WPF 包含載入並具現化類型的功能所在`x:ClassModifier`是`internal`，如果該類別從 WPF 資源，但透過 URI 參考的組件參考。</span><span class="sxs-lookup"><span data-stu-id="b183c-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="b183c-125">由於此情況下，可能還有其他像藉由將其他架構，請避免只針對`x:ClassModifier`封鎖所有可能的具現化嘗試。</span><span class="sxs-lookup"><span data-stu-id="b183c-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b183c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b183c-126">See also</span></span>
- [<span data-ttu-id="b183c-127">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="b183c-127">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)
- [<span data-ttu-id="b183c-128">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="b183c-128">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="b183c-129">x:FieldModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="b183c-129">x:FieldModifier Directive</span></span>](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)
- [<span data-ttu-id="b183c-130">安全性 (WPF)</span><span class="sxs-lookup"><span data-stu-id="b183c-130">Security (WPF)</span></span>](../../../docs/framework/wpf/security-wpf.md)
- [<span data-ttu-id="b183c-131">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="b183c-131">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
