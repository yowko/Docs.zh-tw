---
title: "UI 自動化概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
caps.latest.revision: "35"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d86c70ec4421bc716b12044bac30f8f925c375f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-overview"></a>UI 自動化概觀
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 是 [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]的新協助工具架構，可在所有支援 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]的作業系統上使用。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 會以程式設計方式存取桌面上大部分的 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 項目，啟用輔助技術產品 (例如螢幕助讀員)，以便為使用者提供 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 的相關資訊，以及使用標準輸入以外的方式來操作 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 也可以讓自動化測試指令碼與 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]互動。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]不會啟用由不同使用者透過啟動處理序之間通訊**以執行**命令。  
  
 撰寫使用者介面自動化用戶端應用程式時，可以保證應用程式可在多個架構上運作。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心可以降低組成 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]各種元件之架構的任何差異。 例如， `Content` 按鈕的 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 屬性、 `Caption` 按鈕的 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 屬性以及 HTML 影像的 `ALT` 屬性，都會對應至 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>檢視中的單一屬性 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]、 [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)]和 [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)]中的完整功能。  
  
 使用者介面自動化提供者會透過內建的橋接服務，為 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] 用戶端應用程式提供某些支援。  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>提供者和用戶端  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 具有四個主要元件，如下表所示。  
  
|元件|描述|  
|---------------|-----------------|  
|提供者 [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] (UIAutomationProvider.dll 和 UIAutomationTypes.dll)|一組由使用者介面自動化提供者實作的介面定義，提供 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目之相關資訊，以及對程式設計輸入做出回應的物件。|  
|用戶端 API (UIAutomationClient.dll 和 UIAutomationTypes.dll)|一組 Managed 程式碼，可讓使用者介面自動化用戶端應用程式取得 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 的相關資訊，並將輸入傳送至控制項。|  
|UiAutomationCore.dll|基礎程式碼 (有時稱為 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心) 會處理提供者和用戶端之間的通訊。|  
|UIAutomationClientsideProviders.dll|一組適用於標準舊版控制項的使用者介面自動化提供者。 ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]控制項會有原生支援[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]。)這個支援將會自動可供用戶端應用程式使用。|  
  
 就軟體開發人員的觀點而言，使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的方法有兩種：建立自訂控制項 (使用提供者 API) 的支援，以及建立使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心與 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目 (使用用戶端 API) 通訊的應用程式。 視您著重的部分而定，您應該參閱本文件的不同部分。 您可以深入了解這些概念，並在下列章節中取得實際的操作說明知識。  
  
|區段|主題|適用對象|  
|-------------|--------------------|--------------|  
|[UI 自動化基礎觀念](../../../docs/framework/ui-automation/index.md)（本節）|概念概觀淺論。|全部。|  
|[Managed 程式碼的使用者介面自動化提供者](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|協助您使用提供者 API 的概觀及操作說明主題。|控制項開發人員。|  
|[Managed 程式碼的使用者介面自動化用戶端](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|協助您使用用戶端 API 的概觀及操作說明主題。|用戶端應用程式開發人員。|  
|[使用者介面自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|提供者應如何實作控制項模式，以及哪些功能可供用戶端使用的相關資訊。|全部。|  
|[使用者介面自動化文字模式](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|提供者應如何實作文字控制項模式，以及哪些功能可供用戶端使用的相關資訊。|全部。|  
|[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)|不同控制項類型支援之屬性和控制項模式的相關資訊。|全部。|  
  
 下表會列出 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間、包含這些命名空間的 DLL 以及命名空間的適用對象。  
  
|命名空間|參考的 DLL|適用對象|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|使用者介面自動化用戶端開發人員；用於尋找 <xref:System.Windows.Automation.AutomationElement> 物件、註冊 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件以及使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控制項模式。|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]以外之架構的使用者介面自動化提供者開發人員。|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]以外之架構的使用者介面自動化提供者開發人員；用於實作 TextPattern 控制項模式。|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]的使用者介面自動化提供者開發人員。|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>使用者介面自動化模型  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 會將 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 的每個部分公開給用戶端應用程式，做為 <xref:System.Windows.Automation.AutomationElement>。 項目包含於樹狀結構中，且桌面是根項目。 用戶端可將樹狀結構之未經處理的檢視篩選為控制項檢視或內容檢視。 應用程式也可以建立自訂檢視。  
  
 <xref:System.Windows.Automation.AutomationElement> 物件會公開其所代表之 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目的常見屬性。 其中一個屬性是控制項類型，它會將其基本外觀和功能定義為單一可辨識的實體：例如，按鈕或核取方塊。  
  
 此外，項目還會公開控制項模式，用以提供其控制項類型專用的屬性。 控制項模式也會公開方法，讓用戶端取得項目的進一步資訊及提供輸入。  
  
> [!NOTE]
>  控制項類型和控制項模式之間並不存在一對一的對應關係。 控制項模式可由多個控制項類型所支援，且控制項可支援多個控制項模式，每個控制項都會公開其行為的不同層面。 例如，下拉式方塊擁有至少兩個控制項模式：其中一個代表展開和折疊的能力，另一個則代表選取機制。 如需特定資訊，請參閱 [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 也可以透過事件，將資訊提供給用戶端應用程式。 與 [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)]不同的是， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件並不是以廣播機制為基礎。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 用戶端會註冊特定事件通知，且可以要求將特定的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性和控制項模式資訊傳遞至所屬的事件處理常式。 此外， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件也包含引發事件之項目的參考。 提供者可以選擇引發事件來改善效能，取決於是否有任何用戶端接聽。  
  
## <a name="see-also"></a>請參閱  
 [UI 自動化樹狀目錄概觀](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI 自動化控制項模式概觀](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI 自動化屬性概觀](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [UI 自動化事件概觀](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [UI 自動化安全性概觀](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
