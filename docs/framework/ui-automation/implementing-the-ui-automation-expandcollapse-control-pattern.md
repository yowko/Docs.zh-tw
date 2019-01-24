---
title: 實作 UI 自動化 ExpandCollapse 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b4c53990969916f5c094c1a55a1383a242d884cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719751"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>實作 UI 自動化 ExpandCollapse 控制項模式
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題簡介實作 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>的方針和慣例，包括屬性、方法和事件的相關資訊。 其他參考的連結會在概觀的結尾列出。  
  
 <xref:System.Windows.Automation.ExpandCollapsePattern> 控制項模式可支援控制項以視覺化方式展開來顯示更多內容和摺疊以隱藏內容。 如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
 實作 ExpandCollapse 控制項模式時，請注意下列方針和慣例：  
  
-   彙總控制項 - 以提供 UI 展開/摺疊功能的子物件建置 — 必須支援 <xref:System.Windows.Automation.ExpandCollapsePattern> 控制項模式，而其子項目並不支援。 例如，使用清單方塊、按鈕和編輯控制項組合所建置的下拉式方塊控制項，但是它只是必須支援 <xref:System.Windows.Automation.ExpandCollapsePattern>的父下拉式方塊。  
  
    > [!NOTE]
    >  例外狀況是功能表控制項，也就是個別 MenuItem 物件的彙總。 MenuItem 物件可以支援 <xref:System.Windows.Automation.ExpandCollapsePattern> 控制項模式，但是父功能表控制項無法支援。 樹狀結構和樹狀目錄項目控制項適用類似的例外狀況。  
  
-   當控制項的 <xref:System.Windows.Automation.ExpandCollapseState> 設為 <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>時，控制項的任何 <xref:System.Windows.Automation.ExpandCollapsePattern> 功能目前非使用中，可以使用此控制項模式取得的唯一資訊是 <xref:System.Windows.Automation.ExpandCollapseState>。 如果後續新增任何子物件， <xref:System.Windows.Automation.ExpandCollapseState> 會變更且 <xref:System.Windows.Automation.ExpandCollapsePattern> 功能會啟動。  
  
-   <xref:System.Windows.Automation.ExpandCollapseState> 是指僅限直屬子物件的可見度，而非所有子系物件的可見度。  
  
-   展開和摺疊功能是控制項專屬功能。 以下是此行為的範例：  
  
    -   Office 個人功能表可以是三種狀態 MenuItem (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>、 <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> 和 <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>)，其中控制項會指定當呼叫 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 時要採用的狀態。  
  
    -   在 TreeItem 上呼叫 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 可能會顯示所有子代或只顯示直屬子系。  
  
    -   如果在控制項上呼叫 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 會維護其子代的狀態，應該會傳送可見度變更事件，如果父控制項在摺疊時不會維護其子代的狀態，則不是狀態變更事件，控制項可能會終結所有不再顯示的子代，並引發已終結事件，或者它可能會針對每個子代變更 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> 並且引發可見度變更事件。  
  
-   若要保證導覽功能，物件最好是位於 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中 (具有適當的可見度狀態)，不論其父系 <xref:System.Windows.Automation.ExpandCollapseState>為何。 如果子代是隨選產生，則它們只有在第一次顯示或可見時，才會出現在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iexpandcollapseprovider"></a>IExpandCollapseProvider 的必要成員  
 以下是實作 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>的必要屬性和方法。  
  
|必要成員|成員類型|注意|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|屬性|無|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|方法|無|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|方法|無|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Event - 事件|此控制項沒有相關聯的事件；使用這個泛型委派。|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況類型|條件|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|當 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 時會呼叫 <xref:System.Windows.Automation.ExpandCollapseState> = <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>。|  
  
## <a name="see-also"></a>另請參閱
- [UI 自動化控制項模式概觀](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [支援 UI 自動化提供者的控制項模式](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [使用 TreeWalker 導覽 UI 自動化項目](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)
- [UI 自動化樹狀目錄概觀](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [在 UI 自動化中使用快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
