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
ms.openlocfilehash: 158ebf29bb504dd11f9e8416011226fc5846873e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043619"
---
# <a name="get-ui-automation-element-properties"></a>取得 UI 自動化項目屬性
> [!NOTE]
> 這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。  
  
 本主題說明如何抓取[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]元素的屬性。  
  
### <a name="get-a-current-property-value"></a>取得目前的屬性值  
  
1. 取得您<xref:System.Windows.Automation.AutomationElement>想要取得其屬性的。  
  
2. 呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>或<xref:System.Windows.Automation.AutomationElement.Current%2A>取出屬性結構，並從它的其中一個成員取得值。  
  
### <a name="get-a-cached-property-value"></a>取得快取的屬性值  
  
1. 取得您<xref:System.Windows.Automation.AutomationElement>想要取得其屬性的。 屬性必須已在中<xref:System.Windows.Automation.CacheRequest>指定。  
  
2. 呼叫<xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>或<xref:System.Windows.Automation.AutomationElement.Cached%2A>取出屬性結構，並從它的其中一個成員取得值。  
  
## <a name="example"></a>範例  
 下列範例示範各種可取得之目前屬性的<xref:System.Windows.Automation.AutomationElement>方式。  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>另請參閱

- [用戶端的 UI 自動化屬性](ui-automation-properties-for-clients.md)
- [在 UI 自動化中使用快取](use-caching-in-ui-automation.md)
- [UI 自動化用戶端中的快取](caching-in-ui-automation-clients.md)
