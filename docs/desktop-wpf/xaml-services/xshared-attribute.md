---
title: x:Shared 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: d5000b51d83066ec2d529db2033d8ac54f7ad329
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557784"
---
# <a name="xshared-attribute"></a><span data-ttu-id="950c5-102">x:Shared 屬性</span><span class="sxs-lookup"><span data-stu-id="950c5-102">x:Shared Attribute</span></span>

<span data-ttu-id="950c5-103">當設定為時 `false` ，會修改 WPF 資源抓取行為，如此一來，屬性化資源的要求就會為每個要求建立新的實例，而不是針對所有要求共用相同的實例。</span><span class="sxs-lookup"><span data-stu-id="950c5-103">When set to `false`, modifies WPF resource-retrieval behavior so that requests for the attributed resource create a new instance for each request instead of sharing the same instance for all requests.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="950c5-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="950c5-104">XAML Attribute Usage</span></span>

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a><span data-ttu-id="950c5-105">備註</span><span class="sxs-lookup"><span data-stu-id="950c5-105">Remarks</span></span>

<span data-ttu-id="950c5-106">`x:Shared` 會對應至 XAML 語言 XAML 命名空間，並由 .NET XAML 服務及其 XAML 讀取器辨識為有效的 XAML 語言元素。</span><span class="sxs-lookup"><span data-stu-id="950c5-106">`x:Shared` is mapped to the XAML language XAML namespace and is recognized as a valid XAML language element by .NET XAML Services and its XAML readers.</span></span> <span data-ttu-id="950c5-107">不過，所述的功能 `x:Shared` 只適用于 wpf 應用程式和 WPF XAML 剖析器。</span><span class="sxs-lookup"><span data-stu-id="950c5-107">However, the stated capabilities of `x:Shared` are only relevant for WPF applications and for the WPF XAML parser.</span></span> <span data-ttu-id="950c5-108">在 WPF 中， `x:Shared` 只有當屬性套用至存在於 wpf 中的物件時，才會用來做為屬性 <xref:System.Windows.ResourceDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="950c5-108">In WPF, `x:Shared` is only useful as an attribute when it is applied to an object that exists within a WPF <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="950c5-109">其他使用方式不會擲回 parse 例外狀況或其他錯誤，但它們沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="950c5-109">Other usages do not throw parse exceptions or other errors, but they have no effect.</span></span>

<span data-ttu-id="950c5-110">`x:Shared`XAML 語言規格中未指定的意義。</span><span class="sxs-lookup"><span data-stu-id="950c5-110">The meaning of `x:Shared` is not specified in the XAML language specification.</span></span> <span data-ttu-id="950c5-111">其他 XAML 執行（例如在 .NET XAML 服務上建立的）不一定會提供資源分享支援。</span><span class="sxs-lookup"><span data-stu-id="950c5-111">Other XAML implementations, such as those that build on .NET XAML Services, do not necessarily provide resource-sharing support.</span></span> <span data-ttu-id="950c5-112">這類 XAML 實值可能會在支援的架構中提供同樣使用值的類似行為 `x:Shared` 。</span><span class="sxs-lookup"><span data-stu-id="950c5-112">Such XAML implementations could provide similar behavior in the supporting framework that also used `x:Shared` values.</span></span>

<span data-ttu-id="950c5-113">在 WPF 中，資源的預設 `x:Shared` 條件為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="950c5-113">In WPF, the default `x:Shared` condition for resources is `true`.</span></span> <span data-ttu-id="950c5-114">這種情況表示任何指定的資源要求一律會傳回相同的實例。</span><span class="sxs-lookup"><span data-stu-id="950c5-114">This condition means that any given resource request always returns the same instance.</span></span>

<span data-ttu-id="950c5-115">修改透過資源 API 傳回的物件（例如 <xref:System.Windows.FrameworkElement.FindResource%2A> ，或直接在中修改物件 <xref:System.Windows.ResourceDictionary> ），會變更原始資源。</span><span class="sxs-lookup"><span data-stu-id="950c5-115">Modifying an object that is returned through a resource API, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, or modifying an object directly within a <xref:System.Windows.ResourceDictionary>, changes the original resource.</span></span> <span data-ttu-id="950c5-116">如果該資源的參考是動態資源參考，則該資源的取用者會取得變更的資源。</span><span class="sxs-lookup"><span data-stu-id="950c5-116">If references to that resource were dynamic resource references, the consumers of that resource get the changed resource.</span></span>

