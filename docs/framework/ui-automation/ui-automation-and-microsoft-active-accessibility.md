---
title: "UI Automation and Microsoft Active Accessibility | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Active Accessibility"
  - "UI Automation, Active Accessibility compared to"
  - "UI Automation, Microsoft Active Accessibility"
  - "Active Accessibility, UI Automation compared to"
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
caps.latest.revision: 24
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 23
---
# UI Automation and Microsoft Active Accessibility
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] 是讓應用程式可供存取的早期解決方案。[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 是 [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] 的新式協助工具模型，能滿足輔助科技產品及自動化測試工具的需求。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 透過 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 提供許多改善。  
  
 本主題包含 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的主要功能，並解釋這些功能與 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 的差異。  
  
<a name="Programming_Languages_compare"></a>   
## 程式語言：  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 以支援雙重介面的 [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] 為基礎，因此可使用 C\/C\+\+、[!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)] 和指令碼語言加以程式化。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] \(包含適用於標準控制碼的用戶端提供者程式庫\) 是以 Managed 程式碼所撰寫，而且使用 [!INCLUDE[TLA#tla_vcshrp](../../../includes/tlasharptla-vcshrp-md.md)] 或 [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)] 設計使用者介面自動化用戶端應用程式最為輕鬆。 使用 Managed 程式碼或 C\/C\+\+ 皆可撰寫使用者介面自動化提供者，亦即介面實作。  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## Windows Presentation Foundation 的支援  
 [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] 是用於建立使用者介面的新模型。[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 項目不包含 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 的原生支援；但是支援具有 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 用戶端橋接支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 只有特別為 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 撰寫的用戶端可完整利用 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 協助工具的功能，例如豐富的文字支援。  
  
<a name="Servers_and_Clients_compare"></a>   
## 伺服器和用戶端  
 在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 中，伺服器基本上只要透過實作 `IAccessible`，便能和用戶端直接通訊。  
  
 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中，則有核心服務介於伺服器 \(稱為提供者\) 與用戶端之間。 此核心服務會呼叫提供者所實作的介面，並提供額外服務，例如為項目產生唯一的執行階段識別碼。 用戶端應用程式會使用程式庫函式呼叫 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 服務。  
  
 使用者介面自動化提供者可以將資訊提供給 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 用戶端，而 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 伺服器可以將資訊提供給使用者介面自動化應用程式。 然而，因為 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 公開的資訊量不及 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，所以這兩個模型並不完全相容。  
  
<a name="UI_Elements_compare"></a>   
## UI 項目  
 由於 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 會將 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目顯示為 `IAccessible` 介面或子識別碼， 因此我們很難藉由比較兩者的 `IAccessible` 指標，來判斷它們是否參考同一個項目。  
  
 但在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中，每個項目都會顯示為 <xref:System.Windows.Automation.AutomationElement> 物件， 所以只要使用等號比較運算子或 <xref:System.Windows.Automation.AutomationElement.Equals%2A> 方法就能進行比較。這兩個方法都會比較項目的唯一執行階段識別碼。  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## 樹狀檢視和導覽  
 畫面上的 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 項目可視為以桌面為根、應用程式視窗為下層子項目、應用程式內項目為後續子系的樹狀結構。  
  
 在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 中，許多與使用者無關的自動化項目都會公開於樹狀結構內。 用戶端應用程式必須先全盤查看，才能判斷出重要的項目。  
  
 使用者介面自動化用戶端應用程式則透過篩選過的檢視來查看 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]。 此檢視只包含所需項目，也就是可提供資訊給使用者或可互動的項目。 使用者可查看只包含控制項目和只包含內容項目的預先定義檢視；此外，應用程式可以定義自訂檢視。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]簡化了向使用者描述 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 及協助使用者與應用程式互動的工作。  
  
 在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 中，於兩個項目間的導覽方式可以是空間式 \(例如移至位於畫面左側的的項目\)、邏輯式 \(例如移至下一個功能表項目，或對話方塊內依索引標籤排序的下一個項目\) 或階層式 \(例如移至容器中第一個子系，或從子系移至其父系\)。 階層式導覽相當複雜，因為事實上子項目不一定是實作 `IAccessible` 的物件。  
  
 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中，所有 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目都是支援相同基本功能的 <xref:System.Windows.Automation.AutomationElement>。 \(從提供者角度來看，這些是實作繼承自 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> 之介面的物件。\) 導覽主要為階層式：從父系到子系，以及同層級之間。 \(在同層級間的導覽帶有邏輯項目，因為可能會遵循索引標籤順序。\) 您只要使用 <xref:System.Windows.Automation.TreeWalker> 類別，就能透過任何已篩選的樹狀檢視，由任一起點進行導覽。 您也可以使用 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 和 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 導覽到特定子系；例如，您可以非常輕易地截取支援特定控制項模式的對話方塊內所有項目。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中的導覽比 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 中的導覽更具一致性。 下拉式清單及彈出視窗等部分項目會在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 樹狀結構中出現兩次，從這類項目進行導覽也可能會產生意外的結果。 事實上，要為 Rebar 控制項正確實作 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 是不可能的。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 允許重設父代及重新調整位置，因此儘管階層受到視窗擁有權強制，項目仍可放置在樹狀中任何位置。  
  
