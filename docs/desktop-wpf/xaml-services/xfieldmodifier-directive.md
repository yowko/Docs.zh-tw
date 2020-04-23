---
title: x:FieldModifier 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 3e104b4c464d545e048f29901701c1c3dbb68229
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071525"
---
# <a name="xfieldmodifier-directive"></a><span data-ttu-id="59b16-102">x:FieldModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="59b16-102">x:FieldModifier Directive</span></span>
<span data-ttu-id="59b16-103">修改 XAML 編譯行為,<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>以便使用 訪問而不是默認行為定義命名<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>物件引用的 欄位。</span><span class="sxs-lookup"><span data-stu-id="59b16-103">Modifies XAML compilation behavior so that fields for named object references are defined with <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> access instead of the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> default behavior.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="59b16-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="59b16-104">XAML Attribute Usage</span></span>

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a><span data-ttu-id="59b16-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="59b16-105">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="59b16-106">*公開*</span><span class="sxs-lookup"><span data-stu-id="59b16-106">*Public*</span></span>|<span data-ttu-id="59b16-107">傳遞給指定的<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>確切字串因<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>所使用的代碼後面程式設計語言而異。</span><span class="sxs-lookup"><span data-stu-id="59b16-107">The exact string you pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that is used.</span></span> <span data-ttu-id="59b16-108">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="59b16-108">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="59b16-109">相依性</span><span class="sxs-lookup"><span data-stu-id="59b16-109">Dependencies</span></span>

 <span data-ttu-id="59b16-110">如果 XAML`x:FieldModifier`生產 在任何地方使用,則 XAML 生產的根元素必須聲明[x:類指令](xclass-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="59b16-110">If a XAML production uses `x:FieldModifier` anywhere, the root element of that XAML production must declare an [x:Class Directive](xclass-directive.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="59b16-111">備註</span><span class="sxs-lookup"><span data-stu-id="59b16-111">Remarks</span></span>

<span data-ttu-id="59b16-112">`x:FieldModifier`與聲明類或其成員的一般訪問級別無關。</span><span class="sxs-lookup"><span data-stu-id="59b16-112">`x:FieldModifier` is not relevant for declaring the general access level of a class or its members.</span></span> <span data-ttu-id="59b16-113">它僅與 XAML 處理行為相關,因為處理屬於 XAML 生產一部分的特定 XAML 物件,並成為在應用程式的物件圖中可能可存取的物件。</span><span class="sxs-lookup"><span data-stu-id="59b16-113">It is relevant only for XAML-processing behavior when a particular XAML object that is part of a XAML production is processed, and becomes an object that is potentially accessible in the object graph of an application.</span></span> <span data-ttu-id="59b16-114">默認情況下,此類物件的欄位引用保持私有,這可以防止控件消費者直接修改物件圖。</span><span class="sxs-lookup"><span data-stu-id="59b16-114">By default, the field reference for such an object is kept private, which prevents control consumers from modifying the object graph directly.</span></span> <span data-ttu-id="59b16-115">相反,控制使用者應該使用程式設計模型啟用的標準模式來修改物件圖,例如透過獲取佈局根、子元素集合、專用公共屬性等。</span><span class="sxs-lookup"><span data-stu-id="59b16-115">Instead, control consumers are expected to modify the object graph by using standard patterns that are enabled by programming models, such as by obtaining the layout root, the child element collections, the dedicated public properties, and so on.</span></span>

<span data-ttu-id="59b16-116">`x:FieldModifier`屬性的值因程式設計語言而異,並且其用途可能因特定框架而異。</span><span class="sxs-lookup"><span data-stu-id="59b16-116">The value for the `x:FieldModifier` attribute varies by programming language, and its purpose can vary in specific frameworks.</span></span> <span data-ttu-id="59b16-117">要使用的字串取決於每種語言如何實現其<xref:System.CodeDom.Compiler.CodeDomProvider>和返回的類型轉換器來定義<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>和的含義,以及該語言是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="59b16-117">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="59b16-118">對 C#,要傳遞到指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>的字串為`public`。</span><span class="sxs-lookup"><span data-stu-id="59b16-118">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `public`.</span></span>

- <span data-ttu-id="59b16-119">對於 Microsoft Visual Basic .NET,要傳遞<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>要`Public`指定的字串為 。</span><span class="sxs-lookup"><span data-stu-id="59b16-119">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `Public`.</span></span>

- <span data-ttu-id="59b16-120">對於C++/CLI,目前不存在 XAML 的目標;因此,要傳遞的字串未定義。</span><span class="sxs-lookup"><span data-stu-id="59b16-120">For C++/CLI, no targets for XAML currently exist; therefore, the string to pass is undefined.</span></span>

<span data-ttu-id="59b16-121"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>您還可以指定(`internal`在 C# 中`Friend`,在 Visual Basic<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>中),`NotPublic`但指定是不尋常的,因為行為已經是預設值。</span><span class="sxs-lookup"><span data-stu-id="59b16-121">You can also specify <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` in C#, `Friend` in Visual Basic) but specifying <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is unusual because `NotPublic` as the behavior is already the default.</span></span>

<span data-ttu-id="59b16-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是默認行為,因為編譯 XAML 的程式集外部的代碼很少需要訪問 XAML 創建的元素。</span><span class="sxs-lookup"><span data-stu-id="59b16-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is the default behavior because it is infrequent that code outside the assembly that compiled the XAML needs access to a XAML-created element.</span></span> <span data-ttu-id="59b16-123">WPF 安全體系結構以及 XAML 編譯行為不會聲明存儲元素實例的欄位為公共,除非`x:FieldModifier`您專門設置 允許公共存取。</span><span class="sxs-lookup"><span data-stu-id="59b16-123">WPF security architecture together with XAML compilation behavior will not declare fields that store element instances as public, unless you specifically set the `x:FieldModifier` to allow public access.</span></span>

<span data-ttu-id="59b16-124">`x:FieldModifier`僅與[具有 x:name 指令](xname-directive.md)的元素相關,因為該名稱用於在字段公開後引用該欄位。</span><span class="sxs-lookup"><span data-stu-id="59b16-124">`x:FieldModifier` is only relevant for elements with an [x:Name Directive](xname-directive.md) because that name is used to reference the field after it is public.</span></span>

<span data-ttu-id="59b16-125">默認情況下,根元素的部分類是公共的;因此,根元素的部分類為公共類。但是,您可以使用[x:Class 修改器指令](xclassmodifier-directive.md)將其非公開。</span><span class="sxs-lookup"><span data-stu-id="59b16-125">By default, the partial class for the root element is public; however, you can make it nonpublic by using the [x:ClassModifier Directive](xclassmodifier-directive.md).</span></span> <span data-ttu-id="59b16-126">[x:Class 修改器指令](xclassmodifier-directive.md)還影響根元素類實例的訪問級別。</span><span class="sxs-lookup"><span data-stu-id="59b16-126">The [x:ClassModifier Directive](xclassmodifier-directive.md) also affects the access level of the instance of the root element class.</span></span> <span data-ttu-id="59b16-127">您可以將和`x:FieldModifier``x:Name`放在根元素上,但這僅使根元素的公共欄位副本,真正的根元素類存取級別仍由[x:Class 修改器指令](xclassmodifier-directive.md)控制。</span><span class="sxs-lookup"><span data-stu-id="59b16-127">You can put both `x:Name` and `x:FieldModifier` on the root element, but this only makes a public field copy of the root element, with the true root element class access level still controlled by [x:ClassModifier Directive](xclassmodifier-directive.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59b16-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59b16-128">See also</span></span>

- [<span data-ttu-id="59b16-129">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="59b16-129">XAML and Custom Classes for WPF</span></span>](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [<span data-ttu-id="59b16-130">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="59b16-130">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="59b16-131">x:Name 指示詞</span><span class="sxs-lookup"><span data-stu-id="59b16-131">x:Name Directive</span></span>](xname-directive.md)
- [<span data-ttu-id="59b16-132">建置 WPF 應用程式 (WPF)</span><span class="sxs-lookup"><span data-stu-id="59b16-132">Building a WPF Application (WPF)</span></span>](../../framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="59b16-133">x:ClassModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="59b16-133">x:ClassModifier Directive</span></span>](xclassmodifier-directive.md)
