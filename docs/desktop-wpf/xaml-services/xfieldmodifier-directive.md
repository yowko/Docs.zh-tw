---
title: x:FieldModifier 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 4e67a6dac49b8d6a7d316526f99a1519b08fd68b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554471"
---
# <a name="xfieldmodifier-directive"></a><span data-ttu-id="3255b-102">x:FieldModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="3255b-102">x:FieldModifier Directive</span></span>
<span data-ttu-id="3255b-103">修改 XAML 編譯行為，以便將命名物件參考的欄位定義為具有 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 存取權，而不是使用 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 預設行為。</span><span class="sxs-lookup"><span data-stu-id="3255b-103">Modifies XAML compilation behavior so that fields for named object references are defined with <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> access instead of the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> default behavior.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="3255b-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="3255b-104">XAML Attribute Usage</span></span>

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a><span data-ttu-id="3255b-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="3255b-105">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="3255b-106">*公開*</span><span class="sxs-lookup"><span data-stu-id="3255b-106">*Public*</span></span>|<span data-ttu-id="3255b-107"><xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 視使用的程式碼後端程式設計語言而定，您傳遞給指定和的確切字串會有所不同。</span><span class="sxs-lookup"><span data-stu-id="3255b-107">The exact string you pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that is used.</span></span> <span data-ttu-id="3255b-108">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="3255b-108">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="3255b-109">相依性</span><span class="sxs-lookup"><span data-stu-id="3255b-109">Dependencies</span></span>

 <span data-ttu-id="3255b-110">如果 XAML 生產環境使用 `x:FieldModifier` 任何位置，則該 xaml 生產的根項目必須宣告 [x：Class](xclass-directive.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="3255b-110">If a XAML production uses `x:FieldModifier` anywhere, the root element of that XAML production must declare an [x:Class Directive](xclass-directive.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="3255b-111">備註</span><span class="sxs-lookup"><span data-stu-id="3255b-111">Remarks</span></span>

<span data-ttu-id="3255b-112">`x:FieldModifier` 與宣告類別或其成員的一般存取層級無關。</span><span class="sxs-lookup"><span data-stu-id="3255b-112">`x:FieldModifier` is not relevant for declaring the general access level of a class or its members.</span></span> <span data-ttu-id="3255b-113">只有在處理屬於 XAML 生產的特定 XAML 物件時，它才會與 XAML 處理行為相關，並且會成為可能在應用程式的物件圖形中存取的物件。</span><span class="sxs-lookup"><span data-stu-id="3255b-113">It is relevant only for XAML-processing behavior when a particular XAML object that is part of a XAML production is processed, and becomes an object that is potentially accessible in the object graph of an application.</span></span> <span data-ttu-id="3255b-114">根據預設，這類物件的欄位參考會保留為私用，以防止控制取用者直接修改物件圖形。</span><span class="sxs-lookup"><span data-stu-id="3255b-114">By default, the field reference for such an object is kept private, which prevents control consumers from modifying the object graph directly.</span></span> <span data-ttu-id="3255b-115">相反地，控制取用者應該使用程式設計模型所啟用的標準模式來修改物件圖形，例如藉由取得配置根、子項目集合、專用公用屬性等。</span><span class="sxs-lookup"><span data-stu-id="3255b-115">Instead, control consumers are expected to modify the object graph by using standard patterns that are enabled by programming models, such as by obtaining the layout root, the child element collections, the dedicated public properties, and so on.</span></span>

<span data-ttu-id="3255b-116">`x:FieldModifier`屬性（attribute）的值會因程式設計語言而異，而其用途在特定架構中會有所不同。</span><span class="sxs-lookup"><span data-stu-id="3255b-116">The value for the `x:FieldModifier` attribute varies by programming language, and its purpose can vary in specific frameworks.</span></span> <span data-ttu-id="3255b-117">要使用的字串取決於每個語言的實作為方式， <xref:System.CodeDom.Compiler.CodeDomProvider> 以及它所傳回的類型轉換器來定義和的意義 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ，以及該語言是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3255b-117">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="3255b-118">若為 c #，要傳遞給指定的字串 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 為 `public` 。</span><span class="sxs-lookup"><span data-stu-id="3255b-118">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `public`.</span></span>

- <span data-ttu-id="3255b-119">針對 Microsoft Visual Basic .NET，要傳遞給指定的字串 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 為 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="3255b-119">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `Public`.</span></span>

- <span data-ttu-id="3255b-120">針對 c + +/CLI，目前沒有 XAML 的目標存在;因此，要傳遞的字串是未定義的。</span><span class="sxs-lookup"><span data-stu-id="3255b-120">For C++/CLI, no targets for XAML currently exist; therefore, the string to pass is undefined.</span></span>

<span data-ttu-id="3255b-121">您也可以 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `internal` 在 Visual Basic) 中，以 c # 指定 (， `Friend` 但 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 因為 `NotPublic` 行為已是預設值，所以指定為不尋常。</span><span class="sxs-lookup"><span data-stu-id="3255b-121">You can also specify <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` in C#, `Friend` in Visual Basic) but specifying <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is unusual because `NotPublic` as the behavior is already the default.</span></span>

<span data-ttu-id="3255b-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 是預設行為，因為編譯 XAML 的元件之外的程式碼需要存取 XAML 建立的元素。</span><span class="sxs-lookup"><span data-stu-id="3255b-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is the default behavior because it is infrequent that code outside the assembly that compiled the XAML needs access to a XAML-created element.</span></span> <span data-ttu-id="3255b-123">除非您特別將設定 `x:FieldModifier` 為允許公用存取，否則 WPF 安全性架構與 XAML 編譯行為將不會宣告將專案實例儲存為公用的欄位。</span><span class="sxs-lookup"><span data-stu-id="3255b-123">WPF security architecture together with XAML compilation behavior will not declare fields that store element instances as public, unless you specifically set the `x:FieldModifier` to allow public access.</span></span>

<span data-ttu-id="3255b-124">`x:FieldModifier` 僅與具有 [x：Name](xname-directive.md) 指示詞的元素相關，因為該名稱是在公用之後用來參考欄位。</span><span class="sxs-lookup"><span data-stu-id="3255b-124">`x:FieldModifier` is only relevant for elements with an [x:Name Directive](xname-directive.md) because that name is used to reference the field after it is public.</span></span>

<span data-ttu-id="3255b-125">根據預設，根項目的部分類別是公用的，不過，您可以使用 [x:ClassModifier](xclassmodifier-directive.md)指示詞將它設為非公用。</span><span class="sxs-lookup"><span data-stu-id="3255b-125">By default, the partial class for the root element is public; however, you can make it nonpublic by using the [x:ClassModifier Directive](xclassmodifier-directive.md).</span></span> <span data-ttu-id="3255b-126">[X:ClassModifier](xclassmodifier-directive.md)指示詞也會影響根項目類別之實例的存取層級。</span><span class="sxs-lookup"><span data-stu-id="3255b-126">The [x:ClassModifier Directive](xclassmodifier-directive.md) also affects the access level of the instance of the root element class.</span></span> <span data-ttu-id="3255b-127">您可以在 `x:Name` `x:FieldModifier` 根項目上放置和，但這只會建立根項目的公用欄位複本，而真正的根項目類別存取層級仍由 [x:ClassModifier](xclassmodifier-directive.md)指示詞控制。</span><span class="sxs-lookup"><span data-stu-id="3255b-127">You can put both `x:Name` and `x:FieldModifier` on the root element, but this only makes a public field copy of the root element, with the true root element class access level still controlled by [x:ClassModifier Directive](xclassmodifier-directive.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3255b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3255b-128">See also</span></span>

- [<span data-ttu-id="3255b-129">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="3255b-129">XAML and Custom Classes for WPF</span></span>](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
- [<span data-ttu-id="3255b-130">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="3255b-130">Code-Behind and XAML in WPF</span></span>](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [<span data-ttu-id="3255b-131">x:Name 指示詞</span><span class="sxs-lookup"><span data-stu-id="3255b-131">x:Name Directive</span></span>](xname-directive.md)
- [<span data-ttu-id="3255b-132"> (WPF) 建立 WPF 應用程式 </span><span class="sxs-lookup"><span data-stu-id="3255b-132">Building a WPF Application (WPF)</span></span>](/dotnet/desktop/wpf/app-development/building-a-wpf-application-wpf)
- [<span data-ttu-id="3255b-133">x:ClassModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="3255b-133">x:ClassModifier Directive</span></span>](xclassmodifier-directive.md)
