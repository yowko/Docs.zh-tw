---
title: 實作 UI 自動化 Invoke 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: f6afb850b16493bab79dd368ba1ff126305f96aa
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077638"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>實作 UI 自動化 Invoke 控制項模式
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題將介紹實作 <xref:System.Windows.Automation.Provider.IInvokeProvider>的方針和慣例，包括事件和屬性的相關資訊。 其他參考的連結列於此主題的結尾部分。  
  
 <xref:System.Windows.Automation.InvokePattern> 控制項模式用來支援控制項，且這些控制項在啟動時並不會維護狀態，而是會啟始或執行明確的單一動作。 維護狀態的控制項，例如核取方塊和選項按鈕，必須分別實作 <xref:System.Windows.Automation.Provider.IToggleProvider> 及 <xref:System.Windows.Automation.Provider.ISelectionItemProvider> 。 如需實作叫用控制項模式的控制項，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
 實作叫用控制項模式時，請注意下列方針和慣例：  
  
-   如果未透過另一個控制項模式提供者來公開相同的行為，則控制項會實作 <xref:System.Windows.Automation.Provider.IInvokeProvider> 。 例如，如果控制項的 <xref:System.Windows.Automation.InvokePattern.Invoke%2A> 方法所執行的動作與 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 方法相同，該控制項就不應實作 <xref:System.Windows.Automation.Provider.IInvokeProvider>。  
  
-   通常按一下、按兩下或按 ENTER、使用預先定義的鍵盤快速鍵，或其他按鈕組合，就可以叫用控制項。  
  
-   已啟動的控制項上會引發<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> (以回應執行相關動作的控制項)。 在可能的情況下，應該是在控制項完成該動作並返回，且沒有發生封鎖時才會引發該事件。 在下列情節中，叫用事件應該在服務叫用要求之前引發：  
  
    -   無法或不適合等待至動作完成。  
  
    -   動作需要使用者互動。  
  
    -   動作費時，且會導致發出呼叫的用戶端長時間凍結。  
  
-   如果叫用控制項會有嚴重的副作用，就必須透過 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> 屬性公開這些副作用。 例如，雖然 <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> 和選取範圍沒有關聯，但 <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> 卻可能會造成其他控制項受到選取。  
  
-   停留 (滑鼠在上) 效果通常不會形成叫用事件。 但是，根據停留狀態而執行動作 (相對於產生視覺效果) 的控制項，應該要支援 <xref:System.Windows.Automation.InvokePattern> 控制項模式。  
  
> [!NOTE]
>  如果控制項的叫用是與滑鼠相關的副作用所造成的，便會將這個實作視為協助工具問題。  
  
-   叫用控制項和選擇項目不同。 但是，依據控制項而定，叫用某些控制項可能會有造成此項目受到選取的副作用。 例如，叫用 [我的文件] 資料夾中的 [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] 文件清單項目時，便會選取這個項目並開啟文件。  
  
-   叫用某個項目時，此項目可能會立即從 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中消失。 要求事件回呼所提供的項目資訊，可能會因此而失敗。 建議的解決方法是預先擷取快取的資訊。  
  
-   控制項可以實作多個控制項模式。 例如， [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] 工具列上的 [填滿色彩] 控制項會實作 <xref:System.Windows.Automation.InvokePattern> 及 <xref:System.Windows.Automation.ExpandCollapsePattern> 控制項模式。 <xref:System.Windows.Automation.ExpandCollapsePattern> 會公開功能表，而 <xref:System.Windows.Automation.InvokePattern> 則會以選擇的色彩填滿作用中的選取範圍。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iinvokeprovider"></a>IInvokeProvider 的必要成員  
 以下是實作 <xref:System.Windows.Automation.Provider.IInvokeProvider>的必要屬性和方法。  
  
|必要成員|成員類型|注意|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|方法|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> 為非同步呼叫，且必須立即返回，不可封鎖。<br /><br /> 對於叫用時直接或間接啟動強制回應對話方塊的控制項，此行為尤其重要。 任何引發事件的使用者介面自動化用戶端都會維持封鎖的狀態，直到強制回應對話方塊關閉為止。|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況類型|條件|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|如果未啟用此控制項。|  
  
## <a name="see-also"></a>另請參閱  
 [UI 自動化控制項模式概觀](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [支援 UI 自動化提供者的控制項模式](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [使用 UI 自動化叫用控制項](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [UI 自動化樹狀目錄概觀](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [在 UI 自動化中使用快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
