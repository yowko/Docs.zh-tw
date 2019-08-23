---
title: UI 自動化和 Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 8aadcc213e92fd53490f639f37dc8d8f62762c2c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946474"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>UI 自動化和 Microsoft Active Accessibility
> [!NOTE]
> 這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。  
  
 Microsoft Active Accessibility 是過去用來讓應用程式成為可存取的方法。 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 是 [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] 的新式協助工具模型，能滿足輔助科技產品及自動化測試工具的需求。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]提供了許多優於 Active Accessibility 的改良功能。  
  
 本主題包含的主要功能[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , 並說明這些功能與 Active Accessibility 有何不同。  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>程式語言：  
< Active Accessibility 是以具有雙重介面支援的元件物件模型 (COM) 為基礎, 因此可在 C/C++、 [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]和指令碼語言中進行程式化。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](包括適用于標準控制項的用戶端提供者程式庫) 是以 managed 程式碼撰寫, 而且使用者介面自動化用戶端應用C#程式最容易使用或 Visual Basic .net 來設計。 使用 Managed 程式碼或 C/C++ 皆可撰寫使用者介面自動化提供者，亦即介面實作。  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Windows Presentation Foundation 的支援  
 Windows Presentation Foundation (WPF) 是建立使用者介面的新模型。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]元素不包含 Active Accessibility 的原生支援;不過, 它們支援[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], 其中包括 Active Accessibility 用戶端的橋接支援。 只有特別為 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 撰寫的用戶端可完整利用 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]協助工具的功能，例如豐富的文字支援。  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>伺服器和用戶端  
 在 Active Accessibility 中, 伺服器和用戶端會透過伺服器的執行`IAccessible`, 而直接進行通訊。  
  
 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，則有核心服務介於伺服器 (稱為提供者) 與用戶端之間。 此核心服務會呼叫提供者所實作的介面，並提供額外服務，例如為項目產生唯一的執行階段識別碼。 用戶端應用程式會使用程式庫函式呼叫 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 服務。  
  
 使用者介面自動化提供者可以提供資訊給 Active Accessibility 的用戶端, Active Accessibility 伺服器則可以提供資訊給使用者介面自動化用戶端應用程式。 不過, 因為 Active Accessibility 不會公開所需的資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], 所以這兩個模型並不完全相容。  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>UI 項目  
 Active Accessibility 會[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] `IAccessible`以介面或子識別碼的形式呈現元素。 因此我們很難藉由比較兩者的 `IAccessible` 指標，來判斷它們是否參考同一個項目。  
  
 但在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，每個項目都會顯示為 <xref:System.Windows.Automation.AutomationElement> 物件， 所以只要使用等號比較運算子或 <xref:System.Windows.Automation.AutomationElement.Equals%2A> 方法就能進行比較。這兩個方法都會比較項目的唯一執行階段識別碼。  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>樹狀檢視和導覽  
 畫面上的 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 項目可視為以桌面為根、應用程式視窗為下層子項目、應用程式內項目為後續子系的樹狀結構。  
  
 在 Active Accessibility 中, 許多與使用者無關的自動化元素會在樹狀結構中公開。 用戶端應用程式必須先全盤查看，才能判斷出重要的項目。  
  
 使用者介面自動化用戶端應用程式則透過篩選過的檢視來查看 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 。 此檢視只包含所需項目，也就是可提供資訊給使用者或可互動的項目。 使用者可查看只包含控制項目和只包含內容項目的預先定義檢視；此外，應用程式可以定義自訂檢視。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 簡化了向使用者描述 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 及協助使用者與應用程式互動的工作。  
  
 在 Active Accessibility 中的專案之間導覽是空間 (例如, 移至位於畫面左側的元素)、邏輯 (例如移至下一個功能表項目, 或在對話方塊內的定位順序中的下一個專案) 或階層式 (例如, 將容器中的第一個子系或從子系移至其父系)。 階層式導覽相當複雜，因為事實上子項目不一定是實作 `IAccessible`的物件。  
  
 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，所有 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目都是支援相同基本功能的 <xref:System.Windows.Automation.AutomationElement> 。 (從提供者角度來看，這些是實作繼承自 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> 之介面的物件。)導覽主要為階層式：從父系到子系，以及同層級之間。 (在同層級間的導覽帶有邏輯項目，因為可能會遵循索引標籤順序。)您只要使用 <xref:System.Windows.Automation.TreeWalker> 類別，就能透過任何已篩選的樹狀檢視，由任一起點進行導覽。 您也可以使用 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 和 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>導覽到特定子系；例如，您可以非常輕易地截取支援特定控制項模式的對話方塊內所有項目。  
  
 中[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的導覽比 Active Accessibility 中的更一致。 某些專案 (例如下拉式清單和快顯視窗) 會在 Active Accessibility 樹狀目錄中出現兩次, 而從這些專案進行的導覽可能會產生非預期的結果。 其實無法正確地為 Rebar 控制項執行 Active Accessibility。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 允許重設父代及重新調整位置，因此儘管階層受到視窗擁有權強制，項目仍可放置在樹狀中任何位置。  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>角色和控制項類型  
 Active Accessibility 使用`accRole`屬性 (`IAccessible::get_actRole`) 來抓取中[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]元素的角色描述, 例如 ROLE_SYSTEM_SLIDER 或 ROLE_SYSTEM_MENUITEM。 從項目的角色可以了解他所能使用的功能。 使用 `IAccessible::accSelect` 和 `IAccessible::accDoDefaultAction`等固定方法可與控制項互動。 用戶端應用程式和 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 之間的互動受限於可透過 `IAccessible`完成的內容。  
  
 相反地， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 則從項目的預期功能大量減少其控制項類型 (由 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> 屬性所描述)。 功能是由提供者透過其特定介面實作所支援的控制項模式來判斷。 結合控制項模式即可描述由特定 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目支援的完整功能。 某些提供者必須支援特定控制項模式；例如，核取方塊的提供者必須支援切換控制項模式。 其他提供者則必須支援一組控制項模式中的一或多項；例如，按鈕必須支援切換或叫用。 也有其他提供者不支援任何控制項模式；例如無法移動、調整大小或固定的窗格即不具有任何控制項模式。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支援自訂控制項，這些控制項由 <xref:System.Windows.Automation.ControlType.Custom> 屬性識別，並且可由 <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> 屬性描述。  
  
 下表顯示 Active Accessibility 角色與[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]控制項類型的對應。  
  
|Active Accessibility 角色|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項類型|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|按鈕|  
|ROLE_SYSTEM_CLIENT|行事曆|  
|ROLE_SYSTEM_CHECKBUTTON|核取方塊|  
|ROLE_SYSTEM_COMBOBOX|下拉式方塊|  
|ROLE_SYSTEM_CLIENT|自訂|  
|ROLE_SYSTEM_LIST|資料格|  
|ROLE_SYSTEM_LISTITEM|資料項目|  
|ROLE_SYSTEM_DOCUMENT|文件|  
|ROLE_SYSTEM_TEXT|編輯|  
|ROLE_SYSTEM_GROUPING|群組|  
|ROLE_SYSTEM_LIST|頁首|  
|ROLE_SYSTEM_COLUMNHEADER|標頭項目|  
|ROLE_SYSTEM_LINK|超連結|  
|ROLE_SYSTEM_GRAPHIC|Image|  
|ROLE_SYSTEM_LIST|清單|  
|ROLE_SYSTEM_LISTITEM|清單項目|  
|ROLE_SYSTEM_MENUPOPUP|功能表|  
|ROLE_SYSTEM_MENUBAR|功能表列|  
|ROLE_SYSTEM_MENUITEM|Menu item|  
|ROLE_SYSTEM_PANE|窗格|  
|ROLE_SYSTEM_PROGRESSBAR|進度列|  
|ROLE_SYSTEM_RADIOBUTTON|選項按鈕|  
|ROLE_SYSTEM_SCROLLBAR|捲軸|  
|ROLE_SYSTEM_SEPARATOR|Separator|  
|ROLE_SYSTEM_SLIDER|滑桿|  
|ROLE_SYSTEM_SPINBUTTON|Spinner|  
|ROLE_SYSTEM_SPLITBUTTON|Split 按鈕|  
|ROLE_SYSTEM_STATUSBAR|狀態列|  
|ROLE_SYSTEM_PAGETABLIST|索引標籤|  
|ROLE_SYSTEM_PAGETAB|索引標籤項目|  
|ROLE_SYSTEM_TABLE|資料表|  
|ROLE_SYSTEM_STATICTEXT|文字|  
|ROLE_SYSTEM_INDICATOR|Thumb|  
|ROLE_SYSTEM_TITLEBAR|標題列|  
|ROLE_SYSTEM_TOOLBAR|工具列|  
|ROLE_SYSTEM_TOOLTIP|ToolTip|  
|ROLE_SYSTEM_OUTLINE|樹狀結構|  
|ROLE_SYSTEM_OUTLINEITEM|樹狀結構項目|  
|ROLE_SYSTEM_WINDOW|視窗|  
  
 如需其他控制項類型的詳細資訊，請參閱 [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)。  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>狀態和屬性  
 在 Active Accessibility 中, 元素支援一組常用的屬性, 而某些屬性 (例如`accState`) 則必須根據專案的角色來描述非常不同的事物。 伺服器必須實作所有會傳回屬性的 `IAccessible` 方法，即使方法與項目無關亦然。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]會定義更多屬性, 其中一些屬性會對應至 Active Accessibility 中的狀態。 有些屬性對所有項目而言都很常見，其他則專屬控制項類型和控制項模式。 屬性是透過唯一識別碼來區別，而且大部分屬性可使用單一方法、 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> 或 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>加以擷取。 許多屬性也可從 <xref:System.Windows.Automation.AutomationElement.Current%2A> 和 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 屬性存取子輕鬆擷取。  
  
 使用者介面自動化提供者無須實作不相關的屬性，只要針對不支援的所有屬性傳回 `null` 值即可。 而且， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心服務可以從預設視窗提供者取得一些屬性，而這些屬性會與提供者明確實作的屬性合併。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 不僅支援更多屬性，同時透過允許單一跨程序呼叫擷取多個屬性，提供更佳效能。  
  
 下表顯示兩個模型之間屬性的對應。  
  
