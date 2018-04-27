---
title: x:Null 標記延伸
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: 20
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f176598db00c57159bf351ea5d9ec428c5c04bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="2ece9-102">x:Null 標記延伸</span><span class="sxs-lookup"><span data-stu-id="2ece9-102">x:Null Markup Extension</span></span>
<span data-ttu-id="2ece9-103">指定`null`做為 XAML 成員的值。</span><span class="sxs-lookup"><span data-stu-id="2ece9-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="2ece9-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="2ece9-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="2ece9-105">備註</span><span class="sxs-lookup"><span data-stu-id="2ece9-105">Remarks</span></span>  
 <span data-ttu-id="2ece9-106">C# 中的 null 參考的關鍵字和[!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)]為 null。</span><span class="sxs-lookup"><span data-stu-id="2ece9-106">The keyword for a null reference in C# and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="2ece9-107">Null 參考的 Microsoft Visual Basic 關鍵字是`Nothing`，但會一直使用`{x:Null}`與 XAML 用法不論關聯的 xaml 程式碼後置語言。</span><span class="sxs-lookup"><span data-stu-id="2ece9-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="2ece9-108">`x:Null`標記延伸可以沒有可設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="2ece9-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="2ece9-109">Null 使用量都通常與 CLR 的 XAML 成員公開<xref:System.Nullable%601>值。</span><span class="sxs-lookup"><span data-stu-id="2ece9-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="2ece9-110">`x:Null`像所有的 XAML 標記延伸的標記延伸使用大括號 (`{,}`) 屬性值而不是常值或參考事件處理常式處理逸出。</span><span class="sxs-lookup"><span data-stu-id="2ece9-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="2ece9-111">屬性語法是最常搭配這個標記延伸使用的語法。</span><span class="sxs-lookup"><span data-stu-id="2ece9-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="2ece9-112">物件項目語法`<x:Null />`可行，但很少使用，因為`x:Null`標記延伸可以沒有位置參數或建構引數。</span><span class="sxs-lookup"><span data-stu-id="2ece9-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="2ece9-113">如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="2ece9-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="2ece9-114">在.NET Framework XAML 服務，此標記延伸處理由定義<xref:System.Windows.Markup.NullExtension>類別。</span><span class="sxs-lookup"><span data-stu-id="2ece9-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="2ece9-115">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="2ece9-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="2ece9-116">請注意，`null`不一定是參考類型的相依性屬性未設定的初始值。</span><span class="sxs-lookup"><span data-stu-id="2ece9-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="2ece9-117">初始預設值為每個相依性屬性可能會不同，可以根據特定屬性的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2ece9-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="2ece9-118">不接受多個相依性屬性`null`做為值，方法是透過標記或程式碼，因為它們的驗證回呼實作。</span><span class="sxs-lookup"><span data-stu-id="2ece9-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="2ece9-119">如需相依性屬性的詳細資訊，請參閱[相依性屬性概觀](../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2ece9-119">For more information about dependency properties, see [Dependency Properties Overview](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ece9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ece9-120">See Also</span></span>  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [<span data-ttu-id="2ece9-121">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="2ece9-121">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="2ece9-122">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="2ece9-122">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
