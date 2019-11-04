---
title: x:Shared 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: c820a9b1d9708e24b1460378199a6addc1e20899
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459922"
---
# <a name="xshared-attribute"></a><span data-ttu-id="46733-102">x:Shared 屬性</span><span class="sxs-lookup"><span data-stu-id="46733-102">x:Shared Attribute</span></span>
<span data-ttu-id="46733-103">設定為 `false`時，會修改 WPF 資源抓取行為，讓屬性化資源的要求為每個要求建立新的實例，而不是共用所有要求的相同實例。</span><span class="sxs-lookup"><span data-stu-id="46733-103">When set to `false`, modifies WPF resource-retrieval behavior so that requests for the attributed resource create a new instance for each request instead of sharing the same instance for all requests.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="46733-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="46733-104">XAML Attribute Usage</span></span>  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a><span data-ttu-id="46733-105">備註</span><span class="sxs-lookup"><span data-stu-id="46733-105">Remarks</span></span>  
 <span data-ttu-id="46733-106">`x:Shared` 會對應至 XAML 語言 XAML 命名空間，並藉由 .NET Framework XAML 服務及其 XAML 讀取器來辨識為有效的 XAML 語言專案。</span><span class="sxs-lookup"><span data-stu-id="46733-106">`x:Shared` is mapped to the XAML language XAML namespace and is recognized as a valid XAML language element by .NET Framework XAML Services and its XAML readers.</span></span> <span data-ttu-id="46733-107">不過，`x:Shared` 所述的功能僅與 WPF 應用程式和 WPF XAML 剖析器有關。</span><span class="sxs-lookup"><span data-stu-id="46733-107">However, the stated capabilities of `x:Shared` are only relevant for WPF applications and for the WPF XAML parser.</span></span> <span data-ttu-id="46733-108">在 WPF 中，`x:Shared` 只有當屬性套用至存在於 WPF <xref:System.Windows.ResourceDictionary>內的物件時，才有用。</span><span class="sxs-lookup"><span data-stu-id="46733-108">In WPF, `x:Shared` is only useful as an attribute when it is applied to an object that exists within a WPF <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="46733-109">其他使用方式不會擲回剖析例外狀況或其他錯誤，但它們沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="46733-109">Other usages do not throw parse exceptions or other errors, but they have no effect.</span></span>  
  
 <span data-ttu-id="46733-110">XAML 語言規格中未指定 `x:Shared` 的意義。</span><span class="sxs-lookup"><span data-stu-id="46733-110">The meaning of `x:Shared` is not specified in the XAML language specification.</span></span> <span data-ttu-id="46733-111">其他 XAML 執行（例如建置於 .NET Framework XAML 服務上的）不一定會提供資源分享支援。</span><span class="sxs-lookup"><span data-stu-id="46733-111">Other XAML implementations, such as those that build on .NET Framework XAML Services, do not necessarily provide resource-sharing support.</span></span> <span data-ttu-id="46733-112">這類 XAML 執行可能會在支援的架構中，提供同樣用於 `x:Shared` 值的類似行為。</span><span class="sxs-lookup"><span data-stu-id="46733-112">Such XAML implementations could provide similar behavior in the supporting framework that also used `x:Shared` values.</span></span>  
  
 <span data-ttu-id="46733-113">在 WPF 中，資源的預設 `x:Shared` 條件是 `true`。</span><span class="sxs-lookup"><span data-stu-id="46733-113">In WPF, the default `x:Shared` condition for resources is `true`.</span></span> <span data-ttu-id="46733-114">這種情況表示任何指定的資源要求一律會傳回相同的實例。</span><span class="sxs-lookup"><span data-stu-id="46733-114">This condition means that any given resource request always returns the same instance.</span></span>  
  
 <span data-ttu-id="46733-115">修改透過資源 API 傳回的物件（例如 <xref:System.Windows.FrameworkElement.FindResource%2A>）或直接在 <xref:System.Windows.ResourceDictionary>中修改物件，會變更原始資源。</span><span class="sxs-lookup"><span data-stu-id="46733-115">Modifying an object that is returned through a resource API, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, or modifying an object directly within a <xref:System.Windows.ResourceDictionary>, changes the original resource.</span></span> <span data-ttu-id="46733-116">如果對該資源的參考是動態資源參考，該資源的取用者會取得已變更的資源。</span><span class="sxs-lookup"><span data-stu-id="46733-116">If references to that resource were dynamic resource references, the consumers of that resource get the changed resource.</span></span>  
  
 <span data-ttu-id="46733-117">如果資源的參考是靜態資源參考，則在 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 處理時間之後對資源所做的變更是不相關的。</span><span class="sxs-lookup"><span data-stu-id="46733-117">If references to the resource were static resource references, changes to the resource after [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing time are irrelevant.</span></span> <span data-ttu-id="46733-118">如需靜態與動態資源參考的詳細資訊，請參閱[XAML 資源](../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="46733-118">For more information about static versus dynamic resource references, see [XAML Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="46733-119">明確指定 `x:Shared="true"` 很少會完成，因為這已經是預設值。</span><span class="sxs-lookup"><span data-stu-id="46733-119">Explicitly specifying `x:Shared="true"` is rarely done, because that is already the default.</span></span> <span data-ttu-id="46733-120">WPF 物件模型中的 `x:Shared` 沒有直接的程式碼對應項;它只能在 XAML 使用方式中指定，而且如果使用 .NET Framework XAML 服務及其 XAML 讀取器來處理，則必須由預設 WPF 行為或載入路徑上的中繼 XAML 節點資料流程來處理。</span><span class="sxs-lookup"><span data-stu-id="46733-120">There is no direct code equivalent for `x:Shared` in the WPF object model; it can only be specified in a XAML usage and must be processed either by the default WPF behavior or in an intermediate XAML node stream on the load path if processed using .NET Framework XAML Services and its XAML readers.</span></span>  
  
 <span data-ttu-id="46733-121">`x:Shared="false"` 的案例是，如果您將 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 衍生的類別定義為資源，然後將元素資源引入內容模型中。</span><span class="sxs-lookup"><span data-stu-id="46733-121">A scenario for `x:Shared="false"` is if you define a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class as a resource and then you introduce the element resource into a content model.</span></span> <span data-ttu-id="46733-122">`x:Shared="false"` 可讓元素資源在同一個集合（例如 <xref:System.Windows.Controls.UIElementCollection>）中引進多次。</span><span class="sxs-lookup"><span data-stu-id="46733-122">`x:Shared="false"` enables an element resource to be introduced multiple times in the same collection (such as a <xref:System.Windows.Controls.UIElementCollection>).</span></span> <span data-ttu-id="46733-123">沒有 `x:Shared="false"` 這會無效，因為集合會強制執行其內容的唯一性。</span><span class="sxs-lookup"><span data-stu-id="46733-123">Without `x:Shared="false"` this is invalid because the collection enforces uniqueness of its contents.</span></span> <span data-ttu-id="46733-124">不過，`x:Shared="false"` 行為會建立另一個相同的資源實例，而不會傳回相同的實例。</span><span class="sxs-lookup"><span data-stu-id="46733-124">However, the `x:Shared="false"` behavior creates another identical instance of the resource instead of returning the same instance.</span></span>  
  
 <span data-ttu-id="46733-125">`x:Shared="false"` 的另一個案例是，如果您將 <xref:System.Windows.Freezable> 資源用於動畫值，但想要以每個動畫為基礎修改資源。</span><span class="sxs-lookup"><span data-stu-id="46733-125">Another scenario for `x:Shared="false"` is if you use a <xref:System.Windows.Freezable> resource for animation values but want to modify the resource on a per animation basis.</span></span>  
  
 <span data-ttu-id="46733-126">`false` 的字串處理不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="46733-126">The string handling of `false` is not case sensitive.</span></span>  
  
 <span data-ttu-id="46733-127">在 WPF 中，`x:Shared` 只有在下列情況下才有效：</span><span class="sxs-lookup"><span data-stu-id="46733-127">In WPF, `x:Shared` is only valid under the following conditions:</span></span>  
  
- <span data-ttu-id="46733-128">包含具有 `x:Shared` 之專案的 <xref:System.Windows.ResourceDictionary> 必須進行編譯。</span><span class="sxs-lookup"><span data-stu-id="46733-128">The <xref:System.Windows.ResourceDictionary> that contains the items with `x:Shared` must be compiled.</span></span> <span data-ttu-id="46733-129"><xref:System.Windows.ResourceDictionary> 不能在鬆散的 XAML 內或用於主題。</span><span class="sxs-lookup"><span data-stu-id="46733-129">The <xref:System.Windows.ResourceDictionary> cannot be within loose XAML or used for themes.</span></span>  
  
- <span data-ttu-id="46733-130">包含專案的 <xref:System.Windows.ResourceDictionary> 不得嵌套在另一個 <xref:System.Windows.ResourceDictionary>內。</span><span class="sxs-lookup"><span data-stu-id="46733-130">The <xref:System.Windows.ResourceDictionary> that contains the items must not be nested within another <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="46733-131">例如，您無法在已經是 <xref:System.Windows.ResourceDictionary> 專案的 <xref:System.Windows.Style> 中 <xref:System.Windows.ResourceDictionary> 專案使用 `x:Shared`。</span><span class="sxs-lookup"><span data-stu-id="46733-131">For example, you cannot use `x:Shared` for items in a <xref:System.Windows.ResourceDictionary> that is within a <xref:System.Windows.Style> that is already a <xref:System.Windows.ResourceDictionary> item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46733-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="46733-132">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- [<span data-ttu-id="46733-133">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="46733-133">XAML Resources</span></span>](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="46733-134">基底項目</span><span class="sxs-lookup"><span data-stu-id="46733-134">Base Elements</span></span>](../wpf/advanced/base-elements.md)
