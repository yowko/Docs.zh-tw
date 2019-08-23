---
title: 取得支援的 UI 自動化控制項模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 8987526a572d3c9a239885407c19bd1ad3674f0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968985"
---
# <a name="get-supported-ui-automation-control-patterns"></a>取得支援的 UI 自動化控制項模式
> [!NOTE]
> 這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。  
  
 本主題顯示如何從 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目擷取控制項模式物件。  
  
### <a name="obtain-all-control-patterns"></a>取得所有控制項模式  
  
1. 取得您對其控制項模式有興趣的 <xref:System.Windows.Automation.AutomationElement>。  
  
2. 呼叫 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> 以取得項目的所有控制項模式。  
  
> [!CAUTION]
>  強烈建議用戶端不要使用 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>。 可能會嚴重影響效能，因為這個方法會在內部針對每個現有的控制項模式呼叫 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>。 可能的話，用戶端應該針對感興趣的重要模式呼叫 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>。  
  
### <a name="obtain-a-specific-control-pattern"></a>取得特定的控制項模式  
  
1. 取得您對其控制項模式有興趣的 <xref:System.Windows.Automation.AutomationElement>。  
  
2. 呼叫 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> 或 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> 以查詢特定模式。 這些方法很相似，但如果找不到模式，<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> 會引發例外狀況，且 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> 會傳回 `false`。  
  
## <a name="example"></a>範例  
 下列範例會擷取清單項目的 <xref:System.Windows.Automation.AutomationElement>，並從該項目取得 <xref:System.Windows.Automation.SelectionItemPattern>。  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>另請參閱

- [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
