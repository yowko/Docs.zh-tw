---
title: "使用 AutomationID 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1a0613ecc6693b12dc76b77d6a634aafa599d5ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="use-the-automationid-property"></a><span data-ttu-id="45a7c-102">使用 AutomationID 屬性</span><span class="sxs-lookup"><span data-stu-id="45a7c-102">Use the AutomationID Property</span></span>
> [!NOTE]
>  <span data-ttu-id="45a7c-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="45a7c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="45a7c-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="45a7c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="45a7c-105">本主題包含的案例和範例程式碼，說明如何及何時可以使用 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 找出 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構內的項目。</span><span class="sxs-lookup"><span data-stu-id="45a7c-105">This topic contains scenarios and sample code that show how and when the <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> can be used to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree.</span></span>  
  
 <span data-ttu-id="45a7c-106"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 可唯一識別來自其同層級的使用者介面自動化項目。</span><span class="sxs-lookup"><span data-stu-id="45a7c-106"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> uniquely identifies a UI Automation element from its siblings.</span></span> <span data-ttu-id="45a7c-107">如需與控制項識別相關之屬性識別項的詳細資訊，請參閱 [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="45a7c-107">For more information on property identifiers related to control identification, see [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45a7c-108"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 不保證整個樹狀結構的唯一身分識別；它通常需要搭配容器和範圍資訊才更加實用。</span><span class="sxs-lookup"><span data-stu-id="45a7c-108"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> does not guarantee a unique identity throughout the tree; it typically needs container and scope information to be useful.</span></span> <span data-ttu-id="45a7c-109">例如，應用程式可能包含具有多個最上層功能表項目的功能表控制項，因此也會有多個子功能表項目。</span><span class="sxs-lookup"><span data-stu-id="45a7c-109">For example, an application may contain a menu control with multiple top-level menu items that, in turn, have multiple child menu items.</span></span> <span data-ttu-id="45a7c-110">這些次要功能表項目可由 Item1、Item2 (依此類推) 之類的一般配置識別，因此最上層功能表項目的子系可以有重複識別項。</span><span class="sxs-lookup"><span data-stu-id="45a7c-110">These secondary menu items may be identified by a generic scheme such as "Item1", "Item 2", and so on, allowing duplicate identifiers for children across top-level menu items.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="45a7c-111">案例</span><span class="sxs-lookup"><span data-stu-id="45a7c-111">Scenarios</span></span>  
 <span data-ttu-id="45a7c-112">已識別三個主要的使用者介面自動化用戶端應用程式案例，其在搜尋項目時需要使用 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 才能達到正確且一致的結果。</span><span class="sxs-lookup"><span data-stu-id="45a7c-112">Three primary UI Automation client application scenarios have been identified that require the use of <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> to achieve accurate and consistent results when searching for elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45a7c-113">所有控制項檢視中的使用者介面自動化項目都支援<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> ，除了最上層的應用程式視窗、衍生自不具識別碼或 x:Uid 之 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 控制項的使用者介面自動化項目，以及和使用者介面自動化項目衍生自不具控制項識別碼之 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 控制項的使用者介面自動化項目以外。</span><span class="sxs-lookup"><span data-stu-id="45a7c-113"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> is supported by all UI Automation elements in the control view except top-level application windows, UI Automation elements derived from [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controls that do not have an ID or x:Uid, and UI Automation elements derived from [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] controls that do not have a control ID.</span></span>  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a><span data-ttu-id="45a7c-114">使用唯一且可探索的 AutomationID，在使用者介面自動化樹狀結構中找出特定項目</span><span class="sxs-lookup"><span data-stu-id="45a7c-114">Use a unique and discoverable AutomationID to locate a specific element in the UI Automation tree</span></span>  
  
-   <span data-ttu-id="45a7c-115">使用 [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] 這類工具來報告所要之 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 項目的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="45a7c-115">Use a tool such as [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] to report the <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> of a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] element of interest.</span></span> <span data-ttu-id="45a7c-116">您即可將這個值以測試指令碼形式複製及貼入用戶端應用程式，以進行後續的自動化測試。</span><span class="sxs-lookup"><span data-stu-id="45a7c-116">This value can then be copied and pasted into a client application such as a test script for subsequent automated testing.</span></span> <span data-ttu-id="45a7c-117">這種方法可減少並簡化要在執行階段中識別及尋找項目的必要程式碼。</span><span class="sxs-lookup"><span data-stu-id="45a7c-117">This approach reduces and simplifies the code necessary to identify and locate an element at runtime.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="45a7c-118">一般而言，您應該試著取得 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>的直接子系。</span><span class="sxs-lookup"><span data-stu-id="45a7c-118">In general, you should try to obtain only direct children of the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.</span></span> <span data-ttu-id="45a7c-119">如果搜尋子代可能會逐一查看數百或甚至數千個項目，就很有可能會造成堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="45a7c-119">A search for descendants may iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="45a7c-120">如果您嘗試取得較低層級的特定項目，您應該從應用程式視窗或較低層級的容器開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="45a7c-120">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a><span data-ttu-id="45a7c-121">使用持續性路徑，返回先前識別的 AutomationElement</span><span class="sxs-lookup"><span data-stu-id="45a7c-121">Use a persistent path to return to a previously identified AutomationElement</span></span>  
  
-   <span data-ttu-id="45a7c-122">用戶端應用程式 (從簡單的測試指令碼到完整的錄製和播放公用程式) 可能需要存取目前未具現化因此並不存在於使用者介面自動化樹狀結構中的項目，例如檔案開啟對話方塊或功能表項目。</span><span class="sxs-lookup"><span data-stu-id="45a7c-122">Client applications, from simple test scripts to robust record and playback utilities, may require access to elements that are not currently instantiated, such as a file open dialog or a menu item and therefore do not exist in the UI Automation tree.</span></span> <span data-ttu-id="45a7c-123">這些項目只能在重現或透過使用 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 屬性 (例如 AutomationID、控制項模式和事件接聽程式) 來「播放」特定的一連串 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 動作時，才會具現化。</span><span class="sxs-lookup"><span data-stu-id="45a7c-123">These elements can only be instantiated by reproducing, or "playing back", a specific sequence of [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] actions through the use of [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties such as AutomationID, control patterns and event listeners.</span></span> <span data-ttu-id="45a7c-124">如需使用 [TLA#tla_uiautomation](http://msdn.microsoft.com/en-us/028467fd-2980-4691-9522-0131dcef23a0) 產生以使用者與 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 互動情況為依據的測試指令碼範例，請參閱 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="45a7c-124">See [Test Script Generator Sample](http://msdn.microsoft.com/en-us/028467fd-2980-4691-9522-0131dcef23a0) for an example that uses [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to generate test scripts based on user interaction with the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a><span data-ttu-id="45a7c-125">使用相對路徑，返回先前識別的 AutomationElement</span><span class="sxs-lookup"><span data-stu-id="45a7c-125">Use a relative path to return to a previously identified AutomationElement</span></span>  
  
-   <span data-ttu-id="45a7c-126">在某些情況下，由於 AutomationID 只保證在同層級是唯一的，因此在使用者介面自動化樹狀結構中的多個項目可能有相同的 AutomationID 屬性值。</span><span class="sxs-lookup"><span data-stu-id="45a7c-126">In certain circumstances, since AutomationID is only guaranteed to be unique amongst siblings, multiple elements in the UI Automation tree may have identical AutomationID property values.</span></span> <span data-ttu-id="45a7c-127">在這些情況下，項目只能依據父代、祖系 (若有需要) 來唯一識別。</span><span class="sxs-lookup"><span data-stu-id="45a7c-127">In these situations the elements can be uniquely identified based on a parent and, if necessary, a grandparent.</span></span> <span data-ttu-id="45a7c-128">例如，開發人員可能會提供包含多個功能表項目的功能表列，且每個功能表項目具有多個子功能表項目，並以循序 AutomationID 如「項目 1」、「項目 2」等等來識別子系。</span><span class="sxs-lookup"><span data-stu-id="45a7c-128">For example, a developer may provide a menu bar with multiple menu items each with multiple child menu items where the children are identified with sequential AutomationID's such as "Item1", "Item2", and so on.</span></span> <span data-ttu-id="45a7c-129">這樣一來，每個功能表項目即可由本身的 AutomationID 搭配其父代及其祖系 (若有需要) 的 AutomationID 來唯一識別。</span><span class="sxs-lookup"><span data-stu-id="45a7c-129">Each menu item could then be uniquely identified by its AutomationID along with the AutomationID of its parent and, if necessary, its grandparent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45a7c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45a7c-130">See Also</span></span>  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>  
 [<span data-ttu-id="45a7c-131">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="45a7c-131">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="45a7c-132">尋找 UI 自動化的項目，根據屬性條件</span><span class="sxs-lookup"><span data-stu-id="45a7c-132">Find a UI Automation Element Based on a Property Condition</span></span>](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
