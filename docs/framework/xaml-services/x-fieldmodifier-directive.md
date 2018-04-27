---
title: x:FieldModifier 指示詞
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
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: 15
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eccad019bf18c56c23864c7a1559ce5076d954bb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="xfieldmodifier-directive"></a><span data-ttu-id="5def0-102">x:FieldModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="5def0-102">x:FieldModifier Directive</span></span>
<span data-ttu-id="5def0-103">修改 XAML 編譯行為，使具名的物件參考的欄位會定義使用<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>存取而不是<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>預設行為。</span><span class="sxs-lookup"><span data-stu-id="5def0-103">Modifies XAML compilation behavior so that fields for named object references are defined with <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> access instead of the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> default behavior.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="5def0-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="5def0-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="5def0-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="5def0-105">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5def0-106">*Public*</span><span class="sxs-lookup"><span data-stu-id="5def0-106">*Public*</span></span>|<span data-ttu-id="5def0-107">您將傳遞至指定的完整字串<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>與<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>會有所差異，使用程式碼後置程式設計語言而定。</span><span class="sxs-lookup"><span data-stu-id="5def0-107">The exact string you pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that is used.</span></span> <span data-ttu-id="5def0-108">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="5def0-108">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="5def0-109">相依性</span><span class="sxs-lookup"><span data-stu-id="5def0-109">Dependencies</span></span>  
 <span data-ttu-id="5def0-110">如果 XAML 生產使用`x:FieldModifier`該 XAML 生產的根項目必須宣告的任何地方、 [X:class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="5def0-110">If a XAML production uses `x:FieldModifier` anywhere, the root element of that XAML production must declare an [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5def0-111">備註</span><span class="sxs-lookup"><span data-stu-id="5def0-111">Remarks</span></span>  
 <span data-ttu-id="5def0-112">`x:FieldModifier` 不相關的宣告類別或其成員的一般存取層級。</span><span class="sxs-lookup"><span data-stu-id="5def0-112">`x:FieldModifier` is not relevant for declaring the general access level of a class or its members.</span></span> <span data-ttu-id="5def0-113">這樣做只適用於 XAML 處理行為屬於 XAML 生產的特定 XAML 物件處理時，就會變成應用程式的物件圖形中可能可以存取的物件。</span><span class="sxs-lookup"><span data-stu-id="5def0-113">It is relevant only for XAML-processing behavior when a particular XAML object that is part of a XAML production is processed, and becomes an object that is potentially accessible in the object graph of an application.</span></span> <span data-ttu-id="5def0-114">根據預設，這類物件的欄位參考會保留私用，它可防止控制項的取用者直接修改的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="5def0-114">By default, the field reference for such an object is kept private, which prevents control consumers from modifying the object graph directly.</span></span> <span data-ttu-id="5def0-115">相反地，控制取用者應該使用標準模式所啟用的程式設計模型，例如藉由取得的版面配置根目錄中，子元素的集合，專用的公用屬性，來修改物件圖形，並以此類推。</span><span class="sxs-lookup"><span data-stu-id="5def0-115">Instead, control consumers are expected to modify the object graph by using standard patterns that are enabled by programming models, such as by obtaining the layout root, the child element collections, the dedicated public properties, and so on.</span></span>  
  
 <span data-ttu-id="5def0-116">值`x:FieldModifier`屬性會因程式設計語言，與特定架構可以改變其用途。</span><span class="sxs-lookup"><span data-stu-id="5def0-116">The value for the `x:FieldModifier` attribute varies by programming language, and its purpose can vary in specific frameworks.</span></span> <span data-ttu-id="5def0-117">要使用的字串取決於各種語言的實作方式其<xref:System.CodeDom.Compiler.CodeDomProvider>和類型轉換器，它會傳回定義意義<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>和<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>，以及該語言是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5def0-117">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="5def0-118">C#，要傳遞至指定的字串<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>是`public`。</span><span class="sxs-lookup"><span data-stu-id="5def0-118">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `public`.</span></span>  
  
-   <span data-ttu-id="5def0-119">Microsoft Visual Basic.NET，要傳遞至指定字串的<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>是`Public`。</span><span class="sxs-lookup"><span data-stu-id="5def0-119">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is `Public`.</span></span>  
  
-   <span data-ttu-id="5def0-120">如[!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]，XAML 的任何目標目前存在; 因此，要傳遞的字串是未定義。</span><span class="sxs-lookup"><span data-stu-id="5def0-120">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets for XAML currently exist; therefore, the string to pass is undefined.</span></span>  
  
 <span data-ttu-id="5def0-121">您也可以指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>(`internal`在 C# 中，`Friend`在 Visual Basic 中) 但指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是常見的事因為`NotPublic`時已經是預設行為。</span><span class="sxs-lookup"><span data-stu-id="5def0-121">You can also specify <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` in C#, `Friend` in Visual Basic) but specifying <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is unusual because `NotPublic` as the behavior is already the default.</span></span>  
  
 <span data-ttu-id="5def0-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 是預設行為，因為它不頻繁編譯 XAML 的組件外部的程式碼需要存取 XAML 建立的項目。</span><span class="sxs-lookup"><span data-stu-id="5def0-122"><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is the default behavior because it is infrequent that code outside the assembly that compiled the XAML needs access to a XAML-created element.</span></span> <span data-ttu-id="5def0-123">WPF 安全性架構，連同 XAML 編譯行為將會宣告為公用，儲存項目執行個體的欄位，除非您特別設定`x:FieldModifier`為允許公用存取。</span><span class="sxs-lookup"><span data-stu-id="5def0-123">WPF security architecture together with XAML compilation behavior will not declare fields that store element instances as public, unless you specifically set the `x:FieldModifier` to allow public access.</span></span>  
  
 <span data-ttu-id="5def0-124">`x:FieldModifier` 只會與相關的項目[X:name 指示詞](../../../docs/framework/xaml-services/x-name-directive.md)因為該名稱用來參考的欄位之後，它是公用。</span><span class="sxs-lookup"><span data-stu-id="5def0-124">`x:FieldModifier` is only relevant for elements with an [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md) because that name is used to reference the field after it is public.</span></span>  
  
 <span data-ttu-id="5def0-125">根據預設，部分類別的根項目是公用的。不過，您可以將非公用使用[X:classmodifier 指示詞](../../../docs/framework/xaml-services/x-classmodifier-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="5def0-125">By default, the partial class for the root element is public; however, you can make it nonpublic by using the [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).</span></span> <span data-ttu-id="5def0-126">[X:classmodifier 指示詞](../../../docs/framework/xaml-services/x-classmodifier-directive.md)也會影響根項目類別的執行個體的存取層級。</span><span class="sxs-lookup"><span data-stu-id="5def0-126">The [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md) also affects the access level of the instance of the root element class.</span></span> <span data-ttu-id="5def0-127">您可以將兩者`x:Name`和`x:FieldModifier`根項目，但這只會公用欄位複製的根項目，則為 true 的根項目類別存取層級仍受[X:classmodifier 指示詞](../../../docs/framework/xaml-services/x-classmodifier-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="5def0-127">You can put both `x:Name` and `x:FieldModifier` on the root element, but this only makes a public field copy of the root element, with the true root element class access level still controlled by [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5def0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5def0-128">See Also</span></span>  
 [<span data-ttu-id="5def0-129">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="5def0-129">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [<span data-ttu-id="5def0-130">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="5def0-130">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="5def0-131">x:Name 指示詞</span><span class="sxs-lookup"><span data-stu-id="5def0-131">x:Name Directive</span></span>](../../../docs/framework/xaml-services/x-name-directive.md)  
 [<span data-ttu-id="5def0-132">建置 WPF 應用程式 (WPF)</span><span class="sxs-lookup"><span data-stu-id="5def0-132">Building a WPF Application (WPF)</span></span>](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [<span data-ttu-id="5def0-133">x:ClassModifier 指示詞</span><span class="sxs-lookup"><span data-stu-id="5def0-133">x:ClassModifier Directive</span></span>](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
