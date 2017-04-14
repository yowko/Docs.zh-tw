---
title: "Get UI Automation Element Properties | Microsoft Docs"
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
  - "properties, retrieving"
  - "UI Automation, retrieving properties of elements"
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
caps.latest.revision: 5
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 5
---
# Get UI Automation Element Properties
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。  如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746) \(英文\)。  
  
 本主題說明如何擷取 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]項目的屬性。  
  
### 取得目前屬性值  
  
1.  取得想要其屬性的 <xref:System.Windows.Automation.AutomationElement>。  
  
2.  呼叫 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>，或擷取 <xref:System.Windows.Automation.AutomationElement.Current%2A> 屬性結構，然後從其中一個成員取得值。  
  
### 取得快取屬性值  
  
1.  取得想要其屬性的 <xref:System.Windows.Automation.AutomationElement>。  屬性必須已在 <xref:System.Windows.Automation.CacheRequest> 中指定。  
  
2.  呼叫 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>，或擷取 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 屬性結構，然後從其中一個成員取得值。  
  
## 範例  
 下列範例會示範擷取 <xref:System.Windows.Automation.AutomationElement> 目前屬性的不同方法。  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## 請參閱  
 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)   
 [Caching in UI Automation Clients](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)