---
title: 使用 UI 自動化進行自動化測試
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
caps.latest.revision: 26
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: d38183d90e99c7b8b9b5ffabb871f13886d801f0
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="using-ui-automation-for-automated-testing"></a>使用 UI 自動化進行自動化測試
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本概觀說明 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 在自動化測試案例中做為程式設計存取的架構有何幫助。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供了一致的物件模型，可讓所有 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 架構透過可存取、輕鬆自動化的方式來公開複雜、豐富的功能。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的開發目的是要接替 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]。 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 是現有的架構，專為提供存取控制項及應用程式的方案所設計。 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 設計時未考慮測試自動化，但由於協助工具和自動化有極為相似的需求，進而發展為該角色。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]除了提供更精細的協助工具方案之外，還特別設計來提供穩固的自動化測試功能。 例如， [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 依賴單一介面來同時公開使用者介面的相關資訊及收集 AT 產品所需資訊； [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 則分隔兩個模型。  
  
 若要實作 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 讓它成為跟自動化測試工具一樣有用，就需要有提供者和用戶端。 使用者介面自動化提供者是應用程式，例如 Microsoft Word、Excel 和其他以 [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] 作業系統為基礎的協力廠商應用程式或控制項。 使用者介面自動化用戶端則包括自動化測試指令碼和輔助技術應用程式。  
  
> [!NOTE]
>  本概觀的用意是展示 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]全新和改善的自動化測試功能， 並不會提供協助工具功能的資訊，除非必要，否則不會說明協助工具。  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>提供者中的使用者介面自動化  
 若要讓 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 自動化，應用程式或控制項的開發人員必須查看使用者在使用標準鍵盤和滑鼠互動時，可以在 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 物件上執行哪些動作。  
  
 一旦識別出這些按鍵動作，就應該在控制項上實作對應的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項模式 (也就是可鏡像 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目功能和行為的控制項模式)。 例如，與下拉式方塊控制項 (例如執行對話方塊) 的使用者互動一般會涉及到展開及摺疊下拉式方塊，以隱藏或顯示項目清單、從該清單中選取項目，或透過鍵盤輸入加入新值。  
  
> [!NOTE]
>  藉由其他協助工具模式，開發人員必須直接從個別按鈕、功能或其他控制項收集資訊。 可惜的是，每種控制項類型都有許多次要變化。 換句話說，即使按鈕的十個變化全都以相同方式運作，並執行相同功能，仍必須全都視為唯一的控制項。 無法得知這些控制項是否功能對等。 開發控制項模式的目的就是為了呈現這些常見的控制項行為。 如需詳細資訊，請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>實作使用者介面自動化  
 如上所述，如果沒有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]所提供的一致模型，測試工具和開發人員就必須知道架構特定的資訊，才能公開該架構中控制項的屬性和行為。 因為可能有數個不同的 UI 架構在任何 Windows 作業系統內的時候，包括[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]， [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]，而且 Windows Presentation Foundation (WPF)，它可以是鉅的任務的工作，若要測試多個應用程式看起來類似的控制項。 例如，下表列出擷取與按鈕控制項相關名稱 (或文字) 時所需的架構特定屬性名稱，並顯示單一對等的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性。  
  
|使用者介面自動化控制項類型|使用者介面架構|架構特定的屬性|使用者介面自動化屬性|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|按鈕|Windows Presentation Foundation|內容|NameProperty|  
|按鈕|Win32|標題|NameProperty|  
|Image|HTML|alt|NameProperty|  
  
 使用者介面自動化提供者會負責將其控制項的架構特定屬性對應至對等的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性。  
  
 如需在提供者中實作 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的詳細資訊，請參閱 [UI Automation Providers for Managed Code](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)。 如需實作控制項模式的詳細資訊，請參閱 [UI Automation Control Patterns](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) 和 [UI Automation Text Pattern](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)。  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>用戶端中的使用者介面自動化  
 許多自動化測試工具和案例的目標是提供一致、可重複的使用者介面操作。 這可能涉及到特定控制項單元測試，一直到在一組控制項上反覆一連串動作的測試指令碼錄製及播放。  
  
 自動化應用程式的困難在於測試與動態目標的同步處理。 例如，清單方塊控制項 (例如 Windows 工作管理員中所包含的控制項) 會顯示目前執行中應用程式的清單。 因為該清單方塊中的項目是在測試應用程式的控制之外動態更新的，所以嘗試以任何一致性來重複清單方塊中的特定項目選取是不可能的。 在測試應用程式控制之外的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 中嘗試簡單的焦點變更時，也會發生類似問題。  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>以程式設計方式存取  
 程式設計存取能夠透過程式碼，模擬由傳統滑鼠和鍵盤輸入所公開的任何互動和體驗。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 透過五個元件啟用程式設計存取：  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構有助於巡覽 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]的結構。 此樹狀結構是由 hWnd 的集合建置而成。 如需詳細資訊，請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)。  
  
-   自動化項目是 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]中的個別元件。 這些元件通常比 hWnd 更細微。 如需詳細資訊，請參閱 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)。  
  
