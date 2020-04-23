---
title: x:Shared 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: e1cd1d9db5c19decd840b433f986e0ba53557a8b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071371"
---
# <a name="xshared-attribute"></a><span data-ttu-id="27040-102">x:Shared 屬性</span><span class="sxs-lookup"><span data-stu-id="27040-102">x:Shared Attribute</span></span>

<span data-ttu-id="27040-103">設置為`false`時 ,將修改 WPF 資源檢索行為,以便對屬性化資源的請求為每個請求創建一個新實例,而不是為所有請求共用相同的實例。</span><span class="sxs-lookup"><span data-stu-id="27040-103">When set to `false`, modifies WPF resource-retrieval behavior so that requests for the attributed resource create a new instance for each request instead of sharing the same instance for all requests.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="27040-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="27040-104">XAML Attribute Usage</span></span>

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a><span data-ttu-id="27040-105">備註</span><span class="sxs-lookup"><span data-stu-id="27040-105">Remarks</span></span>

<span data-ttu-id="27040-106">`x:Shared`映射到 XAML 語言 XAML 命名空間,並由 .NET XAML 服務及其 XAML 讀取器識別為有效的 XAML 語言元素。</span><span class="sxs-lookup"><span data-stu-id="27040-106">`x:Shared` is mapped to the XAML language XAML namespace and is recognized as a valid XAML language element by .NET XAML Services and its XAML readers.</span></span> <span data-ttu-id="27040-107">但是,聲明`x:Shared`的功能僅與 WPF 應用程式和 WPF XAML 解析器相關。</span><span class="sxs-lookup"><span data-stu-id="27040-107">However, the stated capabilities of `x:Shared` are only relevant for WPF applications and for the WPF XAML parser.</span></span> <span data-ttu-id="27040-108">在 WPF`x:Shared`中,僅當屬性應用於存在於<xref:System.Windows.ResourceDictionary>WPF 中的物件時,它才可用作屬性。</span><span class="sxs-lookup"><span data-stu-id="27040-108">In WPF, `x:Shared` is only useful as an attribute when it is applied to an object that exists within a WPF <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="27040-109">其他用法不會引發解析異常或其他錯誤,但它們沒有效果。</span><span class="sxs-lookup"><span data-stu-id="27040-109">Other usages do not throw parse exceptions or other errors, but they have no effect.</span></span>

<span data-ttu-id="27040-110">在 XAML 語言規範中未`x:Shared`指定 其 含義。</span><span class="sxs-lookup"><span data-stu-id="27040-110">The meaning of `x:Shared` is not specified in the XAML language specification.</span></span> <span data-ttu-id="27040-111">其他 XAML 實現(例如基於 .NET XAML 服務實現)不一定提供資源分享支援。</span><span class="sxs-lookup"><span data-stu-id="27040-111">Other XAML implementations, such as those that build on .NET XAML Services, do not necessarily provide resource-sharing support.</span></span> <span data-ttu-id="27040-112">此類 XAML 實現可以在支援框架中提供類似的行為,`x:Shared`該框架 也使用值。</span><span class="sxs-lookup"><span data-stu-id="27040-112">Such XAML implementations could provide similar behavior in the supporting framework that also used `x:Shared` values.</span></span>

<span data-ttu-id="27040-113">在 WPF`x:Shared`中,資源的預設`true`條件是 。</span><span class="sxs-lookup"><span data-stu-id="27040-113">In WPF, the default `x:Shared` condition for resources is `true`.</span></span> <span data-ttu-id="27040-114">此條件表示任何給定的資源請求始終返回同一實例。</span><span class="sxs-lookup"><span data-stu-id="27040-114">This condition means that any given resource request always returns the same instance.</span></span>

<span data-ttu-id="27040-115">修改通過資源 API 傳回的物件(<xref:System.Windows.FrameworkElement.FindResource%2A>如 ,或<xref:System.Windows.ResourceDictionary>直接修改中的物件)會更改原始資源。</span><span class="sxs-lookup"><span data-stu-id="27040-115">Modifying an object that is returned through a resource API, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, or modifying an object directly within a <xref:System.Windows.ResourceDictionary>, changes the original resource.</span></span> <span data-ttu-id="27040-116">如果對該資源的引用是動態資源引用,則該資源的消費者將獲取已更改的資源。</span><span class="sxs-lookup"><span data-stu-id="27040-116">If references to that resource were dynamic resource references, the consumers of that resource get the changed resource.</span></span>

