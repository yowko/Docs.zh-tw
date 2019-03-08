---
title: 伺服器端 UI 自動化提供者實作
ms.date: 03/30/2017
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
ms.openlocfilehash: df2c1fcd6c84b7670c53a8f06f97c2ea46b8b33d
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679407"
---
# <a name="server-side-ui-automation-provider-implementation"></a>伺服器端 UI 自動化提供者實作
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本節描述如何為自訂控制項實作伺服器端使用者介面自動化提供者。  
  
 實作中的，Windows Presentation Foundation (WPF) 項目，且非位[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]項目 (例如專為[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]) 本質上不同。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 項目透過衍生自 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的類別提供 <xref:System.Windows.Automation.Peers.AutomationPeer>的支援。 非[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 項目透過提供者介面的實作提供支援。  
  
<a name="Security_Considerations"></a>   
## <a name="security-considerations"></a>安全性考量  
 應該寫入提供者，以便他們可在部分信任環境中運作。 因為 UIAutomationClient.dll 未設定為在部分信任下執行，所以您的提供者程式碼不應該參考該組件。 如果這樣做，程式碼可在完全信任環境中執行，但無法在部分信任環境中執行。  
  
 尤其，不要使用來自 UIAutomationClient.dll 中類別的欄位，例如 <xref:System.Windows.Automation.AutomationElement>中的欄位。 請改用來自 UIAutomationTypes.dll 中類別的對等欄位，例如 <xref:System.Windows.Automation.AutomationElementIdentifiers>。  
  
<a name="Provider_Implementation_by_WPF_Elements"></a>   
## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>依 Windows Presentation Foundation 項目的提供者實作  
 如需本主題的詳細資訊，請參閱 [WPF 自訂控制項的 UI 自動化](../../../docs/framework/wpf/controls/ui-automation-of-a-wpf-custom-control.md)。  
  
<a name="Provider_Implementation_by_non_WPF_Elements"></a>   
## <a name="provider-implementation-by-non-wpf-elements"></a>依非 WPF 項目的提供者實作  
 不屬於 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 架構但以 Managed 程式碼撰寫而成的自訂控制項 (其中大多是 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] 控制項)，可藉由實作介面提供 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的支援。 每個項目必須至少實作下一節中第一個資料表列出的其中一個介面。 此外，如果項目支援一或多個控制項模式，它必須針對每個控制項模式實作適當的介面。  
  
 您的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供者專案必須參考下列組件：  
  
-   UIAutomationProviders.dll  
  
-   UIAutomationTypes.dll  
  
-   WindowsBase.dll  
  
  
<a name="Provider_Interfaces"></a>   
### <a name="provider-interfaces"></a>提供者介面  
 每個 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供者必須實作下列其中一個介面。  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|提供功能給裝載在視窗中的簡單控制項，包括支援控制項模式和屬性。|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|繼承自 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>。 為複雜控制項中的項目新增功能，包括在片段內導覽、設定焦點，以及傳回項目的週框。|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|繼承自 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>。 為複雜控制項中的根項目新增功能，包括在指定的座標尋找子項目，以及設定整個控制項的焦點狀態。|  
  
 下列介面提供新增的功能，但不需要實作。  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|可讓提供者追蹤事件的要求。|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|可讓以視窗為基礎的項目在片段的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構內重新定位。|  
  
 <xref:System.Windows.Automation.Provider> 命名空間中的其他所有介面則是用於控制項模式支援。  
  
<a name="Requirements_for_Non_WPF_Providers"></a>   
### <a name="requirements-for-non-wpf-providers"></a>非 WPF 提供者的需求  
 若要與 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]通訊，您的控制項必須實作下列主要功能領域：  
  
