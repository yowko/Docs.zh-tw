---
title: 用戶端的 UI 自動化事件
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: d7105e9211c35e7d6125c3017e8b4b829a25b128
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179911"
---
# <a name="ui-automation-events-for-clients"></a>用戶端的 UI 自動化事件
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題描述使用者介面自動化用戶端如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 事件。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 允許用戶端訂閱感興趣的事件。 這項功能會提高效能，因為不必持續輪詢系統中的所有 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目，以查看是否有任何資訊、結構或狀態變更。  
  
 同時也因為能夠只接聽定義範圍內的事件，而改善效率。 例如，用戶端可以接聽樹狀結構中所有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目的焦點變更事件，或是只接聽一個項目和其下階的焦點變更事件。  
  
> [!NOTE]
> 請勿假設所有可能的事件都由 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 提供者引發。 例如，並非所有屬性更改都會導致 Windows 表單和 Win32 控制項的標準代理提供程式引發事件。  
  
 有關[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]事件的更廣泛視圖，請參閱[UI 自動化事件概述](ui-automation-events-overview.md)。  
  
<a name="Subscribing_to_Events"></a>
## <a name="subscribing-to-events"></a>訂閱事件  
 用戶端應用程式藉由使用下列方法之一註冊事件處理常式，來訂閱特定種類的事件。  
  
|方法|事件類型|事件引數類型|委派類型|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|焦點變更|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|屬性變更|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|結構變更|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|所有其他事件，由 <xref:System.Windows.Automation.AutomationEvent> 所識別|<xref:System.Windows.Automation.AutomationEventArgs> 或 <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 在呼叫方法之前，您必須建立委派方法來處理事件。 您想要的話也可以在單一方法中處理不同類型的事件，並在對資料中其一個方法的多次呼叫裡傳遞此方法。 例如，可以設定單一 <xref:System.Windows.Automation.AutomationEventHandler>，根據 <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> 以不同的方式來處理各種事件。  
  
> [!NOTE]
> 若要處理視窗關閉事件，將傳遞給事件處理常式的引數類型轉型為 <xref:System.Windows.Automation.WindowClosedEventArgs>。 由於視窗的 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 項目已不再有效，您不能使用 `sender` 參數來擷取資訊，請改用 <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A>。  
  
> [!CAUTION]
> 如果您的應用程式可能會接收來自本身的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 事件，請勿使用您應用程式的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 執行緒來訂閱或取消訂閱事件。 這樣可能會導致無法預期的行為。 如需詳細資訊，請參閱 [UI Automation Threading Issues](ui-automation-threading-issues.md)。  
  
 關閉時或當應用程式不再對 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件感興趣時，使用者介面自動化用戶端應該呼叫下列方法之一。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|移除註冊使用 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> 註冊的事件處理常式。|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|移除註冊使用 <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A> 註冊的事件處理常式。|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|移除註冊使用 <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> 註冊的事件處理常式。|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|移除註冊所有已註冊的事件處理常式。|  
  
 例如，請參閱訂閱[UI 自動化事件](subscribe-to-ui-automation-events.md)。  
  
## <a name="see-also"></a>另請參閱

- [訂閱 UI 自動化事件](subscribe-to-ui-automation-events.md)
- [UI 自動化事件概觀](ui-automation-events-overview.md)
- [UI 自動化屬性概觀](ui-automation-properties-overview.md)
- [跟蹤焦點示例](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
