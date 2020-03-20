---
title: 實作 UI 自動化 RangeValue 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 847a8aae3fd0c3d6965c910d19a4cec11cd2a3b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180173"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>實作 UI 自動化 RangeValue 控制項模式
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題將介紹實作 <xref:System.Windows.Automation.Provider.IRangeValueProvider>的方針和慣例，包括事件和屬性的相關資訊。 其他參考的連結列於主題的結尾。  
  
 <xref:System.Windows.Automation.RangeValuePattern> 控制項模式用來支援可以設定為某範圍內的值之控制項。 如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
 實作範圍值控制項模式時，請注意下列方針和慣例：  
  
- 控制項可以根據地區設定或使用者偏好設定，重新劃分所支援屬性的刻度。 例如，溫度計控制項可以設為顯示華氏或攝氏溫度。  
  
- 範圍值不明確的控制項 (如進度列或滑桿) 應將這些值正規化。  
  
 ![進度列。](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
進度列範例，其中的值屬於整數類型，而最小值和最大值的屬性值分別正規化為 0 和 100。  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a>IRangeValueProvider 的必要成員  
  
|必要成員|成員類型|注意|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|屬性|None|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|屬性|None|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|屬性|None|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|屬性|None|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|屬性|None|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|屬性|None|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|方法|None|  
  
 此控制項模式沒有任何相關聯的事件。  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況型別|條件|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> 以大於 <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> 或小於 <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>的值呼叫。|  
  
## <a name="see-also"></a>另請參閱

- [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)
- [支援 UI 自動化提供者的控制項模式](support-control-patterns-in-a-ui-automation-provider.md)
- [用戶端的 UI 自動化控制項模式](ui-automation-control-patterns-for-clients.md)
- [UI Automation Tree Overview](ui-automation-tree-overview.md)
- [使用 UI 自動化中的快取](use-caching-in-ui-automation.md)
