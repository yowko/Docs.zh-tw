---
title: "UI Automation Support for the Text Control Type | Microsoft Docs"
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
  - "Text control type"
  - "UI Automation, Text control type"
  - "control types, Text"
ms.assetid: ab0d0ada-8a71-4547-9c03-aadf675938f2
caps.latest.revision: 19
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 19
---
# UI Automation Support for the Text Control Type
> [!NOTE]
>  這份文件適用於想要使用 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md) 命名空間中定義之 Managed <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 類別的 .NET Framework 開發人員。 如需 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 的最新資訊，請參閱 Windows Automation API：使用者介面自動化[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)][!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)][UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
 本主題提供文字控制項類型的 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 支援相關資訊。 在 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 中，控制項類型是一組控制項條件，控制項必須符合條件才能使用 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md) 屬性。 這些條件包括 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構的特定方針、[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md) 屬性值和控制項模式。  
  
 文字控制項是代表螢幕上一段文字的基本使用者介面項目。  
  
 下列章節會定義文字控制項類型所需的 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構、屬性、控制項模式和事件。 無論是 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)、[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 或 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]，<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 需求都適用於所有文字控制項。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## 必要的使用者介面自動化樹狀結構  
 下表描述文字控制項之 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構的控制項檢視和內容檢視，並說明各檢視中可包含的內容。 如需 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構的詳細資訊，請參閱[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|控制項檢視|內容檢視|  
|-----------|----------|  
|Text|Text \(如果內容\)|  
  
 控制項可以單獨用來當做標籤或當做表單上的靜態文字。 它也可以包含下列結構內：  
  
-   ListItem  
  
-   TreeItem  
  
-   DataItem  
  
 文字控制項可能不在 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構的內容檢視，因為文字通常是透過另一個控制項的 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md) 顯示。 例如，用來標示下拉式方塊控制項的文字會透過控制項的 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 值公開。 因為下拉式方塊控制項是在使用者介面自動化樹狀結構的內容檢視中，所以文字控制項不需要在那個檢視中。 文字控制項在內容檢視中一律有 0 個子系  
  
<a name="Required_UI_Automation_Properties"></a>   
## 必要的使用者介面自動化屬性  
 下表列示 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性，其值或定義與文字控制項特別有關。 如需 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性的詳細資訊，請參閱[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性|值|備註|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------|--------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|請參閱備註。|此屬性的值在應用程式中的所有控制項都不得重複。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|請參閱備註。|包含整個控制項的最外層矩形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|請參閱備註。|如果有週框即受支援。 如果週框中沒有任何可點選的點，而且您執行的是特殊化點擊測試，則會覆寫並提供可點選的點。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|請參閱備註。|如果控制項可接收鍵盤焦點，就必須支援此屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|請參閱備註。|文字列控制項的名稱一律為它所顯示的 txt。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|文字控制項沒有靜態文字標籤。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|文字|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|文字|對應到文字控制項類型的當地語系化字串。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|視情況而定|如果文字控制項包含了未在另一個控制項的 NameProperty 中公開的資訊，文字控制項將會是內容。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|文字控制項必須一律為控制項。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## 必要的使用者介面自動化控制項模式  
 下表列出文字控制項必須支援的 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 控制項模式。 如需控制項模式的詳細資訊，請參閱 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>。  
  
|控制項模式|支援|備註|  
|-----------|--------|--------|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|永不|文字一律不支援 ValuePattern。 如果文字是可編輯的，則此為編輯控制項類型。|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|視情況而定|為了提供更優質的協助，文字應該支援文字控制項模式，不過這並非必要。 當文字有豐富的樣式和屬性 \(例如色彩、粗體和斜體\) 時，文字控制項模式相當有用。視架構而定。|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|視情況而定|如果文字項目包含在資料表控制項中，這必須受到支援。|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|視情況而定|如果文字項目包含在資料表控制項中，這必須受到支援。|  
  
<a name="Required_UI_Automation_Events"></a>   
## 必要的使用者介面自動化事件  
 下表列示所有文字控制項都必須支援的 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 事件。 如需事件的詳細資訊，請參閱 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>。  
  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 事件|支援|備註|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|--------|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|永不|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要項|無|  
  
## 請參閱  
 <xref:System.Windows.Automation.ControlType.Text>   
 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)