<span data-ttu-id="950c5-117">如果資源的參考是靜態資源參考，則在處理時間之後變更資源 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 將不相關。</span><span class="sxs-lookup"><span data-stu-id="950c5-117">If references to the resource were static resource references, changes to the resource after [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing time are irrelevant.</span></span> <span data-ttu-id="950c5-118">如需有關靜態與動態資源參考的詳細資訊，請參閱 [XAML 資源](../fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="950c5-118">For more information about static versus dynamic resource references, see [XAML Resources](../fundamentals/xaml-resources-define.md).</span></span>

<span data-ttu-id="950c5-119">明確指定很 `x:Shared="true"` 少會完成，因為這已經是預設值。</span><span class="sxs-lookup"><span data-stu-id="950c5-119">Explicitly specifying `x:Shared="true"` is rarely done, because that is already the default.</span></span> <span data-ttu-id="950c5-120">WPF 物件模型中沒有對等的直接程式碼， `x:Shared` 它只能以 XAML 使用方式指定，且必須由預設 WPF 行為或在載入路徑上的中繼 XAML 節點資料流程中進行處理（如果使用 .NET XAML 服務及其 XAML 讀取器來處理的話）。</span><span class="sxs-lookup"><span data-stu-id="950c5-120">There is no direct code equivalent for `x:Shared` in the WPF object model; it can only be specified in a XAML usage and must be processed either by the default WPF behavior or in an intermediate XAML node stream on the load path if processed using .NET XAML Services and its XAML readers.</span></span>

<span data-ttu-id="950c5-121">的案例 `x:Shared="false"` 是，如果您將 <xref:System.Windows.FrameworkElement> 或衍生的類別定義 <xref:System.Windows.FrameworkContentElement> 為資源，然後將元素資源引入內容模型中。</span><span class="sxs-lookup"><span data-stu-id="950c5-121">A scenario for `x:Shared="false"` is if you define a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class as a resource and then you introduce the element resource into a content model.</span></span> <span data-ttu-id="950c5-122">`x:Shared="false"` 可讓元素資源在相同的集合中多次導入 (例如 <xref:System.Windows.Controls.UIElementCollection>) 。</span><span class="sxs-lookup"><span data-stu-id="950c5-122">`x:Shared="false"` enables an element resource to be introduced multiple times in the same collection (such as a <xref:System.Windows.Controls.UIElementCollection>).</span></span> <span data-ttu-id="950c5-123">沒有 `x:Shared="false"` 此項是不正確，因為集合會強制執行其內容的唯一性。</span><span class="sxs-lookup"><span data-stu-id="950c5-123">Without `x:Shared="false"` this is invalid because the collection enforces uniqueness of its contents.</span></span> <span data-ttu-id="950c5-124">不過，此 `x:Shared="false"` 行為會建立另一個相同的資源實例，而不會傳回相同的實例。</span><span class="sxs-lookup"><span data-stu-id="950c5-124">However, the `x:Shared="false"` behavior creates another identical instance of the resource instead of returning the same instance.</span></span>

<span data-ttu-id="950c5-125">另一種情況 `x:Shared="false"` 是，如果您將 <xref:System.Windows.Freezable> 資源用於動畫值，但想要以每個動畫為基礎修改資源。</span><span class="sxs-lookup"><span data-stu-id="950c5-125">Another scenario for `x:Shared="false"` is if you use a <xref:System.Windows.Freezable> resource for animation values but want to modify the resource on a per animation basis.</span></span>

<span data-ttu-id="950c5-126">的字串處理 `false` 不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="950c5-126">The string handling of `false` is not case sensitive.</span></span>

<span data-ttu-id="950c5-127">在 WPF 中， `x:Shared` 只有在下列情況下才有效：</span><span class="sxs-lookup"><span data-stu-id="950c5-127">In WPF, `x:Shared` is only valid under the following conditions:</span></span>

- <span data-ttu-id="950c5-128"><xref:System.Windows.ResourceDictionary>包含 `x:Shared` 必須編譯之專案的。</span><span class="sxs-lookup"><span data-stu-id="950c5-128">The <xref:System.Windows.ResourceDictionary> that contains the items with `x:Shared` must be compiled.</span></span> <span data-ttu-id="950c5-129"><xref:System.Windows.ResourceDictionary>不能在鬆散的 XAML 內或用於主題。</span><span class="sxs-lookup"><span data-stu-id="950c5-129">The <xref:System.Windows.ResourceDictionary> cannot be within loose XAML or used for themes.</span></span>

- <span data-ttu-id="950c5-130"><xref:System.Windows.ResourceDictionary>包含專案的不能在另一個中嵌套 <xref:System.Windows.ResourceDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="950c5-130">The <xref:System.Windows.ResourceDictionary> that contains the items must not be nested within another <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="950c5-131">例如，您無法將 `x:Shared` 中的專案用於已經是專案的內的專案 <xref:System.Windows.ResourceDictionary> <xref:System.Windows.Style> <xref:System.Windows.ResourceDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="950c5-131">For example, you cannot use `x:Shared` for items in a <xref:System.Windows.ResourceDictionary> that is within a <xref:System.Windows.Style> that is already a <xref:System.Windows.ResourceDictionary> item.</span></span>

## <a name="see-also"></a><span data-ttu-id="950c5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="950c5-132">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- [<span data-ttu-id="950c5-133">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="950c5-133">XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="950c5-134">基底項目</span><span class="sxs-lookup"><span data-stu-id="950c5-134">Base Elements</span></span>](/dotnet/desktop/wpf/advanced/base-elements)
