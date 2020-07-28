---
title: 取得 UI 自動化項目屬性
description: 請參閱指示和範例，其中顯示如何取得使用者介面自動化專案的目前或快取屬性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 277822c9d89046bfbad50df16bce83da7dd45b3b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164111"
---
# <a name="get-ui-automation-element-properties"></a>取得 UI 自動化項目屬性
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題說明如何抓取元素的屬性 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。  
  
### <a name="get-a-current-property-value"></a>取得目前的屬性值  
  
1. 取得 <xref:System.Windows.Automation.AutomationElement> 您想要取得其屬性的。  
  
2. 呼叫 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> 或取出 <xref:System.Windows.Automation.AutomationElement.Current%2A> 屬性結構，並從它的其中一個成員取得值。  
  
### <a name="get-a-cached-property-value"></a>取得快取的屬性值  
  
1. 取得 <xref:System.Windows.Automation.AutomationElement> 您想要取得其屬性的。 屬性必須已在中指定 <xref:System.Windows.Automation.CacheRequest> 。  
  
2. 呼叫 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> 或取出 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 屬性結構，並從它的其中一個成員取得值。  
  
## <a name="example"></a>範例  
 下列範例示範各種可取得之目前屬性的方式 <xref:System.Windows.Automation.AutomationElement> 。  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>另請參閱

- [用戶端的 UI 自動化屬性](ui-automation-properties-for-clients.md)
- [使用 UI 自動化中的快取](use-caching-in-ui-automation.md)
- [UI 自動化用戶端中的快取](caching-in-ui-automation-clients.md)
