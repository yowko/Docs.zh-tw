---
title: 用戶端的 UI 自動化控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 1ee0df5b133f08ec3cf6ba617c80c480e207ddf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179964"
---
# <a name="ui-automation-control-patterns-for-clients"></a><span data-ttu-id="bfd73-102">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="bfd73-102">UI Automation Control Patterns for Clients</span></span>
> [!NOTE]
> <span data-ttu-id="bfd73-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="bfd73-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bfd73-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="bfd73-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bfd73-105">本概觀介紹使用者介面自動化用戶端的控制項模式。</span><span class="sxs-lookup"><span data-stu-id="bfd73-105">This overview introduces control patterns for UI Automation clients.</span></span> <span data-ttu-id="bfd73-106">其中所包含的資訊，與使用者介面自動化用戶端使用控制項模式來存取 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]相關資訊之方式有關。</span><span class="sxs-lookup"><span data-stu-id="bfd73-106">It includes information on how a UI Automation client can use control patterns to access information about the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="bfd73-107">控制項模式提供一種方式，分類及公開與控制項類型或控制項外觀無關的控制項功能。</span><span class="sxs-lookup"><span data-stu-id="bfd73-107">Control patterns provide a way to categorize and expose a control's functionality independent of the control type or the appearance of the control.</span></span> <span data-ttu-id="bfd73-108">使用者介面自動化用戶端可檢查 <xref:System.Windows.Automation.AutomationElement> 來判斷支援哪些控制項模式，及保證控制項的行為。</span><span class="sxs-lookup"><span data-stu-id="bfd73-108">UI Automation clients can examine an <xref:System.Windows.Automation.AutomationElement> to determine which control patterns are supported and be assured of the behavior of the control.</span></span>  
  
 <span data-ttu-id="bfd73-109">如需控制項模式的完整清單，請參閱 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd73-109">For a complete list of control patterns, see [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).</span></span>  
  
<a name="uiautomation_getting_control_patterns"></a>
## <a name="getting-control-patterns"></a><span data-ttu-id="bfd73-110">取得控制項模式</span><span class="sxs-lookup"><span data-stu-id="bfd73-110">Getting Control Patterns</span></span>  
 <span data-ttu-id="bfd73-111">用戶端藉由呼叫 <xref:System.Windows.Automation.AutomationElement> 或 <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> ，從 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>擷取控制項模式。</span><span class="sxs-lookup"><span data-stu-id="bfd73-111">Clients retrieve a control pattern from an <xref:System.Windows.Automation.AutomationElement> by calling either <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> or <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="bfd73-112">用戶端可以使用 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> 方法或個別的 `IsPatternAvailable` 屬性 (例如， <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) 來判斷 <xref:System.Windows.Automation.AutomationElement>上是否支援模式或模式群組。</span><span class="sxs-lookup"><span data-stu-id="bfd73-112">Clients can use the <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> method or an individual `IsPatternAvailable` property (for example, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) to determine if a pattern or group of patterns is supported on the <xref:System.Windows.Automation.AutomationElement>.</span></span> <span data-ttu-id="bfd73-113">不過，嘗試取得控制項模式和針對 `null` 參考進行測試，比檢查支援的屬性並擷取控制項模式更有效率，因為它會造成較少的跨處理序呼叫。</span><span class="sxs-lookup"><span data-stu-id="bfd73-113">However, it is more efficient to attempt to get the control pattern and test for a `null` reference than to check the supported properties and retrieve the control pattern since it results in fewer cross-process calls.</span></span>  
  
 <span data-ttu-id="bfd73-114">下列範例示範如何從 <xref:System.Windows.Automation.TextPattern> 取得 <xref:System.Windows.Automation.AutomationElement>控制項模式。</span><span class="sxs-lookup"><span data-stu-id="bfd73-114">The following example demonstrates how to get a <xref:System.Windows.Automation.TextPattern> control pattern from an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>
