---
title: "UI Automation Support for the Menu Control Type | Microsoft Docs"
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
  - "control types, Menu"
  - "UI Automation, Menu control type"
  - "Menu control type"
ms.assetid: 016323cb-f800-4938-b77b-2eb25d646090
caps.latest.revision: 24
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 24
---
# UI Automation Support for the Menu Control Type
> [!NOTE]
>  這份文件適用於想要使用 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md) 命名空間中定義之 Managed <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 類別的 .NET Framework 開發人員。 如需 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 的最新資訊，請參閱 Windows Automation API：使用者介面自動化[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)][!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)][UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
 本主題提供功能表控制項類型的 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 支援相關資訊。 其中說明控制項的 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 樹狀結構，並提供特定控制項案例的屬性和控制項模式。  
  
 功能表控制項可將命令和事件處理常式的關聯項目以階層方式組織。 在典型的 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 應用程式中，功能表列會包含數個功能表按鈕 \(例如 \[檔案\][UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)、\[編輯\][!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 和 \[視窗\][!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]\)，而每個功能表按鈕又會顯示功能表。 功能表又包含一組功能表項目 \(例如 \[開新檔案\]<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>、\[開啟舊檔\][UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md) 和 \[關閉檔案\][!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]\)，這些項目可展開顯示更多的功能表項目，或在按一下時可執行特定的動作。  
  
 下列章節會定義功能表控制項類型所需的 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 樹狀結構、屬性、控制項模式和事件。 無論是 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)、[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 或 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]，<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 需求都適用於所有清單控制項。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## 必要的使用者介面自動化樹狀結構  
 下表描述功能表控制項之 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 樹狀結構的控制項檢視和內容檢視，並說明各檢視中可包含的內容。 如需 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 樹狀結構的詳細資訊，請參閱[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|控制項檢視|內容檢視|  
|-----------|----------|  
|功能表<br /><br /> -   MenuItem \(1 或多個\)|不適用 \(除非功能表控制項為非功能表項目之物件父系的內容功能表\)<br /><br /> -   MenuItem \(1 或多個\)|  
  
 功能表控制項一律會出現在 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 樹狀結構的控制項檢視和內容檢視。 功能表控制項類別應該顯示於其資訊所參考的控制項下方。 使用者介面自動化用戶端必須接聽 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>，以確保它們持續取得功能表控制項所傳達的資訊。 內容功能表控制項是特殊案例。 它們會顯示為桌面的子系。  
  
<a name="Required_UI_Automation_Properties"></a>   
## 必要的使用者介面自動化屬性  
 下表列出 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性，其值或定義與功能表控制項類型特別有關。 如需 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性的詳細資訊，請參閱[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性|值|備註|  
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------|--------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|不支援|功能表控制項不需要設定 Name 屬性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|典型的功能表控制項不預期有標籤。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|功能表|此值與所有使用者介面架構的值相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|此功能表控制項不會包含在 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 樹狀結構的內容檢視中。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|此功能表控制項一律包含在 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 樹狀結構的控制項檢視中。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## 必要的使用者介面自動化控制項模式  
 功能表控制項類型沒有必要的控制項模式。  
  
<a name="Required_UI_Automation_Events"></a>   
## 必要的使用者介面自動化事件  
 當功能表控制項出現在畫面時，必須引發 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>。<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 將包含控制項的文字。 當功能表從畫面消失時，必須引發 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>。  
  
 下表列出所有功能表控制項都必須支援的 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 事件。 如需事件的詳細資訊，請參閱 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>。  
  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 事件|支援\/值|備註|  
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent>|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent>|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 屬性變更事件。|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要項|無|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要項|無|  
  
## 請參閱  
 <xref:System.Windows.Automation.ControlType.Menu>   
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)