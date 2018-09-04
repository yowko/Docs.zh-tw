---
title: 使用 TreeWalker 巡覽 UI 自動化項目
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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 6a44cd16513bffa47e56064ea7e0e05692cb78a7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659938"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a>使用 TreeWalker 巡覽 UI 自動化項目
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題包含範例程式碼，示範如何瀏覽[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]使用的項目<xref:System.Windows.Automation.TreeWalker>類別。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Automation.TreeWalker.GetParent%2A>可向上查看[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]樹狀目錄，直到它找到的根項目或桌面。 正下方的項目是指定之項目的父視窗。  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A>並<xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A>來建立<xref:System.Windows.Forms.TreeView>，以顯示整個子樹的[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]項目中的控制項檢視和已啟用的。  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a>另請參閱  
 [取得 UI 自動化項目](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
