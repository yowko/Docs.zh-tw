---
title: "尋找清單項目的 UI 自動化項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
caps.latest.revision: "5"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 16016f5e5b0ab9633f9f8e4ac662838dd7936b18
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>尋找清單項目的 UI 自動化項目
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題示範如何擷取<xref:System.Windows.Automation.AutomationElement>時已知的項目索引的清單中的項目。  
  
## <a name="example"></a>範例  
 下列範例示範兩個方式來擷取指定的項目從清單中，另一個使用<xref:System.Windows.Automation.TreeWalker>及其他使用<xref:System.Windows.Automation.AutomationElement.FindAll%2A>。  
  
 第一種技術往往會有更快，[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]控制項，但第二個就會比較快[!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)]控制項。  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>另請參閱  
 [取得 UI 自動化項目](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
