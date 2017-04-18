---
title: "Navigate Among UI Automation Elements with TreeWalker | Microsoft Docs"
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
  - "classes, TreeWalker"
  - "TreeWalker class"
  - "elements, navigating among"
  - "UI Automation, navigating among elements"
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
caps.latest.revision: 8
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 8
---
# Navigate Among UI Automation Elements with TreeWalker
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。  如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746) \(英文\)。  
  
 本主題內含範例程式碼，說明如何使用 <xref:System.Windows.Automation.TreeWalker> 類別以巡覽 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]項目。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Automation.TreeWalker.GetParent%2A> 向上查核 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]樹狀目錄直到找到根項目或找到桌面為止。  而在該位置之下的項目，就是所指定項目之的視窗。  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## 範例  
 下列範例使用 <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> 及 <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> 以建立 <xref:System.Windows.Forms.TreeView>，顯示控制項檢視中已啟用之 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]項目的整個樹狀子目錄。  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## 請參閱  
 [Obtaining UI Automation Elements](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)