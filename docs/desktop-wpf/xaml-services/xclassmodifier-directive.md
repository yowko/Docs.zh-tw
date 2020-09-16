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
ms.openlocfilehash: 73732a06029cca3a4c6c6d82762d5263c5b8c955
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544813"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="3a829-102">x:ClassModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="3a829-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="3a829-103">當也提供時，修改 XAML 編譯行為 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="3a829-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="3a829-104">具體而言，您不需要建立 `class` 具有 `Public` (預設) 之存取層級的部分，而是 `x:Class` 使用 `NotPublic` 存取層級來建立提供的。</span><span class="sxs-lookup"><span data-stu-id="3a829-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="3a829-105">此行為會影響所產生元件中的類別存取層級。</span><span class="sxs-lookup"><span data-stu-id="3a829-105">This behavior affects the access level for the class in the generated assemblies.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="3a829-106">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="3a829-106">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="3a829-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="3a829-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="3a829-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="3a829-108">*NotPublic*</span></span>|<span data-ttu-id="3a829-109">要傳遞來指定和的確切 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 字串 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ，取決於您使用的程式碼後端程式設計語言而定。</span><span class="sxs-lookup"><span data-stu-id="3a829-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="3a829-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="3a829-110">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="3a829-111">相依性</span><span class="sxs-lookup"><span data-stu-id="3a829-111">Dependencies</span></span>

<span data-ttu-id="3a829-112">您也必須在相同的元素上提供[x：Class](xclass-directive.md) ，且該元素必須是頁面中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3a829-112">[x:Class](xclass-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="3a829-113">如需詳細資訊，請參閱[ \[ MS-XAML \] 區段 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a829-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="3a829-114">備註</span><span class="sxs-lookup"><span data-stu-id="3a829-114">Remarks</span></span>

<span data-ttu-id="3a829-115">`x:ClassModifier`.NET XAML 服務使用方式中的值會因程式設計語言而異。</span><span class="sxs-lookup"><span data-stu-id="3a829-115">The value of `x:ClassModifier` in .NET XAML Services usage varies by programming language.</span></span> <span data-ttu-id="3a829-116">要使用的字串取決於每個語言的實作為方式， <xref:System.CodeDom.Compiler.CodeDomProvider> 以及它所傳回的類型轉換器來定義和的意義 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ，以及該語言是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3a829-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="3a829-117">若為 c #，要傳遞給指定的字串 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 為 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="3a829-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>

- <span data-ttu-id="3a829-118">針對 Microsoft Visual Basic .NET，要傳遞給指定的字串 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 為 `Friend` 。</span><span class="sxs-lookup"><span data-stu-id="3a829-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>

- <span data-ttu-id="3a829-119">針對 c + +/CLI，不存在支援編譯 XAML 的目標;因此，未指定要傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="3a829-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>

<span data-ttu-id="3a829-120">您也可以 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `public` 在 Visual Basic) 中，以 c # 指定 (`Public` ; 不過， <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 因為已 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 是預設行為，所以不常進行指定。</span><span class="sxs-lookup"><span data-stu-id="3a829-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>

<span data-ttu-id="3a829-121">具有對等使用者程式碼存取層級限制的其他值（例如 `private` 在 c # 中）與不相關， `x:ClassModifier` 因為 XAML 中不支援嵌套類別參考，因此 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 修飾詞具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="3a829-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>

## <a name="security-notes"></a><span data-ttu-id="3a829-122">安全性注意事項</span><span class="sxs-lookup"><span data-stu-id="3a829-122">Security Notes</span></span>

<span data-ttu-id="3a829-123">在中宣告的存取層級 `x:ClassModifier` 仍受限於特定架構及其功能的解讀。</span><span class="sxs-lookup"><span data-stu-id="3a829-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="3a829-124">WPF 包含載入和具現化類型的 `x:ClassModifier` 功能 `internal` ，如果是從 WPF 資源透過套件 URI 參考參考該類別，則為。</span><span class="sxs-lookup"><span data-stu-id="3a829-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="3a829-125">這種情況下，可能會因為其他架構所實行的其他架構，而不依賴 `x:ClassModifier` 來封鎖所有可能具現化的嘗試。</span><span class="sxs-lookup"><span data-stu-id="3a829-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a829-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a829-126">See also</span></span>

- [<span data-ttu-id="3a829-127">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="3a829-127">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="3a829-128">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="3a829-128">Code-Behind and XAML in WPF</span></span>](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [<span data-ttu-id="3a829-129">x:FieldModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="3a829-129">x:FieldModifier Directive</span></span>](xfieldmodifier-directive.md)
- [<span data-ttu-id="3a829-130">安全性 (WPF)</span><span class="sxs-lookup"><span data-stu-id="3a829-130">Security (WPF)</span></span>](/dotnet/desktop/wpf/security-wpf)
- [<span data-ttu-id="3a829-131">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="3a829-131">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
