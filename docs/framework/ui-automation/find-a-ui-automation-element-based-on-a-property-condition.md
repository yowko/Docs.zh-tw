---
title: 根據屬性條件尋找 UI 自動化項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 3ca609551955b32ad8b63296975ce10f097d9c30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433595"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>根據屬性條件尋找 UI 自動化項目
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題包含範例程式碼，示範如何根據特定的屬性或屬性，在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中尋找元素。  
  
## <a name="example"></a>範例  
 在下列範例中，會指定一組屬性條件，以識別 <xref:System.Windows.Automation.AutomationElement> 樹狀目錄中感興趣的特定專案（或元素）。 接著會使用 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 方法來搜尋所有相符的專案，其中包含一系列 <xref:System.Windows.Automation.AndCondition> 的布耳運算，以限制相符的元素數目。  
  
> [!NOTE]
> 從 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>搜尋時，您應該嘗試只取得直接子系。 搜尋子代可能會逐一查看數百個或甚至數千個專案，可能會導致堆疊溢位。 如果您嘗試取得較低層級的特定項目，您就應該要從應用程式視窗或較低層級的容器開始搜尋。  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>另請參閱

- [InvokePattern 和 ExpandCollapsePattern 功能表項目範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))
- [Obtaining UI Automation Elements](obtaining-ui-automation-elements.md)
- [使用 AutomationID 屬性](use-the-automationid-property.md)
