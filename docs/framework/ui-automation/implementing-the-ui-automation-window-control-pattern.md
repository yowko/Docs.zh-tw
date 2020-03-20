---
title: 實作 UI 自動化 Window 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: dd677ca9f610d463acc7c69f99767bd7b8781589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180039"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>實作 UI 自動化 Window 控制項模式
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題簡介實作 <xref:System.Windows.Automation.Provider.IWindowProvider>的方針和慣例，包括 <xref:System.Windows.Automation.WindowPattern> 屬性、方法和事件的相關資訊。 其他參考的連結列於主題的結尾。  
  
 控制項<xref:System.Windows.Automation.WindowPattern>模式用於支援在傳統圖形化使用者介面 （GUI） 中提供基於視窗的基本功能的控制項。 必須實現此控制模式的控制項示例包括頂級應用程式視窗、多文檔介面 （MDI） 子視窗、可調整大小的拆分窗格控制項、強制回應對話方塊和氣球説明視窗。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
 實作視窗控制項模式時，請注意下列方針和慣例：  
  
- 為能夠使用使用者介面自動化修改視窗大小和螢幕位置，控制項除了必須實作 <xref:System.Windows.Automation.Provider.ITransformProvider> 之外，還必須實作 <xref:System.Windows.Automation.Provider.IWindowProvider>。  
  
- 若控制項包含可讓它移動、調整大小、最大化、最小化或關閉的標題列和標題列項目，通常必須實作 <xref:System.Windows.Automation.Provider.IWindowProvider>。  
  
- 工具提示快顯視窗和下拉式方塊或下拉式功能表等控制項通常不會實作 <xref:System.Windows.Automation.Provider.IWindowProvider>。  
  
- 氣球說明視窗與基本工具提示快顯視窗的不同之處，在於前者提供了類似視窗的 [關閉] 按鈕。  
  
- IWindowProvider 不支援全螢幕模式，因為它對應用程式是功能特定的，而不是典型的視窗行為。  
  
<a name="Required_Members_for_IWindowProvider"></a>
## <a name="required-members-for-iwindowprovider"></a>IWindowProvider 的必要成員  
 IWindowProvider 介面需要下列屬性、方法和事件。  
  
|必要成員|成員類型|注意|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|屬性|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|屬性|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|屬性|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|屬性|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|屬性|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|屬性|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|方法|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|方法|None|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|方法|None|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|事件|None|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|事件|None|  
|<xref:System.Windows.Automation.WindowInteractionState>|事件|不保證是 <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況型別|條件|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> - 當控制項不支援請求的行為時。|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> - 當參數不是有效數字時。|  
  
## <a name="see-also"></a>另請參閱

- [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)
- [支援 UI 自動化提供者的控制項模式](support-control-patterns-in-a-ui-automation-provider.md)
- [用戶端的 UI 自動化控制項模式](ui-automation-control-patterns-for-clients.md)
- [UI Automation Tree Overview](ui-automation-tree-overview.md)
- [使用 UI 自動化中的快取](use-caching-in-ui-automation.md)
