---
title: 實作 UI 自動化 Value 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: b9c748ccc695ae67306c293c10248c4f3f22c043
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>實作 UI 自動化 Value 控制項模式
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題將介紹實作 <xref:System.Windows.Automation.Provider.IValueProvider>的方針和慣例，包括事件和屬性的相關資訊。 其他參考的連結列於主題的結尾。  
  
 <xref:System.Windows.Automation.ValuePattern> 控制項模式用來支援不跨越某個範圍的內建值且可以表示為字串的控制項。 這個字串可以是可編輯的，視控制項及其設定而定。 如需實作此模式的控制項範例，請參閱 [T:System.Windows.Automation.Provider.IValueProvider](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
 實作值控制項模式時，請注意下列方針和慣例：  
  
-   如果任何項目的值是可編輯的，則例如 <xref:System.Windows.Automation.ControlType.ListItem> 和 <xref:System.Windows.Automation.ControlType.TreeItem> 等控制項必須支援 <xref:System.Windows.Automation.ValuePattern> ，而不論控制項目前的編輯模式為何。 如果子項目是可編輯的，父控制項也必須支援 <xref:System.Windows.Automation.ValuePattern> 。  
  
 ![可編輯的清單項目。] (../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
可編輯的清單項目範例  
  
-   單行編輯控制項支援藉由實作 <xref:System.Windows.Automation.Provider.IValueProvider>，以程式設計方式存取其內容。 不過，多行編輯控制項不會實作 <xref:System.Windows.Automation.Provider.IValueProvider>；它們是改為藉由實作 <xref:System.Windows.Automation.Provider.ITextProvider>來提供其內容的存取。  
  
-   若要擷取多行編輯控制項的文字內容，控制項必須實作 <xref:System.Windows.Automation.Provider.ITextProvider>。 不過， <xref:System.Windows.Automation.Provider.ITextProvider> 不支援設定控制項的值。  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> 不支援擷取格式設定資訊或子字串值。 在這些案例中請實作 <xref:System.Windows.Automation.Provider.ITextProvider> 。  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> 必須由例如來自 **F:System.Windows.Automation.ValuePattern.IsReadOnlyProperty** 的色彩選擇器 [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] 選擇控制項等控制項實作 (下面詳述)，它可支援色彩值 (例如「黃色」) 和對等內部 [!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)] 結構之間的字串對應。  
  
 ![反白顯示黃色的色彩選擇器。] (../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
色樣字串對應範例  
  
-   控制項的 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 應該設為 `true` ， <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 應該設為 `false` ，才能允許呼叫 <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>IValueProvider 的必要成員  
 以下是實作 <xref:System.Windows.Automation.Provider.IValueProvider>的必要屬性和方法。  
  
|必要成員|成員類型|注意|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|屬性|無|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|屬性|無|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|方法|無|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況類型|條件|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -如果地區設定特有的資訊會傳遞至例如格式不正確的日期格式不正確的控制項。|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -如果新的值不能從字串轉換成格式可辨識的控制項。|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -當嘗試對管理未啟用的控制項。|  
  
## <a name="see-also"></a>另請參閱  
 [UI 自動化控制項模式概觀](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [支援 UI 自動化提供者的控制項模式](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [TextPattern 插入文字範例](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [UI 自動化樹狀目錄概觀](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [在 UI 自動化中使用快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
