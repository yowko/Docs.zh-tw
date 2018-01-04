---
title: "x:Shared 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9cc5e2bff9cc2591c7a12630da5422dbf73713a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xshared-attribute"></a><span data-ttu-id="e7bf2-102">x:Shared 屬性</span><span class="sxs-lookup"><span data-stu-id="e7bf2-102">x:Shared Attribute</span></span>
<span data-ttu-id="e7bf2-103">當設定為`false`，修改 WPF 擷取資源的行為，讓屬性化的資源的要求建立每個要求而不是共用相同的執行個體的所有要求的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-103">When set to `false`, modifies WPF resource-retrieval behavior so that requests for the attributed resource create a new instance for each request instead of sharing the same instance for all requests.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="e7bf2-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="e7bf2-104">XAML Attribute Usage</span></span>  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a><span data-ttu-id="e7bf2-105">備註</span><span class="sxs-lookup"><span data-stu-id="e7bf2-105">Remarks</span></span>  
 <span data-ttu-id="e7bf2-106">`x:Shared`對應至 XAML 語言 XAML 命名空間和.NET Framework XAML 服務和其 XAML 讀取器辨識為有效的 XAML 語言項目。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-106">`x:Shared` is mapped to the XAML language XAML namespace and is recognized as a valid XAML language element by .NET Framework XAML Services and its XAML readers.</span></span> <span data-ttu-id="e7bf2-107">不過，所述的功能`x:Shared`才相關 WPF 應用程式和 WPF XAML 剖析器。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-107">However, the stated capabilities of `x:Shared` are only relevant for WPF applications and for the WPF XAML parser.</span></span> <span data-ttu-id="e7bf2-108">在 WPF 中，`x:Shared`時，只做為屬性套用至存在於 WPF 物件<xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-108">In WPF, `x:Shared` is only useful as an attribute when it is applied to an object that exists within a WPF <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="e7bf2-109">其他使用方式剖析例外狀況或其他錯誤，不擲回，但是它們沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-109">Other usages do not throw parse exceptions or other errors, but they have no effect.</span></span>  
  
 <span data-ttu-id="e7bf2-110">意義`x:Shared`XAML 語言規格中未指定。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-110">The meaning of `x:Shared` is not specified in the XAML language specification.</span></span> <span data-ttu-id="e7bf2-111">其他 XAML 實作中的，例如建置在.NET Framework XAML 服務 中，不一定會提供資源共用的支援。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-111">Other XAML implementations, such as those that build on .NET Framework XAML Services, do not necessarily provide resource-sharing support.</span></span> <span data-ttu-id="e7bf2-112">這類的 XAML 實作提供支援也可用的 framework 中的類似行為`x:Shared`值。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-112">Such XAML implementations could provide similar behavior in the supporting framework that also used `x:Shared` values.</span></span>  
  
 <span data-ttu-id="e7bf2-113">在 WPF 中，預設值`x:Shared`資源的條件是`true`。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-113">In WPF, the default `x:Shared` condition for resources is `true`.</span></span> <span data-ttu-id="e7bf2-114">這種情況表示，任何指定的資源要求一律會傳回相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-114">This condition means that any given resource request always returns the same instance.</span></span>  
  
 <span data-ttu-id="e7bf2-115">修改物件，例如傳回資源的 API，透過<xref:System.Windows.FrameworkElement.FindResource%2A>，或修改物件直接內<xref:System.Windows.ResourceDictionary>，變更原始的資源。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-115">Modifying an object that is returned through a resource API, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, or modifying an object directly within a <xref:System.Windows.ResourceDictionary>, changes the original resource.</span></span> <span data-ttu-id="e7bf2-116">如果動態資源參考該資源的參考，該資源的取用者會取得已變更的資源。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-116">If references to that resource were dynamic resource references, the consumers of that resource get the changed resource.</span></span>  
  
 <span data-ttu-id="e7bf2-117">如果資源的參考靜態資源參考，變更之後資源[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]處理時間無關。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-117">If references to the resource were static resource references, changes to the resource after [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing time are irrelevant.</span></span> <span data-ttu-id="e7bf2-118">如需靜態與動態資源參考的詳細資訊，請參閱[XAML 資源](../../../docs/framework/wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-118">For more information about static versus dynamic resource references, see [XAML Resources](../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="e7bf2-119">明確指定`x:Shared="true"`很罕見，因為已預設值。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-119">Explicitly specifying `x:Shared="true"` is rarely done, because that is already the default.</span></span> <span data-ttu-id="e7bf2-120">沒有對等的程式碼直接`x:Shared`WPF 中物件模型; 它只能指定在 XAML 使用，必須處理預設 WPF 行為或在載入路徑上的中繼 XAML 節點資料流中，如果使用.NET Framework XAML Se 處理rvices 和其 XAML 讀取器。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-120">There is no direct code equivalent for `x:Shared` in the WPF object model; it can only be specified in a XAML usage and must be processed either by the default WPF behavior or in an intermediate XAML node stream on the load path if processed using .NET Framework XAML Services and its XAML readers.</span></span>  
  
 <span data-ttu-id="e7bf2-121">案例`x:Shared="false"`是如果您定義<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>衍生類別做為資源，然後您引入的項目資源內容的模型。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-121">A scenario for `x:Shared="false"` is if you define a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class as a resource and then you introduce the element resource into a content model.</span></span> <span data-ttu-id="e7bf2-122">`x:Shared="false"`可讓在相同集合中多次推出的項目資源 (例如<xref:System.Windows.Controls.UIElementCollection>)。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-122">`x:Shared="false"` enables an element resource to be introduced multiple times in the same collection (such as a <xref:System.Windows.Controls.UIElementCollection>).</span></span> <span data-ttu-id="e7bf2-123">不含`x:Shared="false"`這是無效的因為集合會強制執行唯一性的內容。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-123">Without `x:Shared="false"` this is invalid because the collection enforces uniqueness of its contents.</span></span> <span data-ttu-id="e7bf2-124">不過，`x:Shared="false"`行為會建立另一個資源，而不是傳回相同的執行個體的相同執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-124">However, the `x:Shared="false"` behavior creates another identical instance of the resource instead of returning the same instance.</span></span>  
  
 <span data-ttu-id="e7bf2-125">另一個案例`x:Shared="false"`是如果您使用<xref:System.Windows.Freezable>動畫值，但想来修改每個動畫基礎資源的資源。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-125">Another scenario for `x:Shared="false"` is if you use a <xref:System.Windows.Freezable> resource for animation values but want to modify the resource on a per animation basis.</span></span>  
  
 <span data-ttu-id="e7bf2-126">字串處理`false`不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-126">The string handling of `false` is not case sensitive.</span></span>  
  
 <span data-ttu-id="e7bf2-127">在 WPF 中，`x:Shared`只適用於下列條件：</span><span class="sxs-lookup"><span data-stu-id="e7bf2-127">In WPF, `x:Shared` is only valid under the following conditions:</span></span>  
  
-   <span data-ttu-id="e7bf2-128"><xref:System.Windows.ResourceDictionary> ，其中包含的項目`x:Shared`必須編譯。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-128">The <xref:System.Windows.ResourceDictionary> that contains the items with `x:Shared` must be compiled.</span></span> <span data-ttu-id="e7bf2-129"><xref:System.Windows.ResourceDictionary>無法在鬆散的 XAML 或使用佈景主題。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-129">The <xref:System.Windows.ResourceDictionary> cannot be within loose XAML or used for themes.</span></span>  
  
-   <span data-ttu-id="e7bf2-130"><xref:System.Windows.ResourceDictionary>所包含的項目必須不在另一個巢狀<xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-130">The <xref:System.Windows.ResourceDictionary> that contains the items must not be nested within another <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="e7bf2-131">例如，您不能使用`x:Shared`中項目的<xref:System.Windows.ResourceDictionary>裡<xref:System.Windows.Style>已經<xref:System.Windows.ResourceDictionary>項目。</span><span class="sxs-lookup"><span data-stu-id="e7bf2-131">For example, you cannot use `x:Shared` for items in a <xref:System.Windows.ResourceDictionary> that is within a <xref:System.Windows.Style> that is already a <xref:System.Windows.ResourceDictionary> item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7bf2-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="e7bf2-132">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 [<span data-ttu-id="e7bf2-133">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="e7bf2-133">XAML Resources</span></span>](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="e7bf2-134">基底項目</span><span class="sxs-lookup"><span data-stu-id="e7bf2-134">Base Elements</span></span>](../../../docs/framework/wpf/advanced/base-elements.md)
