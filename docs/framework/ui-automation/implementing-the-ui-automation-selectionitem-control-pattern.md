---
title: 實作 UI 自動化 SelectionItem 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 02505224e4673592f1e169c40af1cfb098e5d9bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180107"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>實作 UI 自動化 SelectionItem 控制項模式
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題簡介實作 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>的方針和慣例，包括屬性、方法和事件的相關資訊。 其他參考的連結會在概觀的結尾列出。  
  
 <xref:System.Windows.Automation.SelectionItemPattern> 控制項模式用來支援控制項，其支援的控制項作用如同實作 <xref:System.Windows.Automation.Provider.ISelectionProvider>之容器控制項的個別可選取子項目。 有關實現選擇專案控制模式的控制項的示例，請參閱[UI 自動化用戶端的控制模式映射](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
 實作選取項目控制項模式時，請注意下列方針和慣例：  
  
- 若單一選取控制項有實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>的子控制項，例如 [顯示內容] **** 對話方塊中的 [螢幕解析度] **** 滑桿，應實作 <xref:System.Windows.Automation.Provider.ISelectionProvider> ，且其子系應實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> 和 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-iselectionitemprovider"></a>ISelectionItemProvider 的必要成員  
 實作 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>需要下列屬性、方法和事件。  
  
|必要成員|成員類型|注意|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|屬性|None|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|屬性|None|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|方法|None|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|事件|當容器中的選項大幅變更，需要傳送比 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> 常數所允許的更多 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> 和 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> 事件時，就會引發此事件。|  
  
- 如果 <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>、 <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>或 <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> 的結果是單一選取的項目，則應引發 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> ，否則應視情況傳送 <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> 。  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況型別|條件|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|當嘗試下列任一項時：<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> = <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` 。<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> = <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` 。<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> = <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` 。|  
  
## <a name="see-also"></a>另請參閱

- [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)
- [支援 UI 自動化提供者的控制項模式](support-control-patterns-in-a-ui-automation-provider.md)
- [用戶端的 UI 自動化控制項模式](ui-automation-control-patterns-for-clients.md)
- [實作 UI 自動化 Selection 控制項模式](implementing-the-ui-automation-selection-control-pattern.md)
- [UI Automation Tree Overview](ui-automation-tree-overview.md)
- [使用 UI 自動化中的快取](use-caching-in-ui-automation.md)
- [片段提供程式示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
