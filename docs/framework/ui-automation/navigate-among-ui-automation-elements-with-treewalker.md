---
title: 使用 TreeWalker 巡覽 UI 自動化項目
description: 請參閱程式碼範例，示範如何使用 TreeWalker 類別在消費者介面自動化專案之間流覽。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: e102e6ce258bef06d1fb44decfa1a3a27384e0bc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261211"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a>使用 TreeWalker 巡覽 UI 自動化項目

> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題包含範例程式碼，示範如何使用類別在元素之間進行導覽 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <xref:System.Windows.Automation.TreeWalker> 。  
  
## <a name="example"></a>範例  

 下列範例會使用 <xref:System.Windows.Automation.TreeWalker.GetParent%2A> 來向上查閱 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 樹狀結構，直到找到根項目或 desktop 為止。 緊接在其下方的元素是指定之專案的父視窗。  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a>範例  

 下列範例會使用 <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> 和 <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> 來建立 <xref:System.Windows.Forms.TreeView> ，其 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 會顯示控制項和已啟用之元素的整個子樹。  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a>另請參閱

- [取得 UI 自動化項目](obtaining-ui-automation-elements.md)
