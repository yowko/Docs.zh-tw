---
title: "Find a UI Automation Element Based on a Property Condition | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "elements, finding by property conditions"
  - "UI Automation, finding elements by property conditions"
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
caps.latest.revision: 19
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 19
---
# Find a UI Automation Element Based on a Property Condition
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。  如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746) \(英文\)。  
  
 本主題內含範例程式碼，說明如何根據一個或多個特定屬性尋找 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀目錄中的項目。  
  
## 範例  
 在下列範例中，會指定一組可以識別 <xref:System.Windows.Automation.AutomationElement> 樹狀目錄中一個或多個所需特定項目的屬性條件。  然後使用 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 方法來搜尋所有相符項目，這個方法會加上一連串 <xref:System.Windows.Automation.AndCondition> 布林運算以限制相符項目數目。  
  
> [!NOTE]
>  從 <xref:System.Windows.Automation.AutomationElement.RootElement%2A> 搜尋時，您應嘗試只取得直接子系。  如果搜尋子代，可能會逐一查看數百，甚至數千個項目，因而造成堆疊溢位。  如果您嘗試取得較低層級的特定項目，則應該從應用程式視窗或較低層級的容器開始搜尋。  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## 請參閱  
 [InvokePattern and ExpandCollapsePattern Menu Item Sample](http://msdn.microsoft.com/zh-tw/b7fa141c-e2d1-4da2-a27f-81a7d1172210)   
 [Obtaining UI Automation Elements](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)   
 [Use the AutomationID Property](../../../docs/framework/ui-automation/use-the-automationid-property.md)