|功能|實作|  
|-------------------|--------------------|  
|將提供者公開至 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|在回應傳送至控制項視窗的 WM_GETOBJECT 訊息時，傳回實作 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> 的物件 (或衍生的介面)。 對於片段，這必須是片段根的提供者。|  
|提供屬性值|實作 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> 來提供或覆寫值。|  
|可讓用戶端與控制項互動|實作支援控制模式的介面，例如 <xref:System.Windows.Automation.Provider.IInvokeProvider>。 實作 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>時傳回這些模式提供者。|  
|引發事件|呼叫 <xref:System.Windows.Automation.Provider.AutomationInteropProvider> 的其中一個靜態方法，來引發用戶端可以接聽的事件。|  
|在片段內啟用導覽和聚焦功能|為片段內的每個項目實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> 。 (項目若不屬於片段，則不需要)。|  
|可讓您在片段中將焦點放在子項目和尋找子項目|實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>。 (項目若不是片段根，則不需要)。|  
  
<a name="Property_Values_in_Non_WPF_Providers"></a>   
### <a name="property-values-in-non-wpf-providers"></a>非 WPF 提供者中的屬性值  
 自訂控制項的[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供者必須支援某些屬性，而這些屬性可由自動化系統以及用戶端應用程式使用。 對於裝載於視窗 (HWND) 的項目， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 可以從預設視窗提供者擷取某些屬性，但必須從自訂提供者取得其他屬性。  
  
 以 HWND 為基礎的控制項的提供者通常不需要提供下列屬性 (以欄位值識別)：  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ProcessIdProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClassNameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.HasKeyboardFocusProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty>  
  
> [!NOTE]
>  簡單項目的 <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> 或裝載在視窗中之片段根的項目取自於視窗；不過，根之下的片段項目 (例如清單方塊中的清單項目) 必須提供自己的識別項。 如需詳細資訊，請參閱 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>。  
>   
>  應該針對 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> 控制項中裝載的提供者傳回 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] 。 在此情況下，預設視窗提供者可能無法擷取正確值。  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> 通常由主機提供者所提供。 例如，如果自訂控制項衍生自 <xref:System.Windows.Forms.Control>，則名稱衍生自控制項的 `Text` 屬性。  
  
 如需範例程式碼，請參閱 [Return Properties from a UI Automation Provider](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)。  
  
<a name="Events_in_Non_WPF_Providers"></a>   
### <a name="events-in-non-wpf-providers"></a>非 WPF 提供者中的事件  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供者應該引發事件，將 UI 狀態中的變更通知用戶端應用程式。 下列方法會用於引發事件。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|引發各種事件，包括由控制項模式觸發的事件。|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性變更後，即會引發事件。|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的結構變更後，即會引發事件，例如，移除或加入項目。|  
  
 事件的目的是通知用戶端 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]中發生某種情況，活動是否由 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 系統本身觸發。 例如，每當透過直接使用者輸入，或是藉由呼叫 <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> 的應用程式叫用控制項時，應該引發 <xref:System.Windows.Automation.InvokePattern.Invoke%2A>所識別的事件。  
  
 若要最佳化效能，提供者可以選擇性地引發事件，或如果沒有註冊任何用戶端應用程式來接收事件，則完全不引發任何事件。 下列方法會用於最佳化。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|這個靜態屬性會指定是否有任何用戶端應用程式已訂閱 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|提供者在片段根上實作此介面，可讓提供者在用戶端針對片段上的事件註冊和取消註冊事件處理常式時接到通知。|  
  
<a name="Non_WPF_Provider_Navigation"></a>   
### <a name="non-wpf-provider-navigation"></a>非 WPF 提供者導覽  
 簡單控制項 (例如裝載於視窗 (HWND) 的自訂按鈕) 的提供者不需要支援 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構內的導覽。 項目之間的導覽是由主控視窗的預設提供者處理，而預設提供者則於 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>的實作中指定。 不過，當您實作複雜自訂控制項的提供者時，您必須支援片段的根節點與子系之間的導覽，以及同層級節點之間的導覽。  
  
> [!NOTE]
>  根以外的片段項目必須從 `null` 傳回 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>參考，因為它們不會直接裝載在視窗中，而且沒有預設提供者可支援項目之間的導覽。  
  
 片段的結構取決於您的 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>實作。 對於每個片段的可能方向，此方法會傳回該方向中項目的提供者物件。 如果該方向中沒有任何項目，此方法會傳回 `null` 參考。  
  
 片段根僅支援導覽至子項目。 例如，當方向為 <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>時，清單方塊會傳回清單中的第一個項目，而當方向為 <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>時，則傳回最後一個項目。 片段根目錄不支援導覽至父代或同層級；這是由主控視窗提供者處理。  
  
 不是根的片段項目必須支援導覽至父代，以及導覽至任何同層級和其具有的子系。  
  
