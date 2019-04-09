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
ms.openlocfilehash: e46d8561b62d9137d4fed4df447338a97fc0577b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100804"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="87353-102">x:Null 標記延伸</span><span class="sxs-lookup"><span data-stu-id="87353-102">x:Null Markup Extension</span></span>
<span data-ttu-id="87353-103">指定`null`做為 XAML 成員的值。</span><span class="sxs-lookup"><span data-stu-id="87353-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="87353-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="87353-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="87353-105">備註</span><span class="sxs-lookup"><span data-stu-id="87353-105">Remarks</span></span>  
 <span data-ttu-id="87353-106">為 null 參考中的關鍵字C#並[!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)]為 null。</span><span class="sxs-lookup"><span data-stu-id="87353-106">The keyword for a null reference in C# and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="87353-107">是 null 參考的 Microsoft Visual Basic 關鍵字`Nothing`，但您一律使用`{x:Null}`視為 XAML 使用量不論哪一種程式碼後置的語言與相關聯的 XAML。</span><span class="sxs-lookup"><span data-stu-id="87353-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="87353-108">`x:Null`標記延伸模組沒有任何可設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="87353-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="87353-109">Null 的使用方式通常是相關聯的 CLR 的 XAML 成員公開<xref:System.Nullable%601>值。</span><span class="sxs-lookup"><span data-stu-id="87353-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="87353-110">`x:Null`標記延伸模組，所有 XAML 標記延伸模組，例如使用大括號 (`{,}`) 的逸出為常值或事件處理常式的參考以外的屬性值的處理。</span><span class="sxs-lookup"><span data-stu-id="87353-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="87353-111">屬性語法是最常搭配這個標記延伸語法。</span><span class="sxs-lookup"><span data-stu-id="87353-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="87353-112">物件元素語法`<x:Null />`技術上可行，但很少使用，因為`x:Null`標記延伸模組沒有任何位置參數 」 或 「 建構引數。</span><span class="sxs-lookup"><span data-stu-id="87353-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="87353-113">如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="87353-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="87353-114">在.NET Framework XAML 服務中，這個標記延伸的處理由定義<xref:System.Windows.Markup.NullExtension>類別。</span><span class="sxs-lookup"><span data-stu-id="87353-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="87353-115">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="87353-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="87353-116">請注意，`null`不一定是參考型別相依性屬性未設定的初始值。</span><span class="sxs-lookup"><span data-stu-id="87353-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="87353-117">初始預設值為每個相依性屬性而有所不同，並可根據特定屬性的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="87353-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="87353-118">許多相依性屬性不接受`null`為值時，透過標記或程式碼，因為它們的驗證回呼實作。</span><span class="sxs-lookup"><span data-stu-id="87353-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="87353-119">如需有關相依性屬性的詳細資訊，請參閱 <<c0> [ 相依性屬性概觀](../wpf/advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="87353-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87353-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87353-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="87353-121">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="87353-121">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="87353-122">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="87353-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