-   自動化屬性提供了關於 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目的特定資訊。 如需詳細資訊，請參閱 [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)。  
  
-   控制項模式定義控制項功能的特定層面，可以包含屬性、方法、事件和結構資訊。 如需詳細資訊，請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
-   自動化事件會提供事件通知和資訊。 如需詳細資訊，請參閱 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)。  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>測試自動化的主要屬性  
 在 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 中唯一識別並後續找出任何控制項的能力，可以為要在該 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]上操作的自動化測試應用程式提供基礎。 用戶端和提供者使用數個 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 屬性來輔助此項功能。  
  
#### <a name="automationid"></a>AutomationID  
 在同層級之間以唯一的方式識別自動化項目。 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 並未當地語系化，與發行多國語言版本的產品時通常會當地語系化的屬性 (例如 <xref:System.Windows.Automation.AutomationElement.NameProperty> ) 不同。 請參閱 [Use the AutomationID Property](../../../docs/framework/ui-automation/use-the-automationid-property.md)。  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 不保證整個自動化樹狀結構中的唯一識別。 例如，應用程式可能會包含具有多個最上層功能表項目的功能表控制項，而這些項目也有多個子功能表項目。 這些次要功能表項目可由「項目 1」、「項目 2」、「項目 3」(依此類推) 之類的一般配置識別，因此最上層功能表項目的子系可以有重複識別項。  
  
#### <a name="controltype"></a>ControlType  
 識別自動化項目所代表的控制項類型。 重要的資訊可以從對控制項類型的了解加以推斷。 請參閱 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)。  
  
#### <a name="nameproperty"></a>NameProperty  
 這是識別或說明控制項的文字字串。 因為<xref:System.Windows.Automation.AutomationElement.NameProperty> 可以當地語系化，所以應小心使用。 請參閱 [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)。  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>在測試應用程式中實作使用者介面自動化  
  
|||  
|-|-|  
|加入使用者介面自動化參考。|以下列出使用者介面自動化用戶端所需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] DLL。<br /><br /> -UIAutomationClient.dll 會提供存取[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]用戶端應用程式開發介面。<br />-UIAutomationClientSideProvider.dll 提供了可自動化[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]控制項。 請參閱 [UI Automation Support for Standard Controls](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md)。<br />-UIAutomationTypes.dll 提供特定類型中定義的存取[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]。|  
|加入 <xref:System.Windows.Automation> 命名空間。|這個命名空間包含使用者介面自動化用戶端使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 功能 (文字處理除外) 時需要的所有要件。|  
|加入 <xref:System.Windows.Automation.Text> 命名空間。|這個命名空間包含使用者介面自動化用戶端使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 文字處理時需要的所有要件。|  
|尋找想要的控制項|自動化測試指令碼會在自動化樹狀結構中尋找代表相關控制項的使用者介面自動化項目。<br /><br /> 您可透過多種方式使用程式碼取得使用者介面自動化項目。<br /><br /> -查詢[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]使用<xref:System.Windows.Automation.Condition>陳述式。 通常會在此使用語言中性的 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 。 **注意：** <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>可透過使用能夠詳細列出 Inspect.exe 之類的工具[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]控制項的屬性。 <br /><br /> -使用<xref:System.Windows.Automation.TreeWalker>類別來周遊整個[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀目錄或其子集。<br />-追蹤焦點。<br />-使用控制項的 hWnd。<br />-使用畫面位置，例如滑鼠游標的位置。<br /><br /> 請參閱 [Obtaining UI Automation Elements](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|取得控制項模式|控制項模式會公開功能類似之控制項的一般行為。<br /><br /> 找到需要測試的控制項之後，自動化測試指令碼會從這些使用者介面自動化項目中取得想要的控制項模式。 例如，代表一般按鈕功能的 <xref:System.Windows.Automation.InvokePattern> 控制項模式，或是代表視窗功能的 <xref:System.Windows.Automation.WindowPattern> 控制項模式。<br /><br /> 請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。|  
|自動化使用者介面|自動化測試指令碼現在可以使用 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 控制項模式公開的資訊和功能，從 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 架構中控制想要的任何 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>相關工具和技術  
 有一些相關工具和技術會支援使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]來進行自動化測試。  
  
-   Inspect.exe 是[!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]應用程式可以用來收集[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]提供者和用戶端開發和偵錯資訊。 Inspect.exe 隨附於[!INCLUDE[TLA#tla_winfxsdk](../../../includes/tlasharptla-winfxsdk-md.md)]。  
  
-   MSAABridge 會將 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 資訊公開給 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 用戶端。 橋接 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 至 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 的主要目標是，提供現有 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 用戶端與任何架構 (已經實作 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]) 互動的能力。  
  
<a name="Security"></a>   
## <a name="security"></a>安全性  
 如需安全性資訊，請參閱 [UI Automation Security Overview](../../../docs/framework/ui-automation/ui-automation-security-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面自動化基礎觀念](../../../docs/framework/ui-automation/index.md)
