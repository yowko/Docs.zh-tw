---
title: x:Null 標記延伸
ms.date: 03/30/2017
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
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071427"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="33c1e-102">x:Null 標記延伸</span><span class="sxs-lookup"><span data-stu-id="33c1e-102">x:Null Markup Extension</span></span>

<span data-ttu-id="33c1e-103">指定`null`為 XAML 成員的值。</span><span class="sxs-lookup"><span data-stu-id="33c1e-103">Specifies `null` as a value for a XAML member.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="33c1e-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="33c1e-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="33c1e-105">備註</span><span class="sxs-lookup"><span data-stu-id="33c1e-105">Remarks</span></span>

<span data-ttu-id="33c1e-106">C# 和 C++ 中空引用的關鍵字為 null。</span><span class="sxs-lookup"><span data-stu-id="33c1e-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="33c1e-107">對於 null 引用的 Microsoft `Nothing`Visual Basic 關鍵字是`{x:Null}`,但無論與 XAML 關聯的代碼後面語言如何,您始終用作 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="33c1e-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>

<span data-ttu-id="33c1e-108">標記`x:Null`擴展沒有可設置屬性。</span><span class="sxs-lookup"><span data-stu-id="33c1e-108">The `x:Null` markup extension has no settable properties.</span></span>

<span data-ttu-id="33c1e-109">空用法通常與 CLR<xref:System.Nullable%601>值的 XAML 成員暴露相關聯。</span><span class="sxs-lookup"><span data-stu-id="33c1e-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>

<span data-ttu-id="33c1e-110">標記`x:Null`延伸與所有 XAML 標籤延伸一樣,使用大括`{,}`弧 ( ) 來轉義屬性值的處理,以非文本或事件處理程式引用。</span><span class="sxs-lookup"><span data-stu-id="33c1e-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="33c1e-111">屬性語法是最常用於此標記擴展的語法。</span><span class="sxs-lookup"><span data-stu-id="33c1e-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="33c1e-112">物件元素語法`<x:Null />`在技術上是可能的,但很少使用`x:Null`, 因為標記擴展沒有位置參數或構造參數。</span><span class="sxs-lookup"><span data-stu-id="33c1e-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>

<span data-ttu-id="33c1e-113">有關標記延伸的資訊,請參閱[標籤延伸和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="33c1e-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>

<span data-ttu-id="33c1e-114">在 .NET XAML 服務中,此標記擴展<xref:System.Windows.Markup.NullExtension>的處理由 類定義。</span><span class="sxs-lookup"><span data-stu-id="33c1e-114">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="33c1e-115">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="33c1e-115">WPF Usage Notes</span></span>

<span data-ttu-id="33c1e-116">請注意,`null`不一定是引用類型依賴項屬性的初始未設置值。</span><span class="sxs-lookup"><span data-stu-id="33c1e-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="33c1e-117">初始預設值可能因依賴項屬性而異,並且可以基於特定於屬性的元數據。</span><span class="sxs-lookup"><span data-stu-id="33c1e-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="33c1e-118">許多依賴項屬性不接受`null`作為值,無論是通過標記還是代碼,因為它們的驗證回調實現。</span><span class="sxs-lookup"><span data-stu-id="33c1e-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="33c1e-119">有關相依項屬性的詳細資訊,請參閱[相依項屬性概述](../../framework/wpf/advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="33c1e-119">For more information about dependency properties, see [Dependency Properties Overview](../../framework/wpf/advanced/dependency-properties-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33c1e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33c1e-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="33c1e-121">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="33c1e-121">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="33c1e-122">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="33c1e-122">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
