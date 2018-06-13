---
title: 用戶端的 UI 自動化控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d3ec88eb1054c4cc14f01320c85924c9ca346361
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398803"
---
# <a name="ui-automation-control-patterns-for-clients"></a>用戶端的 UI 自動化控制項模式
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本概觀介紹使用者介面自動化用戶端的控制項模式。 其中所包含的資訊，與使用者介面自動化用戶端使用控制項模式來存取 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]相關資訊之方式有關。  
  
 控制項模式提供一種方式，分類及公開與控制項類型或控制項外觀無關的控制項功能。 使用者介面自動化用戶端可檢查 <xref:System.Windows.Automation.AutomationElement> 來判斷支援哪些控制項模式，及保證控制項的行為。  
  
 如需控制項模式的完整清單，請參閱 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)。  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>取得控制項模式  
 用戶端藉由呼叫 <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>，從 <xref:System.Windows.Automation.AutomationElement> 擷取控制項模式。  
  
 用戶端可以使用 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> 方法或個別的 `IsPatternAvailable` 屬性 (例如， <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) 來判斷 <xref:System.Windows.Automation.AutomationElement>上是否支援模式或模式群組。 不過，嘗試取得控制項模式和針對 `null` 參考進行測試，比檢查支援的屬性並擷取控制項模式更有效率，因為它會造成較少的跨處理序呼叫。  
  
 下列範例示範如何從 <xref:System.Windows.Automation.TextPattern> 取得 <xref:System.Windows.Automation.AutomationElement>控制項模式。  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>在控制項模式上擷取屬性  
 用戶端可藉由呼叫 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType>，並將物件轉型成傳回適當的類型，藉此在控制項模式上擷取屬性值。 如需有關[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]屬性，請參閱[用戶端的使用者介面自動化屬性](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)。  
  
 除了 `GetPropertyValue` 方法，可以透過 [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] 存取子來擷取屬性值，以存取模式上的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 屬性。  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>包含變數模式的控制項  
 某些控制項類型支援不同的模式，視其狀態或使用控制項的方式而定。 可以具有變數模式的控制項範例有清單檢視 (縮圖、圖格、圖示、清單、詳細資料)、 [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] 圖表 (圓形圖、折線圖、橫條圖、包含公式的資料格值)、 [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]的文件區域 (一般、Web 版面配置、大綱、列印版面配置、預覽列印) 和 [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] 面板。  
  
 實作自訂控制項類型的控制項可以有任何控制項模式組合，它們是代表其功能所需的組合。  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)  
 [使用者介面自動化文字模式](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)  
 [使用 UI 自動化叫用控制項](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [使用 UI 自動化取得核取方塊的切換狀態](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [UI 自動化用戶端的控制項模式對應](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [TextPattern 插入文字範例](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [TextPattern 搜尋和選取範例](http://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)  
 [InvokePattern 和 ExpandCollapsePattern 功能表項目範例](http://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
