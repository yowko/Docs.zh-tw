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
ms.openlocfilehash: 536a71532f02782f9e84bb2bd086af212a77c0da
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043671"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>根據屬性條件尋找 UI 自動化項目
> [!NOTE]
> 這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。  
  
 本主題包含範例程式碼，示範如何根據特定的屬性或[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]屬性找出樹狀結構內的專案。  
  
## <a name="example"></a>範例  
 在下列範例中，會指定一組屬性條件，以識別<xref:System.Windows.Automation.AutomationElement>樹狀結構中感興趣的特定專案（或元素）。 接著會使用<xref:System.Windows.Automation.AutomationElement.FindAll%2A>併入一<xref:System.Windows.Automation.AndCondition>系列布耳運算的方法來執行所有相符專案的搜尋，以限制相符元素的數目。  
  
> [!NOTE]
> 從搜尋時<xref:System.Windows.Automation.AutomationElement.RootElement%2A>，您應該只嘗試取得直接子系。 搜尋子代可能會逐一查看數百個或甚至數千個專案，可能會導致堆疊溢位。 如果您嘗試取得較低層級的特定項目，您就應該要從應用程式視窗或較低層級的容器開始搜尋。  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>另請參閱

- [InvokePattern 和 ExpandCollapsePattern 功能表項目範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))
- [取得 UI 自動化項目](obtaining-ui-automation-elements.md)
- [使用 AutomationID 屬性](use-the-automationid-property.md)
