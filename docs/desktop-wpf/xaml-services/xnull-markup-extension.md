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
ms.openlocfilehash: f4971d61d11ec14eaeac2d2f202353e4921b9325
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549440"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="91950-102">x:Null 標記延伸</span><span class="sxs-lookup"><span data-stu-id="91950-102">x:Null Markup Extension</span></span>

<span data-ttu-id="91950-103">指定 `null` 為 XAML 成員的值。</span><span class="sxs-lookup"><span data-stu-id="91950-103">Specifies `null` as a value for a XAML member.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="91950-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="91950-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="91950-105">備註</span><span class="sxs-lookup"><span data-stu-id="91950-105">Remarks</span></span>

<span data-ttu-id="91950-106">C # 和 c + + 中 null 參考的關鍵字是 null。</span><span class="sxs-lookup"><span data-stu-id="91950-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="91950-107">Null 參考的 Microsoft Visual Basic 關鍵字為 `Nothing` ，但 `{x:Null}` 不論您與 xaml 相關聯的程式碼後端語言為何，您一律會使用做為 xaml 用法。</span><span class="sxs-lookup"><span data-stu-id="91950-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>

<span data-ttu-id="91950-108">`x:Null`標記延伸沒有可設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="91950-108">The `x:Null` markup extension has no settable properties.</span></span>

<span data-ttu-id="91950-109">Null 使用量通常會與 CLR 值的 XAML 成員公開相關聯 <xref:System.Nullable%601> 。</span><span class="sxs-lookup"><span data-stu-id="91950-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>

<span data-ttu-id="91950-110">`x:Null`標記延伸（如同所有 XAML 標記延伸）會使用大括弧 (`{,}`) ，將屬性值的處理方式，轉義為常值或事件處理常式參考。</span><span class="sxs-lookup"><span data-stu-id="91950-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="91950-111">屬性語法是最常搭配此標記延伸使用的語法。</span><span class="sxs-lookup"><span data-stu-id="91950-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="91950-112">物件元素語法 `<x:Null />` 在技術上是可行的，但很少使用，因為 `x:Null` 標記延伸沒有位置參數或結構引數。</span><span class="sxs-lookup"><span data-stu-id="91950-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>

<span data-ttu-id="91950-113">如需標記延伸的詳細資訊，請參閱 [標記延伸和 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)。</span><span class="sxs-lookup"><span data-stu-id="91950-113">For information about markup extensions, see [Markup Extensions and WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).</span></span>

<span data-ttu-id="91950-114">在 .NET XAML 服務中，此標記延伸的處理是由類別所定義 <xref:System.Windows.Markup.NullExtension> 。</span><span class="sxs-lookup"><span data-stu-id="91950-114">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="91950-115">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="91950-115">WPF Usage Notes</span></span>

<span data-ttu-id="91950-116">請注意， `null` 不一定是參考型別相依性屬性的初始未設定值。</span><span class="sxs-lookup"><span data-stu-id="91950-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="91950-117">初始預設值可能會因每個相依性屬性而異，而且可以根據屬性專屬的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="91950-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="91950-118">許多相依性屬性都不接受 `null` 作為值，因為它們的驗證回呼是透過標記或程式碼。</span><span class="sxs-lookup"><span data-stu-id="91950-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="91950-119">如需相依性屬性的詳細資訊，請參閱相依性 [屬性總覽](/dotnet/desktop/wpf/advanced/dependency-properties-overview)。</span><span class="sxs-lookup"><span data-stu-id="91950-119">For more information about dependency properties, see [Dependency Properties Overview](/dotnet/desktop/wpf/advanced/dependency-properties-overview).</span></span>

## <a name="see-also"></a><span data-ttu-id="91950-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91950-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="91950-121">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="91950-121">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="91950-122">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="91950-122">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
