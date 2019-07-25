---
title: x:FieldModifier 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 646ad1ca99d83f9fb2994f3c394eca27a60c0eac
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484727"
---
# <a name="xfieldmodifier-directive"></a><span data-ttu-id="7d1e7-102">x:FieldModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="7d1e7-102">x:FieldModifier Directive</span></span>
<span data-ttu-id="7d1e7-103">修改 XAML 編譯行為, 讓命名物件參考的欄位是以存取<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>來定義, 而<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>不是使用預設行為。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-103">Modifies XAML compilation behavior so that fields for named object references are defined with <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> access instead of the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> default behavior.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="7d1e7-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="7d1e7-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="7d1e7-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="7d1e7-105">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d1e7-106">*Public*</span><span class="sxs-lookup"><span data-stu-id="7d1e7-106">*Public*</span></span>|<span data-ttu-id="7d1e7-107">視所使用的程式碼後<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>置<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>程式語言而定, 您傳遞來指定與的確切字串會有所不同。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-107">The exact string you pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that is used.</span></span> <span data-ttu-id="7d1e7-108">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-108">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="7d1e7-109">相依性</span><span class="sxs-lookup"><span data-stu-id="7d1e7-109">Dependencies</span></span>  
 <span data-ttu-id="7d1e7-110">如果 xaml 生產環境使用`x:FieldModifier`任何位置, 則該 xaml 生產環境的根項目必須宣告[x:Class](x-class-directive.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-110">If a XAML production uses `x:FieldModifier` anywhere, the root element of that XAML production must declare an [x:Class Directive](x-class-directive.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d1e7-111">備註</span><span class="sxs-lookup"><span data-stu-id="7d1e7-111">Remarks</span></span>  
 <span data-ttu-id="7d1e7-112">`x:FieldModifier`與宣告類別或其成員的一般存取層級無關。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-112">`x:FieldModifier` is not relevant for declaring the general access level of a class or its members.</span></span> <span data-ttu-id="7d1e7-113">只有在處理 XAML 生產中的特定 XAML 物件時, 它才與 XAML 處理行為有關, 它會成為在應用程式的物件圖形中可能可存取的物件。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-113">It is relevant only for XAML-processing behavior when a particular XAML object that is part of a XAML production is processed, and becomes an object that is potentially accessible in the object graph of an application.</span></span> <span data-ttu-id="7d1e7-114">根據預設, 這類物件的欄位參考會保持為私用, 以防止控制取用者直接修改物件圖形。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-114">By default, the field reference for such an object is kept private, which prevents control consumers from modifying the object graph directly.</span></span> <span data-ttu-id="7d1e7-115">相反地, 控制取用者應該使用由程式設計模型啟用的標準模式 (例如, 藉由取得版面配置根、子專案集合、專用的公用屬性等等) 來修改物件圖形。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-115">Instead, control consumers are expected to modify the object graph by using standard patterns that are enabled by programming models, such as by obtaining the layout root, the child element collections, the dedicated public properties, and so on.</span></span>  
  
 <span data-ttu-id="7d1e7-116">`x:FieldModifier`屬性的值會因程式設計語言而異, 而且其目的可能會因特定架構而異。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-116">The value for the `x:FieldModifier` attribute varies by programming language, and its purpose can vary in specific frameworks.</span></span> <span data-ttu-id="7d1e7-117">要使用的字串取決於每種語言如何執行<xref:System.CodeDom.Compiler.CodeDomProvider>其和它所傳回的型別轉換器, 以<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>定義<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>和的意義, 以及該語言是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-117">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="7d1e7-118">若C#為, 要傳遞以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>的字串是。 `public`</span><span class="sxs-lookup"><span data-stu-id="7d1e7-118">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `public`.</span></span>  
  
- <span data-ttu-id="7d1e7-119">若為 Microsoft Visual Basic .net, 要傳遞以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>的字串是。 `Public`</span><span class="sxs-lookup"><span data-stu-id="7d1e7-119">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `Public`.</span></span>  
  
- <span data-ttu-id="7d1e7-120">針對C++/CLI, XAML 目前不存在任何目標;因此, 要傳遞的字串未定義。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-120">For C++/CLI, no targets for XAML currently exist; therefore, the string to pass is undefined.</span></span>  
  
 <span data-ttu-id="7d1e7-121">您也可以指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal`在C#Visual Basic `Friend`中), 但指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>不尋常, `NotPublic`因為行為已經是預設值。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-121">You can also specify <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` in C#, `Friend` in Visual Basic) but specifying <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is unusual because `NotPublic` as the behavior is already the default.</span></span>  
  
 <span data-ttu-id="7d1e7-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是預設行為, 因為編譯 XAML 之元件外部的程式碼需要存取 XAML 所建立的專案。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is the default behavior because it is infrequent that code outside the assembly that compiled the XAML needs access to a XAML-created element.</span></span> <span data-ttu-id="7d1e7-123">WPF 安全性架構與 XAML 編譯行為並不會宣告將元素實例儲存為公用的欄位, 除非您特別將`x:FieldModifier`設定為允許公用存取。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-123">WPF security architecture together with XAML compilation behavior will not declare fields that store element instances as public, unless you specifically set the `x:FieldModifier` to allow public access.</span></span>  
  
 <span data-ttu-id="7d1e7-124">`x:FieldModifier`僅與具有[x:Name](x-name-directive.md)指示詞的元素相關, 因為該名稱是在公用後用來參考欄位。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-124">`x:FieldModifier` is only relevant for elements with an [x:Name Directive](x-name-directive.md) because that name is used to reference the field after it is public.</span></span>  
  
 <span data-ttu-id="7d1e7-125">根據預設, 根項目的部分類別是公用的;不過, 您可以使用[x:ClassModifier](x-classmodifier-directive.md)指示詞將它設為非公用。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-125">By default, the partial class for the root element is public; however, you can make it nonpublic by using the [x:ClassModifier Directive](x-classmodifier-directive.md).</span></span> <span data-ttu-id="7d1e7-126">[X:ClassModifier](x-classmodifier-directive.md)指示詞也會影響根項目類別之實例的存取層級。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-126">The [x:ClassModifier Directive](x-classmodifier-directive.md) also affects the access level of the instance of the root element class.</span></span> <span data-ttu-id="7d1e7-127">您可以將`x:Name`和`x:FieldModifier`放在根項目上, 但這只會建立根項目的公用欄位複本, 而真正的根項目類別存取層級仍由[x:ClassModifier](x-classmodifier-directive.md)指示詞控制。</span><span class="sxs-lookup"><span data-stu-id="7d1e7-127">You can put both `x:Name` and `x:FieldModifier` on the root element, but this only makes a public field copy of the root element, with the true root element class access level still controlled by [x:ClassModifier Directive](x-classmodifier-directive.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1e7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d1e7-128">See also</span></span>

- [<span data-ttu-id="7d1e7-129">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="7d1e7-129">XAML and Custom Classes for WPF</span></span>](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [<span data-ttu-id="7d1e7-130">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="7d1e7-130">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="7d1e7-131">x:Name 指示詞</span><span class="sxs-lookup"><span data-stu-id="7d1e7-131">x:Name Directive</span></span>](x-name-directive.md)
- [<span data-ttu-id="7d1e7-132">建置 WPF 應用程式 (WPF)</span><span class="sxs-lookup"><span data-stu-id="7d1e7-132">Building a WPF Application (WPF)</span></span>](../wpf/app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="7d1e7-133">x:ClassModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="7d1e7-133">x:ClassModifier Directive</span></span>](x-classmodifier-directive.md)
