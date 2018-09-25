---
title: UI 自動化屬性概觀
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 3707196cf833577e65dbd1879f2762ec4336abc2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073511"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="726aa-102">UI 自動化屬性概觀</span><span class="sxs-lookup"><span data-stu-id="726aa-102">UI Automation Properties Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="726aa-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="726aa-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="726aa-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="726aa-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="726aa-105">使用者介面自動化提供者會公開 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 項目上的屬性。</span><span class="sxs-lookup"><span data-stu-id="726aa-105">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="726aa-106">這些屬性可讓使用者介面自動化用戶端應用程式找到 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)](特別是控制項) 的資訊，包括靜態和動態資料。</span><span class="sxs-lookup"><span data-stu-id="726aa-106">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="726aa-107">本節提供 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 屬性的概觀說明。</span><span class="sxs-lookup"><span data-stu-id="726aa-107">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="726aa-108">下列各主題提供更詳細的資訊：</span><span class="sxs-lookup"><span data-stu-id="726aa-108">More specific information is given in the following topics:</span></span>  
  
-   [<span data-ttu-id="726aa-109">用戶端的 UI 自動化屬性</span><span class="sxs-lookup"><span data-stu-id="726aa-109">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
  
-   [<span data-ttu-id="726aa-110">伺服器端 UI 自動化提供者實作</span><span class="sxs-lookup"><span data-stu-id="726aa-110">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>   
## <a name="property-identifiers"></a><span data-ttu-id="726aa-111">屬性識別項</span><span class="sxs-lookup"><span data-stu-id="726aa-111">Property Identifiers</span></span>  
 <span data-ttu-id="726aa-112">每一個屬性都是由一個編號及名稱所識別。</span><span class="sxs-lookup"><span data-stu-id="726aa-112">Every property is identified by a number and a name.</span></span> <span data-ttu-id="726aa-113">屬性名稱僅用於偵錯及診斷作業。</span><span class="sxs-lookup"><span data-stu-id="726aa-113">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="726aa-114">提供者使用數值 [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] 來識別傳入的屬性要求。</span><span class="sxs-lookup"><span data-stu-id="726aa-114">Providers use the numeric [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] to identify incoming property requests.</span></span> <span data-ttu-id="726aa-115">但是，用戶端應用程式只使用 <xref:System.Windows.Automation.AutomationProperty>(會封裝編號及名稱) 以識別它們要擷取的屬性。</span><span class="sxs-lookup"><span data-stu-id="726aa-115">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="726aa-116"><xref:System.Windows.Automation.AutomationProperty> 物件代表特定屬性，其在許多類別中可做為欄位使用。</span><span class="sxs-lookup"><span data-stu-id="726aa-116"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="726aa-117">基於安全性考量，使用者介面自動化提供者會從 Uiautomationtypes.dll 內含的不同類別集之中取得這些物件。</span><span class="sxs-lookup"><span data-stu-id="726aa-117">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="726aa-118">下表按照內含 <xref:System.Windows.Automation.AutomationProperty>[!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="726aa-118">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>[!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)].</span></span>  
  
|<span data-ttu-id="726aa-119">屬性的種類</span><span class="sxs-lookup"><span data-stu-id="726aa-119">Kinds of properties</span></span>|<span data-ttu-id="726aa-120">用戶端取得 ID 的來源</span><span class="sxs-lookup"><span data-stu-id="726aa-120">Clients get IDs from</span></span>|<span data-ttu-id="726aa-121">提供者取得 ID 的來源</span><span class="sxs-lookup"><span data-stu-id="726aa-121">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="726aa-122">所有項目的通用屬性 (請參閱下表)</span><span class="sxs-lookup"><span data-stu-id="726aa-122">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="726aa-123">視窗的停駐位置</span><span class="sxs-lookup"><span data-stu-id="726aa-123">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="726aa-124">可展開和摺疊的項目狀態</span><span class="sxs-lookup"><span data-stu-id="726aa-124">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="726aa-125">格線中的項目屬性</span><span class="sxs-lookup"><span data-stu-id="726aa-125">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="726aa-126">格線屬性</span><span class="sxs-lookup"><span data-stu-id="726aa-126">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="726aa-127">具有多個檢視的項目之目前及支援的檢視</span><span class="sxs-lookup"><span data-stu-id="726aa-127">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="726aa-128">在某個範圍值上移動之項目 (例如滑桿) 的屬性</span><span class="sxs-lookup"><span data-stu-id="726aa-128">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="726aa-129">捲動視窗的屬性</span><span class="sxs-lookup"><span data-stu-id="726aa-129">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="726aa-130">可選擇項目 (例如清單中的項目) 的狀態與容器</span><span class="sxs-lookup"><span data-stu-id="726aa-130">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="726aa-131">內含選取項目之控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="726aa-131">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="726aa-132">表格中項目的資料行與資料列標頭</span><span class="sxs-lookup"><span data-stu-id="726aa-132">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="726aa-133">表格的方向和資料行與資料列標頭</span><span class="sxs-lookup"><span data-stu-id="726aa-133">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="726aa-134">切換控制項的狀態</span><span class="sxs-lookup"><span data-stu-id="726aa-134">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="726aa-135">可移動、旋轉或重新調整大小之項目的功能</span><span class="sxs-lookup"><span data-stu-id="726aa-135">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="726aa-136">具有值之項目的值以及讀取/寫入功能</span><span class="sxs-lookup"><span data-stu-id="726aa-136">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="726aa-137">視窗的功能與狀態</span><span class="sxs-lookup"><span data-stu-id="726aa-137">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>   
## <a name="properties-by-category"></a><span data-ttu-id="726aa-138">按類別分類屬性</span><span class="sxs-lookup"><span data-stu-id="726aa-138">Properties by Category</span></span>  
 <span data-ttu-id="726aa-139">下表針對可在 [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] 和 <xref:System.Windows.Automation.AutomationElement> 中找到其 <xref:System.Windows.Automation.AutomationElementIdentifiers>的屬性進行分類。</span><span class="sxs-lookup"><span data-stu-id="726aa-139">The following tables categorize the properties whose [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="726aa-140">所有控制項都有這些屬性。</span><span class="sxs-lookup"><span data-stu-id="726aa-140">These properties are common to all controls.</span></span> <span data-ttu-id="726aa-141">大部分動態屬性都與控制項模式相關，除了少數幾個在提供者應用程式的存留期可能是靜態的。</span><span class="sxs-lookup"><span data-stu-id="726aa-141">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="726aa-142">[屬性存取]  資料行中，除了 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> 及 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>以外，還列出每個屬性的任何其他存取子。</span><span class="sxs-lookup"><span data-stu-id="726aa-142">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="726aa-143">如需取得用戶端應用程式屬性的詳細資訊，請參閱 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="726aa-143">For more information on getting properties in a client application, see [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="726aa-144">如需每一個屬性的特定資訊，請按一下 [屬性存取]  資料行中的連結。</span><span class="sxs-lookup"><span data-stu-id="726aa-144">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="726aa-145">顯示特性</span><span class="sxs-lookup"><span data-stu-id="726aa-145">Display Characteristics</span></span>  
  
|<span data-ttu-id="726aa-146">屬性識別項</span><span class="sxs-lookup"><span data-stu-id="726aa-146">Property identifier</span></span>|<span data-ttu-id="726aa-147">屬性存取</span><span class="sxs-lookup"><span data-stu-id="726aa-147">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="726aa-148">N/A</span><span class="sxs-lookup"><span data-stu-id="726aa-148">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="726aa-149">項目類型</span><span class="sxs-lookup"><span data-stu-id="726aa-149">Element Type</span></span>  
  
|<span data-ttu-id="726aa-150">屬性識別項</span><span class="sxs-lookup"><span data-stu-id="726aa-150">Property identifier</span></span>|<span data-ttu-id="726aa-151">屬性存取</span><span class="sxs-lookup"><span data-stu-id="726aa-151">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="726aa-152">識別</span><span class="sxs-lookup"><span data-stu-id="726aa-152">Identification</span></span>  
  
|<span data-ttu-id="726aa-153">屬性識別項</span><span class="sxs-lookup"><span data-stu-id="726aa-153">Property identifier</span></span>|<span data-ttu-id="726aa-154">屬性存取</span><span class="sxs-lookup"><span data-stu-id="726aa-154">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="726aa-155">互動</span><span class="sxs-lookup"><span data-stu-id="726aa-155">Interaction</span></span>  
  
|<span data-ttu-id="726aa-156">屬性識別項</span><span class="sxs-lookup"><span data-stu-id="726aa-156">Property identifier</span></span>|<span data-ttu-id="726aa-157">屬性存取</span><span class="sxs-lookup"><span data-stu-id="726aa-157">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="726aa-158">模式支援</span><span class="sxs-lookup"><span data-stu-id="726aa-158">Support for Patterns</span></span>  
  
|<span data-ttu-id="726aa-159">屬性識別項</span><span class="sxs-lookup"><span data-stu-id="726aa-159">Property identifier</span></span>|<span data-ttu-id="726aa-160">屬性存取</span><span class="sxs-lookup"><span data-stu-id="726aa-160">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a><span data-ttu-id="726aa-161">其他</span><span class="sxs-lookup"><span data-stu-id="726aa-161">Miscellaneous</span></span>  
  
|<span data-ttu-id="726aa-162">屬性識別項</span><span class="sxs-lookup"><span data-stu-id="726aa-162">Property identifier</span></span>|<span data-ttu-id="726aa-163">屬性存取</span><span class="sxs-lookup"><span data-stu-id="726aa-163">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>   
## <a name="localization"></a><span data-ttu-id="726aa-164">當地語系化</span><span class="sxs-lookup"><span data-stu-id="726aa-164">Localization</span></span>  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="726aa-165"> 提供者應該以作業系統所使用的語言來顯示下列屬性：</span><span class="sxs-lookup"><span data-stu-id="726aa-165"> providers should present the following properties in the language of the operating system:</span></span>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>   
## <a name="properties-and-events"></a><span data-ttu-id="726aa-166">屬性和事件</span><span class="sxs-lookup"><span data-stu-id="726aa-166">Properties and Events</span></span>  
 <span data-ttu-id="726aa-167">屬性變更事件的概念是要與 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 做緊密的繫結。</span><span class="sxs-lookup"><span data-stu-id="726aa-167">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="726aa-168">如果是動態屬性，用戶端應用程式需要一個知道屬性值已變更的方法，以更新快取的資訊或根據新資料做出回應。</span><span class="sxs-lookup"><span data-stu-id="726aa-168">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="726aa-169">當 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 變更時，提供者會引發事件。</span><span class="sxs-lookup"><span data-stu-id="726aa-169">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="726aa-170">例如，如果選取或清除核取方塊，提供者的切換模式實作就會引發屬性變更事件。</span><span class="sxs-lookup"><span data-stu-id="726aa-170">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="726aa-171">提供者可以視任何用戶端是否正在接聽事件或接聽特定事件，以選擇性地引發事件。</span><span class="sxs-lookup"><span data-stu-id="726aa-171">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="726aa-172">並非所有屬性變更都會引發事件，這完全由項目的使用者介面自動化提供者實作所決定。</span><span class="sxs-lookup"><span data-stu-id="726aa-172">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="726aa-173">例如，當 <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> 變更時，清單方塊的標準 Proxy 提供者就不會引發事件。</span><span class="sxs-lookup"><span data-stu-id="726aa-173">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="726aa-174">此時，應用程式就必須接聽 <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>。</span><span class="sxs-lookup"><span data-stu-id="726aa-174">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="726aa-175">用戶端可以透過訂閱事件的方式以接聽事件。</span><span class="sxs-lookup"><span data-stu-id="726aa-175">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="726aa-176">訂閱事件就是建立可處理事件的委派方法，然後將方法以及會和這些方法一起處理的特定事件一起傳送至 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="726aa-176">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="726aa-177">特別是針對屬性變更事件，用戶端必須實作 <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="726aa-177">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="726aa-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="726aa-178">See Also</span></span>  
 [<span data-ttu-id="726aa-179">UI 自動化用戶端中的快取</span><span class="sxs-lookup"><span data-stu-id="726aa-179">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)  
 [<span data-ttu-id="726aa-180">用戶端的 UI 自動化屬性</span><span class="sxs-lookup"><span data-stu-id="726aa-180">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [<span data-ttu-id="726aa-181">伺服器端 UI 自動化提供者實作</span><span class="sxs-lookup"><span data-stu-id="726aa-181">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [<span data-ttu-id="726aa-182">根據屬性條件尋找 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="726aa-182">Find a UI Automation Element Based on a Property Condition</span></span>](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)  
 [<span data-ttu-id="726aa-183">從 UI 自動化提供者傳回屬性</span><span class="sxs-lookup"><span data-stu-id="726aa-183">Return Properties from a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)  
 [<span data-ttu-id="726aa-184">UI 自動化提供者引發事件</span><span class="sxs-lookup"><span data-stu-id="726aa-184">Raise Events from a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
