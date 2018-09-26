---
title: DataItem 控制項類型的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: e055733a8f3d1ecb9c1fcea336bbe90ddd155731
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47172845"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>DataItem 控制項類型的 UI 自動化支援
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題提供 DataItem 控制項類型的 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 支援相關資訊。 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 中，控制項類型是一組控制項條件，控制項必須符合條件才能使用 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 屬性。 這些條件包括 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性值和控制項模式的特定方針。  
  
 連絡人清單中的項目即是資料項目控制項的範例。 資料項目控制項包含與使用者相關的資訊。 由於包含更為豐富的資訊，這種控制項比簡單的清單項目複雜。  
  
 下列章節會定義 DataItem 控制項類型所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構、屬性、控制項模式和事件。 無論是 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]或 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]， [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]需求都適用於所有資料項目控制項。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必要的使用者介面自動化樹狀結構  
 下表描述與資料項目控制項相關之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視和內容檢視，並說明各檢視中可包含的內容。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的詳細資訊，請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構 - 控制項檢視|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構 - 內容檢視|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataItem<br /><br /> -而有所不同 (0 個以上; 可以結構化為階層)|DataItem<br /><br /> -而有所不同 (0 個以上; 可以結構化為階層)|  
  
 資料格中資料項目 (Item) 的項目 (Element) 可裝載各種不同的物件，包括另一層資料項目，或是特定資料格項目 (Element) 如文字、影像或編輯控制項。 如果資料項目 (Item) 的項目 (Element) 具備特定物件角色，則該項目 (Element) 應公開為特定控制項類型；例如，資料格中可選資料項目 (Item) 的 ListItem 控制項類型。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必要的使用者介面自動化屬性  
 下表列出屬性，其值或定義與資料項目控制項特別有關。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性的詳細資訊，請參閱 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|屬性|值|注意|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|請參閱備註。|此屬性的值在應用程式中的所有控制項都不得重複。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|請參閱備註。|包含整個控制項的最外層矩形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|請參閱備註。|如果有週框即受支援。 如果週框中沒有任何可點選的點，而且您執行的是特殊化點擊測試，則會覆寫並提供可點選的點。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataItem|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|資料項目控制項必須一律為內容。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|資料項目控制項必須一律為控制項。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|請參閱備註。|如果控制項可接收鍵盤焦點，就必定支援此屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|請參閱備註。|如果控制項包含動態更新的狀態，則必須支援此屬性，使輔助技術得以在項目的狀態變更時接收更新。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|請參閱備註。|這個字串值可讓使用者知道項目所代表的物件為何。 例如「媒體檔案」或「連絡人」。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|資料項目控制項沒有靜態文字標籤。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|「資料項目」|對應到 DataItem 控制項類型的當地語系化字串。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|請參閱備註。|資料項目控制項一律會包含主要文字項目，這是最富語意的識別項，可讓使用者聯想該項目。|  
  
<a name="_Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>必要的使用者介面自動化控制項模式  
 下表列出所有資料項目控制項必須支援的 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 控制項模式。 如需控制項模式的詳細資訊，請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
|控制項模式|支援|注意|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|視情況而定|如果資料項目可以展開或摺疊來顯示和隱藏資訊，則必須支援展開摺疊模式。|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|視情況而定|當容器內包含一組資料項目，可以在空間上逐一巡覽項目時，資料項目將會支援方格項目模式。|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|視情況而定|當資料容器有太多項目，無法一次顯示在螢幕上時，所有資料項目會支援捲動項目模式的捲動檢視功能。|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|是|所有資料項目必須支援選取項目模式，表示已選取項目。|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|視情況而定|如果資料項目包含在資料格控制項類型內，則會支援此模式。|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|視情況而定|如果資料項目包含可循環的狀態。|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|視情況而定|如果資料項目的主要文字可以編輯，則必須支援值模式。|  
  
<a name="Working_with_Data_Items_in_Large_Lists"></a>   
## <a name="working-with-data-items-in-large-lists"></a>在大型清單中使用資料項目  
 為提高效能，大型清單在 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 架構中通常會將資料虛擬化。 因此，使用者介面自動化用戶端無法像在其他項目容器一樣，使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 查詢功能將完整樹狀結構的內容集中顯示在一起。 用戶端應將項目設為捲動檢視 (或展開控制項以顯示所有有用的選項)，才能從資料項目存取完整的資訊。  
  
 在資料項目的 `SetFocus` 自動化項目上呼叫 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 時， [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] 會將焦點成功傳回資料項目樹狀子目錄中並設為 Edit。  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必要的使用者介面自動化事件  
 下表列出所有資料項目控制項都必須支援的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 如需事件的詳細資訊，請參閱 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支援|注意|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要|無|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|視情況而定|無|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|必要|無|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|必要|無|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|必要|無|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> 屬性變更事件。|視情況而定|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|視情況而定|無|  
  
<a name="Data_Item_Control_Type_Example"></a>   
## <a name="dataitem-control-type-example"></a>DataItem 控制項類型範例  
 下圖顯示在清單檢視控制項中的 DataItem 控制項類型，且包含對資料行中豐富資訊的支援。  
  
 ![包含兩個資料項目之 List View 控制項的圖形](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 與資料項目控制項相關之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視和內容檢視顯示如下。 每個自動化項目的控制項模式顯示在括號中。 Group "Contoso" 也是資料格主控制項資料格的一部分。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構 - 控制項檢視|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構 - 內容檢視|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-群組"Contoso"（Table、 格線）<br />-DataItem"帳戶 Receivable.doc"（TableItem GridItem、 SelectionItem，叫用）<br />-映像的"Accounts Receivable.doc"<br />-編輯 「 名稱 」 （TableItem，GridItem，值"Accounts Receivable.doc"）<br />-編輯 「 修改日期 」 (TableItem，GridItem，值 「 8/25/2006年下午 3 點 29")<br />-編輯 「 大小 」 （GridItem，TableItem，值"11.0 KB）<br />-DataItem"帳戶 Payable.doc"（TableItem GridItem、 SelectionItem，叫用）<br />-   ...|-群組"Contoso"（Table、 格線）<br />-DataItem"帳戶 Receivable.doc"（TableItem GridItem、 SelectionItem，叫用）<br />-映像的"Accounts Receivable.doc"<br />-編輯 「 名稱 」 （TableItem，GridItem，值"Accounts Receivable.doc"）<br />-編輯 「 修改日期 」 (TableItem，GridItem，值 「 8/25/2006年下午 3 點 29")<br />-編輯 「 大小 」 （GridItem，TableItem，值"11.0 KB）<br />-DataItem"帳戶 Payable.doc"（TableItem GridItem、 SelectionItem，叫用）<br />-   …|  
  
 如果資料格表示可選取項目的清單，則對應的使用者介面項目可使用 ListItem 控制項類型公開，而不是 DataItem 控制項類型。 在前述範例中，Group ("Contoso") 下的 DataItem 項目 ("Accounts Receivable.doc" 和 "Accounts Payable.doc") 可藉由公開為 ListItem 控制項類型的方式獲得改善，因為該類型已支援 SelectionItem 控制項模式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Automation.ControlType.DataItem>  
 [UI 自動化控制項類型概觀](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI 自動化概觀](../../../docs/framework/ui-automation/ui-automation-overview.md)
