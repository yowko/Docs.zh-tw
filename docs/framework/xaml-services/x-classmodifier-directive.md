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
ms.openlocfilehash: 5daff0567c1b1415fe994f6e39b4079cb2ab7346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053824"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="30138-102">x:ClassModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="30138-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="30138-103">當也提供時`x:Class` ，修改 XAML 編譯行為。</span><span class="sxs-lookup"><span data-stu-id="30138-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="30138-104">具體而言，它不會建立`class` `Public`具有存取層級的部分（預設值），而`x:Class`是使用`NotPublic`存取層級建立所提供的。</span><span class="sxs-lookup"><span data-stu-id="30138-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="30138-105">這個行為會影響所產生元件中類別的存取層級。</span><span class="sxs-lookup"><span data-stu-id="30138-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="30138-106">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="30138-106">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="30138-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="30138-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30138-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="30138-108">*NotPublic*</span></span>|<span data-ttu-id="30138-109">視您使用的程式碼後<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>置<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>程式語言而定，要傳遞來指定和的確切字串會有所不同。</span><span class="sxs-lookup"><span data-stu-id="30138-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="30138-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="30138-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="30138-111">相依性</span><span class="sxs-lookup"><span data-stu-id="30138-111">Dependencies</span></span>  
 <span data-ttu-id="30138-112">您也必須在相同的元素上提供[x：Class](x-class-directive.md) ，而且該元素必須是頁面中的根項目。</span><span class="sxs-lookup"><span data-stu-id="30138-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="30138-113">如需詳細資訊，請參閱 < [ \[MS-XAML\]區段 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="30138-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30138-114">備註</span><span class="sxs-lookup"><span data-stu-id="30138-114">Remarks</span></span>  
 <span data-ttu-id="30138-115">.NET Framework XAML 服務`x:ClassModifier`使用量中的值會因程式設計語言而異。</span><span class="sxs-lookup"><span data-stu-id="30138-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="30138-116">要使用的字串取決於每種語言如何執行<xref:System.CodeDom.Compiler.CodeDomProvider>其和它所傳回的型別轉換器，以<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>定義<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>和的意義，以及該語言是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="30138-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="30138-117">若C#為，要傳遞以指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>的字串是。 `internal`</span><span class="sxs-lookup"><span data-stu-id="30138-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="30138-118">若為 Microsoft Visual Basic .net，要傳遞以指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>的字串是。 `Friend`</span><span class="sxs-lookup"><span data-stu-id="30138-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="30138-119">針對C++/cli，不存在支援編譯 XAML 的目標。因此，未指定要傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="30138-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="30138-120">您也可以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> （`public`在C#Visual Basic `Public`中）; 不過，指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>不常完成，因為<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>已經是預設行為。</span><span class="sxs-lookup"><span data-stu-id="30138-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="30138-121">具有對等使用者程式碼存取層級限制的其他值`private` （ C#例如中的）與`x:ClassModifier`不相關，因為 XAML 中不支援嵌套類別參考，因此<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>修飾詞的效果相同.</span><span class="sxs-lookup"><span data-stu-id="30138-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="30138-122">安全性注意事項</span><span class="sxs-lookup"><span data-stu-id="30138-122">Security Notes</span></span>  
 <span data-ttu-id="30138-123">如中`x:ClassModifier`所宣告的存取層級，仍然受限於特定架構及其功能的轉譯。</span><span class="sxs-lookup"><span data-stu-id="30138-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="30138-124">Wpf 包含載入和具現化類型的`x:ClassModifier`功能`internal`，其中是，如果透過 pack URI 參考從 WPF 資源參考該類別。</span><span class="sxs-lookup"><span data-stu-id="30138-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="30138-125">這種情況的結果可能是因為其他架構所實行的其他架構，而不依賴`x:ClassModifier`來封鎖所有可能的具現化嘗試。</span><span class="sxs-lookup"><span data-stu-id="30138-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30138-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30138-126">See also</span></span>

- [<span data-ttu-id="30138-127">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="30138-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="30138-128">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="30138-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="30138-129">x:FieldModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="30138-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="30138-130">安全性（WPF）</span><span class="sxs-lookup"><span data-stu-id="30138-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="30138-131">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="30138-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