<span data-ttu-id="27040-117">如果對資源的引用是靜態資源引用,則處理時間後[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]對資源的更改不相關。</span><span class="sxs-lookup"><span data-stu-id="27040-117">If references to the resource were static resource references, changes to the resource after [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing time are irrelevant.</span></span> <span data-ttu-id="27040-118">有關靜態資源引用和動態資源引用的詳細資訊,請參閱[XAML 資源](../fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="27040-118">For more information about static versus dynamic resource references, see [XAML Resources](../fundamentals/xaml-resources-define.md).</span></span>

<span data-ttu-id="27040-119">顯式指定`x:Shared="true"`很少完成,因為這已經是預設值。</span><span class="sxs-lookup"><span data-stu-id="27040-119">Explicitly specifying `x:Shared="true"` is rarely done, because that is already the default.</span></span> <span data-ttu-id="27040-120">在 WPF 物件`x:Shared`模型中 沒有直接代碼等效;它只能在 XAML 用法中指定,並且如果使用 .NET XAML 服務及其 XAML 讀取器進行處理,則必須通過預設的 WPF 行為或在負載路徑上的中間 XAML 節點流中進行處理。</span><span class="sxs-lookup"><span data-stu-id="27040-120">There is no direct code equivalent for `x:Shared` in the WPF object model; it can only be specified in a XAML usage and must be processed either by the default WPF behavior or in an intermediate XAML node stream on the load path if processed using .NET XAML Services and its XAML readers.</span></span>

<span data-ttu-id="27040-121">的方案`x:Shared="false"`是,如果將<xref:System.Windows.FrameworkElement><xref:System.Windows.FrameworkContentElement>或 派生類定義為資源,然後將元素資源引入內容模型。</span><span class="sxs-lookup"><span data-stu-id="27040-121">A scenario for `x:Shared="false"` is if you define a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class as a resource and then you introduce the element resource into a content model.</span></span> <span data-ttu-id="27040-122">`x:Shared="false"`使元素資源在同一集合(如<xref:System.Windows.Controls.UIElementCollection>) 中多次引入。</span><span class="sxs-lookup"><span data-stu-id="27040-122">`x:Shared="false"` enables an element resource to be introduced multiple times in the same collection (such as a <xref:System.Windows.Controls.UIElementCollection>).</span></span> <span data-ttu-id="27040-123">如果沒有`x:Shared="false"`此選項無效,因為集合會強制其內容的唯一性。</span><span class="sxs-lookup"><span data-stu-id="27040-123">Without `x:Shared="false"` this is invalid because the collection enforces uniqueness of its contents.</span></span> <span data-ttu-id="27040-124">但是,該`x:Shared="false"`行為將創建資源的另一個相同實例,而不是返回相同的實例。</span><span class="sxs-lookup"><span data-stu-id="27040-124">However, the `x:Shared="false"` behavior creates another identical instance of the resource instead of returning the same instance.</span></span>

<span data-ttu-id="27040-125">的另一<xref:System.Windows.Freezable>`x:Shared="false"`個 方案是,如果將資源用於動畫值,但希望根據每個動畫修改資源。</span><span class="sxs-lookup"><span data-stu-id="27040-125">Another scenario for `x:Shared="false"` is if you use a <xref:System.Windows.Freezable> resource for animation values but want to modify the resource on a per animation basis.</span></span>

<span data-ttu-id="27040-126">的`false`字串處理不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="27040-126">The string handling of `false` is not case sensitive.</span></span>

<span data-ttu-id="27040-127">在 WPF`x:Shared`中,僅在以下條件下有效:</span><span class="sxs-lookup"><span data-stu-id="27040-127">In WPF, `x:Shared` is only valid under the following conditions:</span></span>

- <span data-ttu-id="27040-128"><xref:System.Windows.ResourceDictionary>必須編譯包含的`x:Shared`項。</span><span class="sxs-lookup"><span data-stu-id="27040-128">The <xref:System.Windows.ResourceDictionary> that contains the items with `x:Shared` must be compiled.</span></span> <span data-ttu-id="27040-129"><xref:System.Windows.ResourceDictionary>不能在鬆散的 XAML 內或用於主題。</span><span class="sxs-lookup"><span data-stu-id="27040-129">The <xref:System.Windows.ResourceDictionary> cannot be within loose XAML or used for themes.</span></span>

- <span data-ttu-id="27040-130"><xref:System.Windows.ResourceDictionary>包含項的 不能嵌套在另一<xref:System.Windows.ResourceDictionary>個 中。</span><span class="sxs-lookup"><span data-stu-id="27040-130">The <xref:System.Windows.ResourceDictionary> that contains the items must not be nested within another <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="27040-131">例如`x:Shared`,不能<xref:System.Windows.ResourceDictionary>用於已<xref:System.Windows.Style><xref:System.Windows.ResourceDictionary>屬於項的中的項。</span><span class="sxs-lookup"><span data-stu-id="27040-131">For example, you cannot use `x:Shared` for items in a <xref:System.Windows.ResourceDictionary> that is within a <xref:System.Windows.Style> that is already a <xref:System.Windows.ResourceDictionary> item.</span></span>

## <a name="see-also"></a><span data-ttu-id="27040-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27040-132">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- [<span data-ttu-id="27040-133">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="27040-133">XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="27040-134">基底項目</span><span class="sxs-lookup"><span data-stu-id="27040-134">Base Elements</span></span>](../../framework/wpf/advanced/base-elements.md)
