---
title: x:Shared 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: da35f209b632bdf9e4ab2298239a505df69d6048
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125732"
---
# <a name="xshared-attribute"></a><span data-ttu-id="c8224-102">x:Shared 屬性</span><span class="sxs-lookup"><span data-stu-id="c8224-102">x:Shared Attribute</span></span>
<span data-ttu-id="c8224-103">當設定為`false`，修改 WPF 擷取資源的行為，讓屬性化資源的要求建立新的執行個體，針對每個要求，而不是共用相同的執行個體的所有要求。</span><span class="sxs-lookup"><span data-stu-id="c8224-103">When set to `false`, modifies WPF resource-retrieval behavior so that requests for the attributed resource create a new instance for each request instead of sharing the same instance for all requests.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c8224-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="c8224-104">XAML Attribute Usage</span></span>  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a><span data-ttu-id="c8224-105">備註</span><span class="sxs-lookup"><span data-stu-id="c8224-105">Remarks</span></span>  
 `x:Shared` <span data-ttu-id="c8224-106">對應至 XAML 語言 XAML 命名空間，且.NET Framework XAML 服務和其 XAML 讀取器所辨識為有效的 XAML 語言項目。</span><span class="sxs-lookup"><span data-stu-id="c8224-106">is mapped to the XAML language XAML namespace and is recognized as a valid XAML language element by .NET Framework XAML Services and its XAML readers.</span></span> <span data-ttu-id="c8224-107">不過，所述的功能`x:Shared`才相關 WPF 應用程式和 WPF XAML 剖析器。</span><span class="sxs-lookup"><span data-stu-id="c8224-107">However, the stated capabilities of `x:Shared` are only relevant for WPF applications and for the WPF XAML parser.</span></span> <span data-ttu-id="c8224-108">在 WPF 中，`x:Shared`才有用做為屬性，它會套用至存在於 WPF 中的物件時<xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="c8224-108">In WPF, `x:Shared` is only useful as an attribute when it is applied to an object that exists within a WPF <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="c8224-109">其他使用方式不擲回剖析例外狀況或其他錯誤，但它們沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="c8224-109">Other usages do not throw parse exceptions or other errors, but they have no effect.</span></span>  
  
 <span data-ttu-id="c8224-110">意義`x:Shared`XAML 語言規格中未指定。</span><span class="sxs-lookup"><span data-stu-id="c8224-110">The meaning of `x:Shared` is not specified in the XAML language specification.</span></span> <span data-ttu-id="c8224-111">其他 XAML 實作中的，例如建置在.NET Framework XAML 服務中，不一定會提供資源共用的支援。</span><span class="sxs-lookup"><span data-stu-id="c8224-111">Other XAML implementations, such as those that build on .NET Framework XAML Services, do not necessarily provide resource-sharing support.</span></span> <span data-ttu-id="c8224-112">這類的 XAML 實作可以提供類似的行為，在支援的架構，也可以用`x:Shared`值。</span><span class="sxs-lookup"><span data-stu-id="c8224-112">Such XAML implementations could provide similar behavior in the supporting framework that also used `x:Shared` values.</span></span>  
  
 <span data-ttu-id="c8224-113">在 WPF 中，預設值`x:Shared`資源的條件是`true`。</span><span class="sxs-lookup"><span data-stu-id="c8224-113">In WPF, the default `x:Shared` condition for resources is `true`.</span></span> <span data-ttu-id="c8224-114">這種情況表示，任何指定的資源要求一律會傳回相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c8224-114">This condition means that any given resource request always returns the same instance.</span></span>  
  
 <span data-ttu-id="c8224-115">修改物件，例如傳回資源的 API，透過<xref:System.Windows.FrameworkElement.FindResource%2A>，或修改物件直接內<xref:System.Windows.ResourceDictionary>，變更原始的資源。</span><span class="sxs-lookup"><span data-stu-id="c8224-115">Modifying an object that is returned through a resource API, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, or modifying an object directly within a <xref:System.Windows.ResourceDictionary>, changes the original resource.</span></span> <span data-ttu-id="c8224-116">如果該資源的參考動態資源參考，該資源的取用者會取得已變更的資源。</span><span class="sxs-lookup"><span data-stu-id="c8224-116">If references to that resource were dynamic resource references, the consumers of that resource get the changed resource.</span></span>  
  
 <span data-ttu-id="c8224-117">如果資源的參考靜態資源參考，變更後的資源為[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]處理時間無關。</span><span class="sxs-lookup"><span data-stu-id="c8224-117">If references to the resource were static resource references, changes to the resource after [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing time are irrelevant.</span></span> <span data-ttu-id="c8224-118">如需靜態與動態資源參考的詳細資訊，請參閱[XAML 資源](../wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="c8224-118">For more information about static versus dynamic resource references, see [XAML Resources](../wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="c8224-119">明確指定`x:Shared="true"`很罕見，因為這已經是預設值。</span><span class="sxs-lookup"><span data-stu-id="c8224-119">Explicitly specifying `x:Shared="true"` is rarely done, because that is already the default.</span></span> <span data-ttu-id="c8224-120">沒有對等的程式碼直接`x:Shared`WPF 中的物件模型; 它只能指定在 XAML 用法，並必須處理的預設 WPF 行為或中繼上載入路徑 XAML 節點資料流中，如果使用.NET Framework XAML Se 處理rvices 和其 XAML 讀取器。</span><span class="sxs-lookup"><span data-stu-id="c8224-120">There is no direct code equivalent for `x:Shared` in the WPF object model; it can only be specified in a XAML usage and must be processed either by the default WPF behavior or in an intermediate XAML node stream on the load path if processed using .NET Framework XAML Services and its XAML readers.</span></span>  
  
 <span data-ttu-id="c8224-121">案例`x:Shared="false"`就是如果您定義<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>衍生類別做為資源，然後您引入的項目資源內容的模型。</span><span class="sxs-lookup"><span data-stu-id="c8224-121">A scenario for `x:Shared="false"` is if you define a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class as a resource and then you introduce the element resource into a content model.</span></span> `x:Shared="false"` <span data-ttu-id="c8224-122">可讓在相同的集合，將推出許多次的項目資源 (例如<xref:System.Windows.Controls.UIElementCollection>)。</span><span class="sxs-lookup"><span data-stu-id="c8224-122">enables an element resource to be introduced multiple times in the same collection (such as a <xref:System.Windows.Controls.UIElementCollection>).</span></span> <span data-ttu-id="c8224-123">不含`x:Shared="false"`這是無效的因為集合會強制執行唯一性的內容。</span><span class="sxs-lookup"><span data-stu-id="c8224-123">Without `x:Shared="false"` this is invalid because the collection enforces uniqueness of its contents.</span></span> <span data-ttu-id="c8224-124">不過，`x:Shared="false"`行為會建立另一個資源，而不是傳回相同的執行個體的相同執行個體。</span><span class="sxs-lookup"><span data-stu-id="c8224-124">However, the `x:Shared="false"` behavior creates another identical instance of the resource instead of returning the same instance.</span></span>  
  
 <span data-ttu-id="c8224-125">另一個情節`x:Shared="false"`是如果您使用<xref:System.Windows.Freezable>動畫值，但想来修改的資源，以每個動畫為基礎的資源。</span><span class="sxs-lookup"><span data-stu-id="c8224-125">Another scenario for `x:Shared="false"` is if you use a <xref:System.Windows.Freezable> resource for animation values but want to modify the resource on a per animation basis.</span></span>  
  
 <span data-ttu-id="c8224-126">字串處理`false`不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c8224-126">The string handling of `false` is not case sensitive.</span></span>  
  
 <span data-ttu-id="c8224-127">在 WPF 中，`x:Shared`下列條件下才有效：</span><span class="sxs-lookup"><span data-stu-id="c8224-127">In WPF, `x:Shared` is only valid under the following conditions:</span></span>  
  
-   <span data-ttu-id="c8224-128"><xref:System.Windows.ResourceDictionary>所包含的項目`x:Shared`必須編譯。</span><span class="sxs-lookup"><span data-stu-id="c8224-128">The <xref:System.Windows.ResourceDictionary> that contains the items with `x:Shared` must be compiled.</span></span> <span data-ttu-id="c8224-129"><xref:System.Windows.ResourceDictionary>不可在鬆散的 XAML，或用於佈景主題。</span><span class="sxs-lookup"><span data-stu-id="c8224-129">The <xref:System.Windows.ResourceDictionary> cannot be within loose XAML or used for themes.</span></span>  
  
-   <span data-ttu-id="c8224-130"><xref:System.Windows.ResourceDictionary>所包含的項目進行巢狀在另一個<xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="c8224-130">The <xref:System.Windows.ResourceDictionary> that contains the items must not be nested within another <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="c8224-131">例如，您無法使用`x:Shared`中的項目<xref:System.Windows.ResourceDictionary>裡<xref:System.Windows.Style>已經<xref:System.Windows.ResourceDictionary>項目。</span><span class="sxs-lookup"><span data-stu-id="c8224-131">For example, you cannot use `x:Shared` for items in a <xref:System.Windows.ResourceDictionary> that is within a <xref:System.Windows.Style> that is already a <xref:System.Windows.ResourceDictionary> item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8224-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8224-132">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- [<span data-ttu-id="c8224-133">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="c8224-133">XAML Resources</span></span>](../wpf/advanced/xaml-resources.md)
- [<span data-ttu-id="c8224-134">基底項目</span><span class="sxs-lookup"><span data-stu-id="c8224-134">Base Elements</span></span>](../wpf/advanced/base-elements.md)
