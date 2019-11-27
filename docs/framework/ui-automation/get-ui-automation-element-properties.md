---
title: 取得 UI 自動化項目屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 1b82302ff89d2e8407871cbfba6c10e8322ac4e7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435506"
---
# <a name="get-ui-automation-element-properties"></a>取得 UI 自動化項目屬性
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題說明如何抓取 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 元素的屬性。  
  
### <a name="get-a-current-property-value"></a>取得目前的屬性值  
  
1. 取得您想要取得其屬性的 <xref:System.Windows.Automation.AutomationElement>。  
  
2. 呼叫 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>，或取出 <xref:System.Windows.Automation.AutomationElement.Current%2A> 屬性結構，並從它的其中一個成員取得值。  
  
### <a name="get-a-cached-property-value"></a>取得快取的屬性值  
  
1. 取得您想要取得其屬性的 <xref:System.Windows.Automation.AutomationElement>。 屬性必須已在 <xref:System.Windows.Automation.CacheRequest>中指定。  
  
2. 呼叫 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>，或取出 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 屬性結構，並從它的其中一個成員取得值。  
  
## <a name="example"></a>範例  
 下列範例示範各種方式，以取得 <xref:System.Windows.Automation.AutomationElement>的目前屬性。  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>請參閱

- [UI Automation Properties for Clients](ui-automation-properties-for-clients.md)
- [在 UI 自動化中使用快取](use-caching-in-ui-automation.md)
- [Caching in UI Automation Clients](caching-in-ui-automation-clients.md)
