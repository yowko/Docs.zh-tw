---
title: 使用 UI 自動化叫用控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 89e528e7ff3dbeeba30307adf83434b83f540221
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408320"
---
# <a name="invoke-a-control-using-ui-automation"></a>使用 UI 自動化叫用控制項
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題示範如何執行下列工作：  
  
-   藉由查核目標應用程式之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視，尋找符合特定屬性條件的控制項。  
  
-   建立每個控制項的 <xref:System.Windows.Automation.AutomationElement> 。  
  
-   從任何找到可支援 <xref:System.Windows.Automation.InvokePattern> 控制項模式的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目中，取得 <xref:System.Windows.Automation.InvokePattern> 物件。  
  
-   使用 <xref:System.Windows.Automation.InvokePattern.Invoke%2A> 以叫用來自用戶端事件處理常式的控制項。  
  
## <a name="example"></a>範例  
 此範例使用 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> 類別的 <xref:System.Windows.Automation.AutomationElement> 方法，產生 <xref:System.Windows.Automation.InvokePattern> 物件並利用 <xref:System.Windows.Automation.InvokePattern.Invoke%2A> 方法叫用控制項。  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>另請參閱  
 [InvokePattern 和 ExpandCollapsePattern 功能表項目範例](http://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
