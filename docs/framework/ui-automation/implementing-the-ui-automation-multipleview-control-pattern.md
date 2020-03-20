---
title: 實作 UI 自動化 MultipleView 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 9decb617e30a340d3e73e911f7848110de5599e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180162"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>實作 UI 自動化 MultipleView 控制項模式
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題將介紹實作 <xref:System.Windows.Automation.Provider.IMultipleViewProvider>的方針和慣例，包括事件和屬性的相關資訊。 其他參考的連結列於主題的結尾。  
  
 <xref:System.Windows.Automation.MultipleViewPattern> 控制項模式可用來支援控制項，這種控制項提供相同一組資訊或子控制項的多種不同表示，而且能夠在這些表示之間切換。  
  
 可以顯示多個視圖的控制項示例包括清單視圖（可以將其內容顯示為縮略圖、磁貼、圖示或詳細資訊）、Microsoft Excel 圖表（圓形圖、行、橫條圖、帶公式的儲存格值）、Microsoft Word 文檔（普通、Web 佈局、列印）佈局、閱讀佈局、大綱）、微軟 Outlook 日曆（年、月、周、日）和微軟 Windows 媒體播放機外觀。 支援哪些檢視會由控制項的開發人員決定，而且是每個控制項所特有。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
 實作多重檢視控制項模式時，請注意下列方針和慣例：  
  
- 若管理目前檢視的容器與提供目前檢視的控制項不同，則也應在容器上實作<xref:System.Windows.Automation.Provider.IMultipleViewProvider> 。 例如，Windows 檔案總管包含目前資料夾內容的清單控制項，而控制項的檢視則是由 Windows 檔案總管應用程式管理。  
  
- 可以排序內容的控制項不視為支援多種檢視。  
  
- 檢視集合在執行個體之間必須完全相同。  
  
- 檢視名稱必須適用於文字轉換語音、點字以及其他人類看得懂的應用程式。  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a>IMultipleViewProvider 的必要成員  
 以下是實作 IMultipleViewProvider 的必要屬性和方法。  
  
|必要成員|成員類型|注意|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|屬性|None|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|方法|None|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|方法|None|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|方法|None|  
  
 這個控制項模式沒有相關事件。  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況型別|條件|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|呼叫 <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> 或 <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> 時使用的參數不是所支援檢視集合的成員。|  
  
## <a name="see-also"></a>另請參閱

- [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)
- [支援 UI 自動化提供者的控制項模式](support-control-patterns-in-a-ui-automation-provider.md)
- [用戶端的 UI 自動化控制項模式](ui-automation-control-patterns-for-clients.md)
- [UI Automation Tree Overview](ui-automation-tree-overview.md)
- [使用 UI 自動化中的快取](use-caching-in-ui-automation.md)