<a name="Roles_and_Control_Types"></a>   
## 角色和控制項類型  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 使用 `accRole` 屬性 \(`IAccessible::get_actRole`\) 來擷取項目在 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 中的角色描述，例如 ROLE\_SYSTEM\_SLIDER 或 ROLE\_SYSTEM\_MENUITEM。 從項目的角色可以了解他所能使用的功能。 使用 `IAccessible::accSelect` 和 `IAccessible::accDoDefaultAction` 等固定方法可與控制項互動。 用戶端應用程式和 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 之間的互動受限於可透過 `IAccessible` 完成的內容。  
  
 相反地，[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 則從項目的預期功能大量減少其控制項類型 \(由 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> 屬性所描述\)。 功能是由提供者透過其特定介面實作所支援的控制項模式來判斷。 結合控制項模式即可描述由特定 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目支援的完整功能。 某些提供者必須支援特定控制項模式；例如，核取方塊的提供者必須支援切換控制項模式。 其他提供者則必須支援一組控制項模式中的一或多項；例如，按鈕必須支援切換或叫用。 也有其他提供者不支援任何控制項模式；例如無法移動、調整大小或固定的窗格即不具有任何控制項模式。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支援自訂控制項，這些控制項由 <xref:System.Windows.Automation.ControlType.Custom> 屬性識別，並且可由 <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> 屬性描述。  
  
 下表顯示 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 角色對 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項類型的對應。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 角色|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項類型|  
|--------------------------------------------------------------------|---------------------------------------------------------------------------------|  
|ROLE\_SYSTEM\_PUSHBUTTON|按鈕|  
|ROLE\_SYSTEM\_CLIENT|行事曆|  
|ROLE\_SYSTEM\_CHECKBUTTON|核取方塊|  
|ROLE\_SYSTEM\_COMBOBOX|下拉式方塊|  
|ROLE\_SYSTEM\_CLIENT|自訂|  
|ROLE\_SYSTEM\_LIST|資料格|  
|ROLE\_SYSTEM\_LISTITEM|資料項目|  
|ROLE\_SYSTEM\_DOCUMENT|文件|  
|ROLE\_SYSTEM\_TEXT|Edit|  
|ROLE\_SYSTEM\_GROUPING|群組|  
|ROLE\_SYSTEM\_LIST|頁首|  
|ROLE\_SYSTEM\_COLUMNHEADER|標頭項目|  
|ROLE\_SYSTEM\_LINK|超連結|  
|ROLE\_SYSTEM\_GRAPHIC|Image|  
|ROLE\_SYSTEM\_LIST|清單|  
|ROLE\_SYSTEM\_LISTITEM|清單項目|  
|ROLE\_SYSTEM\_MENUPOPUP|功能表|  
|ROLE\_SYSTEM\_MENUBAR|功能表列|  
|ROLE\_SYSTEM\_MENUITEM|Menu item|  
|ROLE\_SYSTEM\_PANE|窗格|  
|ROLE\_SYSTEM\_PROGRESSBAR|進度列|  
|ROLE\_SYSTEM\_RADIOBUTTON|選項按鈕|  
|ROLE\_SYSTEM\_SCROLLBAR|捲軸|  
|ROLE\_SYSTEM\_SEPARATOR|Separator|  
|ROLE\_SYSTEM\_SLIDER|滑桿|  
|ROLE\_SYSTEM\_SPINBUTTON|Spinner|  
|ROLE\_SYSTEM\_SPLITBUTTON|Split 按鈕|  
|ROLE\_SYSTEM\_STATUSBAR|狀態列|  
|ROLE\_SYSTEM\_PAGETABLIST|索引標籤|  
|ROLE\_SYSTEM\_PAGETAB|索引標籤項目|  
|ROLE\_SYSTEM\_TABLE|資料表|  
|ROLE\_SYSTEM\_STATICTEXT|Text|  
|ROLE\_SYSTEM\_INDICATOR|Thumb|  
|ROLE\_SYSTEM\_TITLEBAR|標題列|  
|ROLE\_SYSTEM\_TOOLBAR|工具列|  
|ROLE\_SYSTEM\_TOOLTIP|ToolTip|  
|ROLE\_SYSTEM\_OUTLINE|樹狀結構|  
|ROLE\_SYSTEM\_OUTLINEITEM|樹狀結構項目|  
|ROLE\_SYSTEM\_WINDOW|視窗|  
  
 如需其他控制項類型的詳細資訊，請參閱[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)。  
  
<a name="States_and_Properties"></a>   
## 狀態和屬性  
 在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 中，項目會支援一組常見屬性。然而，根據項目角色的不同，某些屬性必須用來描述非常不同的事物 \(例如 `accState`\)。 伺服器必須實作所有會傳回屬性的 `IAccessible` 方法，即使方法與項目無關亦然。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 定義了更多屬性，其中某些對應到 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 中的狀態。 有些屬性對所有項目而言都很常見，其他則專屬控制項類型和控制項模式。 屬性是透過唯一識別碼來區別，而且大部分屬性可使用單一方法、<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> 或 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> 加以擷取。 許多屬性也可從 <xref:System.Windows.Automation.AutomationElement.Current%2A> 和 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 屬性存取子輕鬆擷取。  
  
 使用者介面自動化提供者無須實作不相關的屬性，只要針對不支援的所有屬性傳回 `null` 值即可。 而且，[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心服務可以從預設視窗提供者取得一些屬性，而這些屬性會與提供者明確實作的屬性合併。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 不僅支援更多屬性，同時透過允許單一跨程序呼叫擷取多個屬性，提供更佳效能。  
  
 下表顯示兩個模型之間屬性的對應。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 屬性存取子|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性識別碼|備註|  
|-----------------------------------------------------------------------|---------------------------------------------------------------------------------|--------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> 或 <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|如果兩者皆存在，則 `AccessKeyProperty` 優先。|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>|``|  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|請參閱前一表格以了解角色與控制項類型的對應。|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=fullName><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=fullName>|只適用於支援 ValuePattern 或 RangeValuePattern 的控制項類型。 RangeValue 值已標準化為 0\-100，以便與 MSAA 行為一致。 值項目使用字串。|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 不支援|`accDescription` 在 MSAA 中沒有清楚的規格，導致提供者在此屬性中放置了不同資訊片段。|  
|`get_accHelpTopic`|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 不支援||  
  
 下表顯示哪些 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性對應至 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 狀態常數。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 狀態|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性|觸發狀態是否變更？|  
|--------------------------------------------------------------------|------------------------------------------------------------------------------|---------------|  
|STATE\_SYSTEM\_CHECKED|若是核取方塊，為 <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> 若是選項按鈕，為 <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Y|  
|STATE\_SYSTEM\_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> \= <xref:System.Windows.Automation.ExpandCollapseState>|Y|  
|STATE\_SYSTEM\_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> \= <xref:System.Windows.Automation.ExpandCollapseState> 或 <xref:System.Windows.Automation.ExpandCollapseState>|Y|  
|STATE\_SYSTEM\_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE\_SYSTEM\_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE\_SYSTEM\_HASPOPUP|若是功能表項目，為 <xref:System.Windows.Automation.ExpandCollapsePattern>|N|  
|STATE\_SYSTEM\_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> \= True 且 <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> 導致 <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE\_SYSTEM\_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> \=<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE\_SYSTEM\_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> \= <xref:System.Windows.Automation.ToggleState>|N|  
|STATE\_SYSTEM\_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE\_SYSTEM\_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE\_SYSTEM\_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> \= True|N|  
|STATE\_SYSTEM\_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE\_SYSTEM\_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=fullName> 和 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=fullName>|N|  
|STATE\_SYSTEM\_SELECTABLE|支援 <xref:System.Windows.Automation.SelectionItemPattern>|N|  
|STATE\_SYSTEM\_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE\_SYSTEM\_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE\_SYSTEM\_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Y|  
  
 下列狀態未由大多數 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 控制伺服器實作，或在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中沒有對等狀態。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 狀態|備註|  
|--------------------------------------------------------------------|--------|  
|STATE\_SYSTEM\_BUSY|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中無法使用|  
|STATE\_SYSTEM\_DEFAULT|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中無法使用|  
|STATE\_SYSTEM\_ANIMATED|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中無法使用|  
|STATE\_SYSTEM\_EXTSELECTABLE|未由 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 伺服器廣泛實作|  
|STATE\_SYSTEM\_MARQUEED|未由 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 伺服器廣泛實作|  
|STATE\_SYSTEM\_SELFVOICING|未由 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 伺服器廣泛實作|  
|STATE\_SYSTEM\_TRAVERSED|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中無法使用|  
|STATE\_SYSTEM\_ALERT\_HIGH|未由 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 伺服器廣泛實作|  
|STATE\_SYSTEM\_ALERT\_MEDIUM|未由 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 伺服器廣泛實作|  
|STATE\_SYSTEM\_ALERT\_LOW|未由 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 伺服器廣泛實作|  
|STATE\_SYSTEM\_FLOATING|未由 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 伺服器廣泛實作|  
|STATE\_SYSTEM\_HOTTRACKED|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中無法使用|  
|STATE\_SYSTEM\_PRESSED|在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中無法使用|  
  
 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性識別碼的完整清單，請參閱[UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)。  
  
<a name="uiautomation_events_compare"></a>   
## 事件  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中的事件機制不同於 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 中的機制，其不依賴 Windows 事件路由 \(與視窗控制代碼緊密繫結\)，也不要求用戶端應用程式設定掛勾。 事件訂閱不僅可微調到特定事件，也可以微調到特定的樹狀組件。 提供者也可以持續注意哪些事件正被接聽，藉此微調事件引發。  
  
 引發事件的項目會直接傳遞到事件回呼，因此用戶端更容易加以擷取。 如果用戶端訂閱事件時，快取要求正在作用，則會自動預先擷取項目的屬性。  
  
 下表顯示 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] WinEvents 和 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件的對應。  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件識別碼|  
|--------------|---------------------------------------------------------------------------------|  
|EVENT\_OBJECT\_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> 屬性變更|  
|EVENT\_OBJECT\_CONTENTSCROLLED|相關聯捲軸上的 <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 或 <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> 屬性變更。|  
|EVENT\_OBJECT\_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_DEFACTIONCHANGE|沒有對等項目|  
|EVENT\_OBJECT\_DESCRIPTIONCHANGE|沒有對等項目；可能有 <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> 或 <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> 屬性變更|  
|EVENT\_OBJECT\_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT\_OBJECT\_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> 變更|  
|EVENT\_OBJECT\_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> 屬性變更|  
|EVENT\_OBJECT\_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> 屬性變更|  
|EVENT\_OBJECT\_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_REORDER|在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 中未一致使用。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中未定義任何直接對應的事件。|  
|EVENT\_OBJECT\_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT\_OBJECT\_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT\_OBJECT\_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT\_OBJECT\_SELECTIONWITHIN|沒有對等項目|  
|EVENT\_OBJECT\_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_STATECHANGE|多項屬性變更事件|  
|EVENT\_OBJECT\_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=fullName> 和 <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=fullName> 已變更|  
|EVENT\_SYSTEM\_ALERT|沒有對等項目|  
|EVENT\_SYSTEM\_CAPTUREEND|沒有對等項目|  
|EVENT\_SYSTEM\_CAPTURESTART|沒有對等項目|  
|EVENT\_SYSTEM\_CONTEXTHELPEND|沒有對等項目|  
|EVENT\_SYSTEM\_CONTEXTHELPSTART|沒有對等項目|  
|EVENT\_SYSTEM\_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT\_SYSTEM\_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT\_SYSTEM\_DRAGDROPEND|沒有對等項目|  
|EVENT\_SYSTEM\_DRAGDROPSTART|沒有對等項目|  
|EVENT\_SYSTEM\_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT\_SYSTEM\_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT\_SYSTEM\_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT\_SYSTEM\_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT\_SYSTEM\_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT\_SYSTEM\_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> 屬性變更|  
|EVENT\_SYSTEM\_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> 屬性變更|  
|EVENT\_SYSTEM\_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> 屬性變更|  
|EVENT\_SYSTEM\_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> 屬性變更|  
|EVENT\_SYSTEM\_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 或 <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> 屬性變更|  
|EVENT\_SYSTEM\_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 或 <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> 屬性變更|  
|EVENT\_SYSTEM\_SOUND|沒有對等項目|  
|EVENT\_SYSTEM\_SWITCHEND|沒有對等項目，但有新應用程式已收到焦點的 <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> 事件訊號。|  
|EVENT\_SYSTEM\_SWITCHSTART|沒有對等項目|  
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
## 安全性  
 某些 `IAccessible` 自訂化情節需要包裝基底 `IAccessible` 並加以呼叫。 這會有安全性顧慮，因為程式碼路徑的媒介不應該是部分受信任的元件。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 模型可讓提供者無須呼叫其他提供者程式碼。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心服務會執行所有必要彙總。  
  
## 請參閱  
 [UI Automation Fundamentals](../../../docs/framework/ui-automation/index.md)