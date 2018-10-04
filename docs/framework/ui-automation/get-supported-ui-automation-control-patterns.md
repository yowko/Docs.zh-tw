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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: d948ff2f71ff7d4335cacc0fa3815dd75af4ad45
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778230"
---
# <a name="get-supported-ui-automation-control-patterns"></a>取得支援的 UI 自動化控制項模式
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題示範如何擷取控制項模式物件從[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]項目。  
  
### <a name="obtain-all-control-patterns"></a>取得所有控制項模式  
  
1.  取得<xref:System.Windows.Automation.AutomationElement>其控制項模式，您有興趣。  
  
2.  呼叫<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>從項目中取得所有控制項模式。  
  
> [!CAUTION]
>  強烈建議的用戶端不使用<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>。 可能會嚴重影響效能，這個方法會呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>在內部針對每個現有的控制項模式。 可能的話，用戶端應該呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>感興趣的索引鍵的模式。  
  
### <a name="obtain-a-specific-control-pattern"></a>取得特定的控制項模式  
  
1.  取得<xref:System.Windows.Automation.AutomationElement>其控制項模式，您有興趣。  
  
2.  呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>或<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>特定模式的查詢。 這些方法很相似，但是，如果找不到模式，<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>引發例外狀況，並<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>傳回`false`。  
  
## <a name="example"></a>範例  
 下列範例會擷取<xref:System.Windows.Automation.AutomationElement>的清單項目，並取得<xref:System.Windows.Automation.SelectionItemPattern>從該項目。  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>另請參閱  
 [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
