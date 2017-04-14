---
title: "取得支援的 UI 自動化控制項模式 | Microsoft Docs"
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
  - "取得控制項模式"
  - "UI 自動化中，取得控制項模式"
  - "取得控制項模式"
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: 10
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 10
---
# 取得支援的 UI 自動化控制項模式
> [!NOTE]
>  這份文件適用於.NET Framework 開發人員想要使用 managed[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中定義的類別<xref:System.Windows.Automation>命名空間。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API: UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題說明如何擷取控制項模式的物件從[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]項目。  
  
### <a name="obtain-all-control-patterns"></a>取得所有控制項模式  
  
1.  取得<xref:System.Windows.Automation.AutomationElement>的控制項模式您所感興趣。  
  
2.  呼叫<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>以取得所有的控制項模式從項目。  
  
> [!CAUTION]
>  強烈建議使用的用戶端不使用<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>。 可能會嚴重影響效能，這個方法會呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>在內部針對每個現有的控制項模式。 可能的話，應該呼叫用戶端<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>感興趣的索引鍵的模式。  
  
### <a name="obtain-a-specific-control-pattern"></a>取得特定的控制項模式  
  
1.  取得<xref:System.Windows.Automation.AutomationElement>的控制項模式您所感興趣。  
  
2.  呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>或<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>特定模式的查詢。 這些方法很類似，但是，如果找不到模式， <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>引發例外狀況，以及<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>傳回`false`。  
  
## <a name="example"></a>範例  
 下列範例會擷取<xref:System.Windows.Automation.AutomationElement>清單項目，並取得<xref:System.Windows.Automation.SelectionItemPattern>從該項目。  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>另請參閱  
 [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)