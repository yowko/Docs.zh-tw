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
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837229"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="22241-102">x:ClassModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="22241-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="22241-103">當同時提供 `x:Class` 時，修改 XAML 編譯行為。</span><span class="sxs-lookup"><span data-stu-id="22241-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="22241-104">具體而言，會以 `NotPublic` 存取層級建立提供的 `x:Class`，而不是建立具有 `Public` 存取層級的部分 `class` （預設值）。</span><span class="sxs-lookup"><span data-stu-id="22241-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="22241-105">這個行為會影響所產生元件中類別的存取層級。</span><span class="sxs-lookup"><span data-stu-id="22241-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="22241-106">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="22241-106">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="22241-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="22241-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22241-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="22241-108">*NotPublic*</span></span>|<span data-ttu-id="22241-109">根據您所使用的程式碼後置程式語言而定，要傳遞來指定 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 與 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 的確切字串會有所不同。</span><span class="sxs-lookup"><span data-stu-id="22241-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="22241-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="22241-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="22241-111">相依性</span><span class="sxs-lookup"><span data-stu-id="22241-111">Dependencies</span></span>  
 <span data-ttu-id="22241-112">您也必須在相同的元素上提供[x：Class](x-class-directive.md) ，而且該元素必須是頁面中的根項目。</span><span class="sxs-lookup"><span data-stu-id="22241-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="22241-113">如需詳細資訊，請參閱[\[MS-XAML\] 區段 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="22241-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22241-114">備註</span><span class="sxs-lookup"><span data-stu-id="22241-114">Remarks</span></span>  
 <span data-ttu-id="22241-115">.NET Framework XAML 服務使用量中 `x:ClassModifier` 的值會因程式設計語言而異。</span><span class="sxs-lookup"><span data-stu-id="22241-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="22241-116">要使用的字串取決於每種語言如何執行其 <xref:System.CodeDom.Compiler.CodeDomProvider> 以及它所傳回的型別轉換器，以定義 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 和 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>的意義，以及該語言是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="22241-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="22241-117">若C#為，要傳遞以指定 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 的字串 `internal`。</span><span class="sxs-lookup"><span data-stu-id="22241-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="22241-118">若為 Microsoft Visual Basic .NET，要傳遞以指定 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 的字串會 `Friend`。</span><span class="sxs-lookup"><span data-stu-id="22241-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="22241-119">針對C++/cli，不存在支援編譯 XAML 的目標。因此，未指定要傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="22241-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="22241-120">您也可以指定 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> （`public` 中C#的，`Public` 在 Visual Basic 中）;不過，指定 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 不常完成，因為 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 已經是預設行為。</span><span class="sxs-lookup"><span data-stu-id="22241-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="22241-121">具有對等使用者程式碼存取層級限制的其他值（例如C#中的 `private`）與 `x:ClassModifier` 無關，因為 XAML 中不支援嵌套類別參考，因此 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 修飾詞具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="22241-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="22241-122">安全性注意事項</span><span class="sxs-lookup"><span data-stu-id="22241-122">Security Notes</span></span>  
 <span data-ttu-id="22241-123">`x:ClassModifier` 中所宣告的存取層級仍受限於特定架構及其功能的轉譯。</span><span class="sxs-lookup"><span data-stu-id="22241-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="22241-124">WPF 包含的功能可載入並具現化 `internal``x:ClassModifier` 的類型（如果透過 pack URI 參考從 WPF 資源參考該類別）。</span><span class="sxs-lookup"><span data-stu-id="22241-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="22241-125">這種情況的結果可能是其他架構所實行的其他架構，因此請勿依賴 `x:ClassModifier` 來封鎖所有可能的具現化嘗試。</span><span class="sxs-lookup"><span data-stu-id="22241-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22241-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="22241-126">See also</span></span>

- [<span data-ttu-id="22241-127">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="22241-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="22241-128">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="22241-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="22241-129">x:FieldModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="22241-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="22241-130">安全性（WPF）</span><span class="sxs-lookup"><span data-stu-id="22241-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="22241-131">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="22241-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
