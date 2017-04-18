---
title: "UI Automation Support for the Document Control Type | Microsoft Docs"
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
  - "control types, Document"
  - "Document control type"
  - "UI Automation, Document control type"
ms.assetid: a79d594b-1ca0-4543-8dac-afd2c645201d
caps.latest.revision: 27
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 27
---
# UI Automation Support for the Document Control Type
> [!NOTE]
>  這份文件適用於想要使用 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md) 命名空間中定義之 Managed <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 類別的 .NET Framework 開發人員。 如需 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 的最新資訊，請參閱 Windows Automation API：使用者介面自動化[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)][!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)][UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
 本主題提供文件控制項類型的 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 支援相關資訊。 在 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 中，控制項類型是一組控制項條件，控制項必須符合條件才能使用 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md) 屬性。 這些條件包括 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構的特定指導方針、[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md) 屬性值和控制項模式。  
  
 控制項可讓使用者檢視和操作多個頁面的文字。 不像編輯控制項僅支援簡單的一行未格式化的文字，文件控制項可以主控樣式和格式化豐富的文字。  
  
 下列章節會定義文件控制項類型所需的 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構、屬性、控制項模式和事件。 無論是 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)、[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 或 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]，<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 需求都適用於所有文件控制項。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## 必要的使用者介面自動化樹狀結構  
 下表描述文件控制項之 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構的控制項檢視和內容檢視，並說明各檢視中可包含的內容。 如需 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構的詳細資訊，請參閱[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|控制項檢視|內容檢視|  
|-----------|----------|  
|文件<br /><br /> -   視情況而定|文件<br /><br /> -   視情況而定|  
  
<a name="Required_UI_Automation_Properties"></a>   
## 必要的使用者介面自動化屬性  
 下表列示 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性，其值或定義與文件控制項特別有關。 如需 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性的詳細資訊，請參閱[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性|值|備註|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------|--------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|請參閱備註。|此屬性的值在應用程式中的所有控制項都不得重複。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|請參閱備註。|包含整個控制項的最外層矩形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|請參閱備註。|文件具有可按的點，它會使文件容器中其中一個項目的文件具有焦點。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|文件|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|文件控制項一律包含在 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構的內容檢視。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|文件控制項一律包含在 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 樹狀結構的控制項檢視。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|請參閱備註。|如果控制項可接收鍵盤焦點，就必須支援此屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|請參閱備註。|這個屬性的值應該是文件控制項的標籤。 通常會使用文件的標題。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|文件|對應到文件控制項類型的當地語系化字串。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|請參閱備註。|文件控制項通常會因它載入來源的檔案名稱得名。 這通常會顯示在包含視窗或框架標題。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## 必要的使用者介面自動化控制項模式  
 下表列出文件控制項必須支援的 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 控制項模式。 如需控制項模式的詳細資訊，請參閱 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>。  
  
|控制項模式|支援|備註|  
|-----------|--------|--------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|視情況而定|文件控制項的跨越範圍可能大於檢視區的跨越範圍。 如果內容是可捲動的，控制項應該支援捲動控制項模式。|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|必要項|文件控制項的跨越範圍可能大於檢視區的跨越範圍。 如果內容是可捲動的，控制項應該支援捲動控制項模式。|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|永不|因為控制項的內容通常會跨越多頁，文件控制項不支援此控制項模式。 使用者介面自動化用戶端應該使用 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 取得文件的文字資訊。|  
  
<a name="Required_UI_Automation_Events"></a>   
## 必要的使用者介面自動化事件  
 下表列出所有文件控制項都必須支援的 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 事件。 如需事件的詳細資訊，請參閱 <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>。  
  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 事件|支援|備註|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|--------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|視情況而定|如果此控制項支援選擇控制項模式，就必須支援這個事件。|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> 屬性變更事件。|永不|無|  
  
## 請參閱  
 <xref:System.Windows.Automation.ControlType.Document>   
 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)