<a name="Non_WPF_Provider_Reparenting"></a>   
### <a name="non-wpf-provider-reparenting"></a>非 WPF 提供者重設父代  
 實際上快顯視窗是最上層視窗，因此預設為出現在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構，以做為桌面的子系。 不過，在許多情況下，快顯視窗在邏輯上是一些其他控制項的子系。 例如，下拉式方塊的下拉式清單在邏輯上是下拉式方塊的子系。 同樣地，功能表快顯視窗在邏輯上是功能表的子系。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供支援，以重設快顯視窗的父代，讓它們看起來似乎是相關聯控制項的子系。  
  
 若要重設快顯視窗的父代：  
  
1.  建立快顯視窗的提供者。 這需要預先知道快顯視窗的類別。  
  
2.  如往常般實作該快顯視窗的所有屬性和模式，好似它本身就是控制項。  
  
3.  實作 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> 屬性，好讓它傳回取自 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>的值，其中參數是快顯視窗的視窗控制代碼。  
  
4.  實作快顯視窗和其父代的 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> ，以便可以適當處理從邏輯父代到邏輯子系的導覽，以及同層級子系之間的導覽。  
  
 當 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 遇到快顯視窗時，它會辨識是否以預設值取代導覽，並在遇到快顯視窗為桌面的子系時，略過快顯視窗。 相反地，節點只能透過片段來連接。  
  
 重設父代不適合控制項可以裝載任何類別之視窗的情況。 例如，rebar 可在其群組列中裝載任何類型的 HWND。 為了處理這些情況， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支援替代形式的 HWND 重新配置，如下一節所述。  
  
<a name="Non_WPF_Provider_Repositioning"></a>   
### <a name="non-wpf-provider-repositioning"></a>非 WPF 提供者重設配置  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 片段可能包含兩個或多個項目，而每一個都包含在一個視窗 (HWND) 中。 因為每個 HWND 都有自己的預設提供者，將 HWND 視為包含 HWND 的子系，所以 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構會根據預設將 HWND 顯示在片段中，做為父視窗的子系。 在大部分情況下，這是所需的行為，但有時候，可能會造成混淆，因為它不符合 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]的邏輯結構。  
  
 rebar 控制項就是這種情況的好範例。 Rebar 包含群組列，其中每一個可以輪流包含 HWND 型控制項，例如工具列、編輯方塊或下拉式方塊。 Rebar HWND 的預設視窗提供者會將群組列控制項 HWND 視為子系，而且 rebar 提供者也會將群組列視為子系。 因為 HWND 提供者和 rebar 提供者會一起運作，並且結合其子系，所以群組列和 HWND 型控制項會顯示為 rebar 的子系。 不過，在邏輯上只有群組列應該顯示為 rebar 的子系，而且每個群組列提供者應該要與其包含之控制項的預設 HWND 提供者配合。  
  
 為了達成此目的，rebar 的片段根提供者會公開一組代表群組列的子系。 每個群組列都有可能公開屬性和模式的單一提供者。 在實作 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>時，群組列提供者會傳回控制項 HWND 的預設視窗提供者，而取得此提供者的方式為呼叫 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>，並傳入控制項的視窗控制代碼。 最後，rebar 的片段根提供者會實作 <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> 介面，以及在實作 <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> 時，它會傳回指定的 HWND 中包含之控制項的適當群組列提供者。  
  
## <a name="see-also"></a>另請參閱
- [UI 自動化提供者概觀](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [公開伺服器端 UI 自動化提供者](../../../docs/framework/ui-automation/expose-a-server-side-ui-automation-provider.md)
- [從 UI 自動化提供者傳回屬性](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)
- [UI 自動化提供者引發事件](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
- [在 UI 自動化片段提供者中啟用導覽](../../../docs/framework/ui-automation/enable-navigation-in-a-ui-automation-fragment-provider.md)
- [支援 UI 自動化提供者的控制項模式](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
