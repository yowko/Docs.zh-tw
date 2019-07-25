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
ms.openlocfilehash: 7dbea2c7d4010d8defc572dbdc14a0dfd6d7601e
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484714"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="1685b-102">x:Null 標記延伸</span><span class="sxs-lookup"><span data-stu-id="1685b-102">x:Null Markup Extension</span></span>
<span data-ttu-id="1685b-103">指定`null`做為 XAML 成員的值。</span><span class="sxs-lookup"><span data-stu-id="1685b-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1685b-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="1685b-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="1685b-105">備註</span><span class="sxs-lookup"><span data-stu-id="1685b-105">Remarks</span></span>  
 <span data-ttu-id="1685b-106">和C# C++中 null 參考的關鍵字是 null。</span><span class="sxs-lookup"><span data-stu-id="1685b-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="1685b-107">Null 參考的 Microsoft Visual Basic 關鍵字是, 但`Nothing`無論您與 xaml 建立`{x:Null}`關聯的程式碼後置語言為何, 一律會使用做為 xaml 用法。</span><span class="sxs-lookup"><span data-stu-id="1685b-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="1685b-108">標記`x:Null`延伸沒有可設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="1685b-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="1685b-109">Null 用法通常與 CLR <xref:System.Nullable%601>值的 XAML 成員公開相關聯。</span><span class="sxs-lookup"><span data-stu-id="1685b-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="1685b-110">標記延伸與所有 XAML 標記延伸一樣, 都是使用大括弧`{,}`() 來將屬性值的處理, 轉義為非常值或事件處理常式參考。 `x:Null`</span><span class="sxs-lookup"><span data-stu-id="1685b-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="1685b-111">屬性語法是最常搭配此標記延伸使用的語法。</span><span class="sxs-lookup"><span data-stu-id="1685b-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="1685b-112">在技術上, `<x:Null />`物件專案語法是可行的, 但很少`x:Null`使用, 因為標記延伸沒有位置參數或結構引數。</span><span class="sxs-lookup"><span data-stu-id="1685b-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="1685b-113">如需標記延伸的詳細資訊, 請參閱[標記延伸和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="1685b-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="1685b-114">在 .NET Framework XAML 服務中, 此標記延伸的處理是由<xref:System.Windows.Markup.NullExtension>類別所定義。</span><span class="sxs-lookup"><span data-stu-id="1685b-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="1685b-115">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="1685b-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="1685b-116">請注意`null` , 不一定是參考型別相依性屬性的初始未設定值。</span><span class="sxs-lookup"><span data-stu-id="1685b-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="1685b-117">每個相依性屬性的初始預設值可能有所不同, 而且可以根據屬性特定的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1685b-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="1685b-118">許多相依性屬性都不`null`會接受作為值, 因為它們的驗證回呼是透過標記或程式碼。</span><span class="sxs-lookup"><span data-stu-id="1685b-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="1685b-119">如需相依性屬性的詳細資訊, 請參閱相依性[屬性總覽](../wpf/advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1685b-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1685b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1685b-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="1685b-121">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="1685b-121">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="1685b-122">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="1685b-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
