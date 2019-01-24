---
title: UI 自動化用戶端中的快取
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 4571af701ea28c3b7dbecbb1b1a82e7093c2831e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646457"
---
# <a name="caching-in-ui-automation-clients"></a>UI 自動化用戶端中的快取
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題將介紹 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性和控制項模式的快取。  
  
 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，快取表示預先提取資料。 該資料即可供存取，而不需進一步的跨處理序通訊。 使用者介面自動化用戶端應用程式通常會使用快取來大量擷取屬性和控制項模式。 接著，就會視需要從快取中擷取資訊。 應用程式通常會為了回應 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 中有項目已變更的事件，而定期更新快取。  
  
 快取的優點是與 Windows Presentation Foundation (WPF) 控制項和具有伺服器端 UI 自動化提供者的自訂控制項最為明顯。 在存取用戶端提供者 (如 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 控制項的預設提供者) 時，優勢較不明顯。  
  
 下列情況會發生快取：當應用程式啟動 <xref:System.Windows.Automation.CacheRequest> ，然後使用任何會傳回 <xref:System.Windows.Automation.AutomationElement>的方法或屬性時；例如 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>、 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>。 <xref:System.Windows.Automation.TreeWalker> 類別的方法例外；僅有在指定 <xref:System.Windows.Automation.CacheRequest> 為參數 (例如 <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>) 時會完成快取。  
  
 在 <xref:System.Windows.Automation.CacheRequest> 為作用中時訂閱事件，也會發生快取。 <xref:System.Windows.Automation.AutomationElement> 會以事件來源的形式傳遞給事件處理常式，其中包含快取的屬性和原始 <xref:System.Windows.Automation.CacheRequest>所指定的模式。 在您訂閱事件之後所做的任何 <xref:System.Windows.Automation.CacheRequest> 變更皆不會有任何作用。  
  
 您可以快取項目的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性和控制項模式。  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>快取選項  
 <xref:System.Windows.Automation.CacheRequest> 可指定下列快取選項。  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>要快取的屬性  
 您可呼叫每一個屬性的 <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> 之後再啟動要求，以指定要快取的屬性。  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>要快取的控制項模式  
 您可呼叫每一個模式的 <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> 之後再啟動要求，以指定要快取的控制項模式。 快取模式時，不會自動快取它的屬性；您必須使用 <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>指定您要快取的屬性。  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>快取的範圍和篩選  
 您可以設定 <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> 屬性之後再啟動要求，以指定要快取其屬性和模式的項目。 範圍與在要求處於作用中時所擷取的項目有關。 例如，如果您只設定 <xref:System.Windows.Automation.TreeScope.Children>，然後擷取 <xref:System.Windows.Automation.AutomationElement>，則會快取該項目子系的屬性和項目，而不是項目本身的屬性和項目。 若要確保進行擷取項目本身的快取，您必須在 <xref:System.Windows.Automation.TreeScope.Element> 屬性中包含 <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> 。 您無法將範圍設 <xref:System.Windows.Automation.TreeScope.Parent> 或 <xref:System.Windows.Automation.TreeScope.Ancestors>。 不過，快取子項目時即會快取父項目；請參閱本主題中的＜擷取快取的子系和父代＞。  
  
 快取的範圍也會受到 <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> 屬性的影響。 根據預設，僅會針對在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視中顯示的項目執行快取。 不過，您可以變更此屬性，將快取套用至所有項目，或是只套用至內容檢視中顯示的項目。  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>項目參考的強度  
 擷取 <xref:System.Windows.Automation.AutomationElement>時，預設為您可以存取該項目的所有屬性與模式 (包括未快取的屬性與模式)。 不過，如需更高的效率，您可以將 <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> 的 <xref:System.Windows.Automation.CacheRequest> 屬性設為 <xref:System.Windows.Automation.AutomationElementMode.None>，以指定項目參考僅參考快取的資料。 在此情況下，您就不能存取擷取項目的任何非快取屬性和模式。 這表示您無法透過 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> 的 `Current` 或 <xref:System.Windows.Automation.AutomationElement> 屬性擷取任何屬性或控制項模式；也無法使用 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> 或 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>擷取模式。 在快取模式上，您可以呼叫 <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>這類擷取陣列屬性的方法，而不是 <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>這類在控制項上執行動作的方法。  
  
 舉例來說，螢幕助讀程式是可能不需要物件完整參考的應用程式，其會預先擷取視窗中項目的 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> 和 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> 屬性，而不需 <xref:System.Windows.Automation.AutomationElement> 物件本身。  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>啟動 CacheRequest  
 僅有在目前執行緒的 <xref:System.Windows.Automation.AutomationElement> 為作用中時擷取 <xref:System.Windows.Automation.CacheRequest> 物件才會執行快取。 有兩個方法可以啟動 <xref:System.Windows.Automation.CacheRequest>。  
  
 一般方式是呼叫 <xref:System.Windows.Automation.CacheRequest.Activate%2A>。 此方法會傳回實作 <xref:System.IDisposable>的物件。 只要 <xref:System.IDisposable> 物件存在，要求就會保持作用中狀態。 若要控制物件的存留期最簡單的方式是在呼叫內`using`(C#) 或`Using`(Visual Basic) 的區塊。 這可確保該要求可從堆疊推出，即使引發例外狀況亦同。  
  
 另一種方法是呼叫 <xref:System.Windows.Automation.CacheRequest.Push%2A>，這種方法在您要將快取要求進行巢狀處理時相當有用。 這會將要求放置在堆疊上，並且啟動要求。 要求會保持作用中狀態，直到 <xref:System.Windows.Automation.CacheRequest.Pop%2A>將要求從堆疊移除為止。 如果另一個要求被推入到堆疊，要求則會暫時變成非作用中，只有堆疊最上層的要求仍然保持作用中的狀態。  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>擷取快取屬性  
 您可以透過下列方法和屬性來擷取項目的快取屬性。  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 如果要求的屬性不在快取中，會引發例外狀況。  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>就像 <xref:System.Windows.Automation.AutomationElement.Current%2A>一樣，會將個別屬性公開為結構的成員。 不過，您不需要擷取此結構，而可以直接存取個別的屬性。 例如， <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> 屬性可以取自 `element.Cached.Name`，其中 `element` 是一種 <xref:System.Windows.Automation.AutomationElement>。  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>擷取快取控制項模式  
 您可以透過下列方法來擷取項目的快取控制項模式。  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 如果模式不在快取中， <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> 會引發例外狀況，而 <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> 會傳回 `false`。  
  
 您可以使用模式物件的 `Cached` 屬性，擷取控制項模式的快取屬性。 您也可以透過 `Current` 屬性擷取目前的值，但是前提是當擷取 <xref:System.Windows.Automation.AutomationElementMode.None> 時未指定 <xref:System.Windows.Automation.AutomationElement> (預設值為<xref:System.Windows.Automation.AutomationElementMode.Full> ，可允許存取目前的值)。  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>擷取快取的子系和父代  
 當您擷取 <xref:System.Windows.Automation.AutomationElement> 並透過要求的 <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> 屬性，要求快取該項目的子系時，後續可能會從您擷取的 <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> 項目屬性取得子系項目。  
  
 如果 <xref:System.Windows.Automation.TreeScope.Element> 已包含在快取要求的範圍內，隨後即可從任何子項目的 <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> 屬性取得要求的根項目。  
  
> [!NOTE]
>  您無法快取要求之根項目的父代或祖系。  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>更新快取  
 只有在 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]保持不變的情況下，快取才會持續有效。 更新快取的工作由應用程式負責，目的通常是為了回應事件。  
  
 如果您在 <xref:System.Windows.Automation.CacheRequest> 為作用中時訂閱事件，即可取得 <xref:System.Windows.Automation.AutomationElement> ，並且在呼叫事件處理常式委派時，取得做為事件來源的更新快取。 您也可以藉由呼叫 <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>來更新項目的快取資訊。 您可以在原始 <xref:System.Windows.Automation.CacheRequest> 中傳遞，以更新之前快取過的所有資訊。  
  
 更新快取不會更改任何現有 <xref:System.Windows.Automation.AutomationElement> 參考的屬性。  
  
## <a name="see-also"></a>另請參閱
- [用戶端的 UI 自動化事件](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
- [在 UI 自動化中使用快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [FetchTimer 範例](https://msdn.microsoft.com/library/5b7d3294-de22-4f24-b2d6-d4785a304b90)
