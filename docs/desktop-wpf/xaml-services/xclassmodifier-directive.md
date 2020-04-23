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
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072029"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="984c5-102">x:ClassModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="984c5-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="984c5-103">在提供時`x:Class`修改 XAML 編譯行為。</span><span class="sxs-lookup"><span data-stu-id="984c5-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="984c5-104">具體而言,提供的不是創建具有`class``Public`訪問級別的部分(預設值),而是`x:Class``NotPublic`使用訪問級別創建所提供的部分。</span><span class="sxs-lookup"><span data-stu-id="984c5-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="984c5-105">此行為會影響生成的程式集中類的訪問級別。</span><span class="sxs-lookup"><span data-stu-id="984c5-105">This behavior affects the access level for the class in the generated assemblies.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="984c5-106">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="984c5-106">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="984c5-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="984c5-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="984c5-108">*不公開*</span><span class="sxs-lookup"><span data-stu-id="984c5-108">*NotPublic*</span></span>|<span data-ttu-id="984c5-109">要指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>的確切字串與不同<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>,具體取決於您使用的代碼背後的程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="984c5-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="984c5-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="984c5-110">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="984c5-111">相依性</span><span class="sxs-lookup"><span data-stu-id="984c5-111">Dependencies</span></span>

<span data-ttu-id="984c5-112">[x:類](xclass-directive.md)也必須在同一元素上提供,並且該元素必須是頁面中的根元素。</span><span class="sxs-lookup"><span data-stu-id="984c5-112">[x:Class](xclass-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="984c5-113">有關詳細資訊,請參閱[\[MS-XAML\]部分 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="984c5-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="984c5-114">備註</span><span class="sxs-lookup"><span data-stu-id="984c5-114">Remarks</span></span>

<span data-ttu-id="984c5-115">.NET `x:ClassModifier` XAML 服務使用中的值因程式設計語言而異。</span><span class="sxs-lookup"><span data-stu-id="984c5-115">The value of `x:ClassModifier` in .NET XAML Services usage varies by programming language.</span></span> <span data-ttu-id="984c5-116">要使用的字串取決於每種語言如何實現其<xref:System.CodeDom.Compiler.CodeDomProvider>和返回的類型轉換器來定義<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>和的含義,以及該語言是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="984c5-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="984c5-117">對 C#,要傳遞到指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>的字串為`internal`。</span><span class="sxs-lookup"><span data-stu-id="984c5-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>

- <span data-ttu-id="984c5-118">對於 Microsoft Visual Basic .NET,要傳遞<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>要`Friend`指定的字串為 。</span><span class="sxs-lookup"><span data-stu-id="984c5-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>

- <span data-ttu-id="984c5-119">對於C++/CLI,不存在支援編譯 XAML 的目標;因此,未指定要傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="984c5-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>

<span data-ttu-id="984c5-120">您還可以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>`public`( 在`Public`C# 中 ,在視覺基礎中);但是,指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>不常執行,因為<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>已是默認行為。</span><span class="sxs-lookup"><span data-stu-id="984c5-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>

<span data-ttu-id="984c5-121">具有等效用戶代碼訪問級別限制的其他值(如`private`C#中)與 XAML`x:ClassModifier`中不支援嵌套類引用<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>無關,因此,修改器具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="984c5-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>

## <a name="security-notes"></a><span data-ttu-id="984c5-122">安全性注意事項</span><span class="sxs-lookup"><span data-stu-id="984c5-122">Security Notes</span></span>

<span data-ttu-id="984c5-123">中`x:ClassModifier`宣佈的訪問級別仍受特定框架及其能力的解釋。</span><span class="sxs-lookup"><span data-stu-id="984c5-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="984c5-124">WPF 包括載入和實例化類型的功能,`x:ClassModifier``internal`如果 透過包URI引用WPF資源引用該類。</span><span class="sxs-lookup"><span data-stu-id="984c5-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="984c5-125">由於這種情況,以及可能由其他框架實現的可能其他框架,不完全依賴`x:ClassModifier`來阻止所有可能的實例化嘗試。</span><span class="sxs-lookup"><span data-stu-id="984c5-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>

## <a name="see-also"></a><span data-ttu-id="984c5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="984c5-126">See also</span></span>

- [<span data-ttu-id="984c5-127">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="984c5-127">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="984c5-128">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="984c5-128">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="984c5-129">x:FieldModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="984c5-129">x:FieldModifier Directive</span></span>](xfieldmodifier-directive.md)
- [<span data-ttu-id="984c5-130">安全性 (WPF)</span><span class="sxs-lookup"><span data-stu-id="984c5-130">Security (WPF)</span></span>](../../framework/wpf/security-wpf.md)
- [<span data-ttu-id="984c5-131">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="984c5-131">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