## <a name="retrieving-properties-on-control-patterns"></a><span data-ttu-id="bfd73-115">在控制項模式上擷取屬性</span><span class="sxs-lookup"><span data-stu-id="bfd73-115">Retrieving Properties on Control Patterns</span></span>  
 <span data-ttu-id="bfd73-116">用戶端可藉由呼叫 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> ，並將物件轉型成傳回適當的類型，藉此在控制項模式上擷取屬性值。</span><span class="sxs-lookup"><span data-stu-id="bfd73-116">Clients can retrieve the property values on control patterns by calling either <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> or <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> and casting the object returned to an appropriate type.</span></span> <span data-ttu-id="bfd73-117">有關[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]屬性的詳細資訊，請參閱[用戶端的 UI 自動化屬性](ui-automation-properties-for-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd73-117">For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
 <span data-ttu-id="bfd73-118">除了這些方法之外`GetPropertyValue`，還可以通過通用語言運行時 （CLR） 訪問器檢索屬性值，以訪問模式上[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的屬性。</span><span class="sxs-lookup"><span data-stu-id="bfd73-118">In addition to the `GetPropertyValue` methods, property values can be retrieved through the common language runtime (CLR) accessors to access the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties on a pattern.</span></span>  
  
<a name="uiautomation_with_variable_patterns"></a>
## <a name="controls-with-variable-patterns"></a><span data-ttu-id="bfd73-119">包含變數模式的控制項</span><span class="sxs-lookup"><span data-stu-id="bfd73-119">Controls with Variable Patterns</span></span>  
 <span data-ttu-id="bfd73-120">某些控制項類型支援不同的模式，視其狀態或使用控制項的方式而定。</span><span class="sxs-lookup"><span data-stu-id="bfd73-120">Some control types support different patterns depending on their state or the manner in which the control is being used.</span></span> <span data-ttu-id="bfd73-121">可以具有可變模式的控制項示例包括清單視圖（縮略圖、磁貼、圖示、清單、詳細資訊）、Microsoft Excel 圖表（圓形圖、線圖、橫條圖、帶公式的儲存格值）、Microsoft Word 的文檔區域（普通、Web 佈局、大綱、列印佈局、列印預覽），和微軟 Windows 媒體播放機外觀。</span><span class="sxs-lookup"><span data-stu-id="bfd73-121">Examples of controls that can have variable patterns are list views (thumbnails, tiles, icons, list, details), Microsoft Excel Charts (Pie, Line, Bar, Cell Value with a formula), Microsoft Word's document area (Normal, Web Layout, Outline, Print Layout, Print Preview), and Microsoft Windows Media Player skins.</span></span>  
  
 <span data-ttu-id="bfd73-122">實作自訂控制項類型的控制項可以有任何控制項模式組合，它們是代表其功能所需的組合。</span><span class="sxs-lookup"><span data-stu-id="bfd73-122">Controls implementing custom control types can have any set of control patterns that are needed to represent their functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd73-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfd73-123">See also</span></span>

- [<span data-ttu-id="bfd73-124">使用者介面自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="bfd73-124">UI Automation Control Patterns</span></span>](ui-automation-control-patterns.md)
- [<span data-ttu-id="bfd73-125">UI 自動化的文字模式</span><span class="sxs-lookup"><span data-stu-id="bfd73-125">UI Automation Text Pattern</span></span>](ui-automation-text-pattern.md)
- [<span data-ttu-id="bfd73-126">使用 UI 自動化叫用控制項</span><span class="sxs-lookup"><span data-stu-id="bfd73-126">Invoke a Control Using UI Automation</span></span>](invoke-a-control-using-ui-automation.md)
- [<span data-ttu-id="bfd73-127">使用 UI 自動化取得核取方塊的切換狀態</span><span class="sxs-lookup"><span data-stu-id="bfd73-127">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="bfd73-128">UI 自動化用戶端的控制項模式對應</span><span class="sxs-lookup"><span data-stu-id="bfd73-128">Control Pattern Mapping for UI Automation Clients</span></span>](control-pattern-mapping-for-ui-automation-clients.md)
- [<span data-ttu-id="bfd73-129">文字模式插入文本示例</span><span class="sxs-lookup"><span data-stu-id="bfd73-129">TextPattern Insert Text Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [<span data-ttu-id="bfd73-130">文字模式搜索和選擇示例</span><span class="sxs-lookup"><span data-stu-id="bfd73-130">TextPattern Search and Selection Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [<span data-ttu-id="bfd73-131">調用模式、展開折疊模式和切換模式示例</span><span class="sxs-lookup"><span data-stu-id="bfd73-131">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
