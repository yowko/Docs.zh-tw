---
title: 實作 UI 自動化 Transform 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: f561f67aed1d024a73d78da26e86110e4cddab2f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932013"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a><span data-ttu-id="c468f-102">實作 UI 自動化 Transform 控制項模式</span><span class="sxs-lookup"><span data-stu-id="c468f-102">Implementing the UI Automation Transform Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="c468f-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="c468f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c468f-104">如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。</span><span class="sxs-lookup"><span data-stu-id="c468f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="c468f-105">本主題簡介實作 <xref:System.Windows.Automation.Provider.ITransformProvider>的方針和慣例，包括屬性、方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c468f-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="c468f-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="c468f-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="c468f-107"><xref:System.Windows.Automation.TransformPattern> 控制項模式用來支援可在二維空間內移動、調整大小或旋轉的控制項。</span><span class="sxs-lookup"><span data-stu-id="c468f-107">The <xref:System.Windows.Automation.TransformPattern> control pattern is used to support controls that can be moved, resized, or rotated within a two-dimensional space.</span></span> <span data-ttu-id="c468f-108">如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="c468f-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="c468f-109">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="c468f-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="c468f-110">實作轉換控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="c468f-110">When implementing the Transform control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="c468f-111">此控制項模式的支援不限於桌面上的物件。</span><span class="sxs-lookup"><span data-stu-id="c468f-111">Support for this control pattern is not limited to objects on the desktop.</span></span> <span data-ttu-id="c468f-112">若容器物件的子項可以自由在容器的範圍內移動、調整大小或旋轉，則這些子項也必須支援此控制項模式。</span><span class="sxs-lookup"><span data-stu-id="c468f-112">This control pattern must also be supported by the children of a container object if the children can be moved, resized, or rotated freely within the boundaries of the container.</span></span>  
  
- <span data-ttu-id="c468f-113">如果物件最後在螢幕上的位置完全在其容器的座標以外，而鍵盤或滑鼠存取不到的話，就無法移動、調整大小或旋轉物件 (例如，最上層的視窗移離螢幕，或是子物件移到容器檢視區範圍以外的地方)。</span><span class="sxs-lookup"><span data-stu-id="c468f-113">An object cannot be moved, resized, or rotated such that its resulting screen location would be completely outside the coordinates of its container and therefore inaccessible to the keyboard or mouse (for example, when a top-level window is moved off-screen or a child object is moved outside the boundaries of the container's viewport).</span></span> <span data-ttu-id="c468f-114">在這種情況下，物件會放置到最接近所要求螢幕座標的地方，其上方或左方座標會覆寫成容器範圍內的座標。</span><span class="sxs-lookup"><span data-stu-id="c468f-114">In these cases, the object is placed as close to the requested screen coordinates as possible with the top or left coordinates overridden to be within the container boundaries.</span></span>  
  
- <span data-ttu-id="c468f-115">針對多監視器系統，若物件移動、調整大小或旋轉後的位置完全超出合併桌面螢幕座標的範圍，物件就會移至主要監視器上最接近所要求座標的位置。</span><span class="sxs-lookup"><span data-stu-id="c468f-115">For multi-monitor systems, if an object is moved, resized, or rotated completely outside the combined desktop screen coordinates, the object is placed on the primary monitor as close to the requested coordinates as possible.</span></span>  
  
- <span data-ttu-id="c468f-116">所有參數和屬性值都是絕對值，不受地區設定影響。</span><span class="sxs-lookup"><span data-stu-id="c468f-116">All parameters and property values are absolute and independent of locale.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a><span data-ttu-id="c468f-117">ITransformProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="c468f-117">Required Members for ITransformProvider</span></span>  
 <span data-ttu-id="c468f-118">以下是實作 <xref:System.Windows.Automation.Provider.ITransformProvider>的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="c468f-118">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>.</span></span>  
  
|<span data-ttu-id="c468f-119">必要成員</span><span class="sxs-lookup"><span data-stu-id="c468f-119">Required members</span></span>|<span data-ttu-id="c468f-120">成員類型</span><span class="sxs-lookup"><span data-stu-id="c468f-120">Member type</span></span>|<span data-ttu-id="c468f-121">注意</span><span class="sxs-lookup"><span data-stu-id="c468f-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|<span data-ttu-id="c468f-122">屬性</span><span class="sxs-lookup"><span data-stu-id="c468f-122">Property</span></span>|<span data-ttu-id="c468f-123">None</span><span class="sxs-lookup"><span data-stu-id="c468f-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|<span data-ttu-id="c468f-124">屬性</span><span class="sxs-lookup"><span data-stu-id="c468f-124">Property</span></span>|<span data-ttu-id="c468f-125">無</span><span class="sxs-lookup"><span data-stu-id="c468f-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|<span data-ttu-id="c468f-126">屬性</span><span class="sxs-lookup"><span data-stu-id="c468f-126">Property</span></span>|<span data-ttu-id="c468f-127">無</span><span class="sxs-lookup"><span data-stu-id="c468f-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|<span data-ttu-id="c468f-128">方法</span><span class="sxs-lookup"><span data-stu-id="c468f-128">Method</span></span>|<span data-ttu-id="c468f-129">無</span><span class="sxs-lookup"><span data-stu-id="c468f-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|<span data-ttu-id="c468f-130">方法</span><span class="sxs-lookup"><span data-stu-id="c468f-130">Method</span></span>|<span data-ttu-id="c468f-131">None</span><span class="sxs-lookup"><span data-stu-id="c468f-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|<span data-ttu-id="c468f-132">方法</span><span class="sxs-lookup"><span data-stu-id="c468f-132">Method</span></span>|<span data-ttu-id="c468f-133">None</span><span class="sxs-lookup"><span data-stu-id="c468f-133">None</span></span>|  
  
 <span data-ttu-id="c468f-134">此控制項模式沒有任何相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="c468f-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="c468f-135">例外狀況</span><span class="sxs-lookup"><span data-stu-id="c468f-135">Exceptions</span></span>  
 <span data-ttu-id="c468f-136">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c468f-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="c468f-137">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="c468f-137">Exception Type</span></span>|<span data-ttu-id="c468f-138">條件</span><span class="sxs-lookup"><span data-stu-id="c468f-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> <span data-ttu-id="c468f-139">-如果<xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty>為 false。</span><span class="sxs-lookup"><span data-stu-id="c468f-139">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> <span data-ttu-id="c468f-140">-如果<xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty>為 false。</span><span class="sxs-lookup"><span data-stu-id="c468f-140">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> <span data-ttu-id="c468f-141">-如果<xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty>為 false。</span><span class="sxs-lookup"><span data-stu-id="c468f-141">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> is false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c468f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c468f-142">See also</span></span>

- [<span data-ttu-id="c468f-143">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="c468f-143">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="c468f-144">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="c468f-144">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="c468f-145">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="c468f-145">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="c468f-146">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="c468f-146">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="c468f-147">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="c468f-147">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