|Active Accessibility 屬性存取子|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性識別碼|備註|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> 或 <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|如果兩者皆存在，則`AccessKeyProperty` 優先。|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|請參閱前一表格以了解角色與控制項類型的對應。|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|只適用於支援 ValuePattern 或 RangeValuePattern 的控制項類型。 RangeValue 值已標準化為 0-100，以便與 MSAA 行為一致。 值項目使用字串。|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` 在 MSAA 中沒有清楚的規格，導致提供者在此屬性中放置了不同資訊片段。|  
|`get_accHelpTopic`|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 下表顯示哪些[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]屬性會對應至 Active Accessibility 狀態常數。  
  
|Active Accessibility 狀態|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性|觸發狀態是否變更？|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|若是核取方塊，為 <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> 若是選項按鈕，為 <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Y|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|Y|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> 或 <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|Y|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|若是功能表項目，為<xref:System.Windows.Automation.ExpandCollapsePattern>|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True 且 <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> 導致 <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|支援<xref:System.Windows.Automation.SelectionItemPattern>|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Y|  
  
 下列狀態不是由大部分 Active Accessibility 的控制伺服器所執行, 或在中[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]沒有對等的。  
  
|Active Accessibility 狀態|備註|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中無法使用|  
|STATE_SYSTEM_DEFAULT|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中無法使用|  
|STATE_SYSTEM_ANIMATED|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中無法使用|  
|STATE_SYSTEM_EXTSELECTABLE|不是由 Active Accessibility 伺服器廣泛實行|  
|STATE_SYSTEM_MARQUEED|不是由 Active Accessibility 伺服器廣泛實行|  
|STATE_SYSTEM_SELFVOICING|不是由 Active Accessibility 伺服器廣泛實行|  
|STATE_SYSTEM_TRAVERSED|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中無法使用|  
|STATE_SYSTEM_ALERT_HIGH|不是由 Active Accessibility 伺服器廣泛實行|  
|STATE_SYSTEM_ALERT_MEDIUM|不是由 Active Accessibility 伺服器廣泛實行|  
|STATE_SYSTEM_ALERT_LOW|不是由 Active Accessibility 伺服器廣泛實行|  
|STATE_SYSTEM_FLOATING|不是由 Active Accessibility 伺服器廣泛實行|  
|STATE_SYSTEM_HOTTRACKED|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中無法使用|  
|STATE_SYSTEM_PRESSED|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中無法使用|  
  
 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性識別碼的完整清單，請參閱 [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)。  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>事件  
 中[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的事件機制不同于 Active Accessibility 中的, 不依賴 Windows 事件路由 (與視窗控制碼緊密系結), 而且不需要用戶端應用程式設定勾點。 事件訂閱不僅可微調到特定事件，也可以微調到特定的樹狀組件。 提供者也可以持續注意哪些事件正被接聽，藉此微調事件引發。  
  
 引發事件的項目會直接傳遞到事件回呼，因此用戶端更容易加以擷取。 如果用戶端訂閱事件時，快取要求正在作用，則會自動預先擷取項目的屬性。  
  
 下表顯示 Active Accessibility WinEvents 和[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]事件的對應。  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件識別碼|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> 屬性變更|  
|EVENT_OBJECT_CONTENTSCROLLED|相關聯捲軸上的<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 或 <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> 屬性變更。|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|沒有對等項目|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|沒有對等項目；可能有 <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> 或 <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> 屬性變更|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> 變更|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> 屬性變更|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> 屬性變更|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|未在 Active Accessibility 中一致使用。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中未定義任何直接對應的事件。|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|沒有對等項目|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|多項屬性變更事件|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> 已變更|  
|EVENT_SYSTEM_ALERT|沒有對等項目|  
|EVENT_SYSTEM_CAPTUREEND|沒有對等項目|  
|EVENT_SYSTEM_CAPTURESTART|沒有對等項目|  
|EVENT_SYSTEM_CONTEXTHELPEND|沒有對等項目|  
|EVENT_SYSTEM_CONTEXTHELPSTART|沒有對等項目|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|沒有對等項目|  
|EVENT_SYSTEM_DRAGDROPSTART|沒有對等項目|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> 屬性變更|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> 屬性變更|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> 屬性變更|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> 屬性變更|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 或 <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> 屬性變更|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 或 <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> 屬性變更|  
|EVENT_SYSTEM_SOUND|沒有對等項目|  
|EVENT_SYSTEM_SWITCHEND|沒有對等項目，但有新應用程式已收到焦點的 <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> 事件訊號。|  
|EVENT_SYSTEM_SWITCHSTART|沒有對等項目|  
|沒有對等項目|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty> 屬性變更|  
|沒有對等項目|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty> 屬性變更|  
|沒有對等項目|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty> 屬性變更|  
|沒有對等項目|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> 屬性變更|  
|沒有對等項目|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 屬性變更|  
|沒有對等項目|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty> 屬性變更|  
|沒有對等項目|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty> 屬性變更|  
|沒有對等項目|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty> 屬性變更|  
|沒有對等項目|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> 屬性變更|  
|沒有對等項目|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent> 事件|  
|沒有對等項目|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>安全性  
 某些 `IAccessible` 自訂化情節需要包裝基底 `IAccessible` 並加以呼叫。 這會有安全性顧慮，因為程式碼路徑的媒介不應該是部分受信任的元件。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 模型可讓提供者無須呼叫其他提供者程式碼。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心服務會執行所有必要彙總。  
  
## <a name="see-also"></a>另請參閱

- [使用者介面自動化基礎觀念](../../../docs/framework/ui-automation/index.md)
