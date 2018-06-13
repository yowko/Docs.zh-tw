---
title: 尋找清單項目的 UI 自動化項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4813f5c9485c819a22a1598e869304d2534c85bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399986"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="867c1-102">尋找清單項目的 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="867c1-102">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
>  <span data-ttu-id="867c1-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="867c1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="867c1-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="867c1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="867c1-105">本主題示範如何擷取<xref:System.Windows.Automation.AutomationElement>時已知的項目索引的清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="867c1-105">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="867c1-106">範例</span><span class="sxs-lookup"><span data-stu-id="867c1-106">Example</span></span>  
 <span data-ttu-id="867c1-107">下列範例示範兩個方式來擷取指定的項目從清單中，另一個使用<xref:System.Windows.Automation.TreeWalker>及其他使用<xref:System.Windows.Automation.AutomationElement.FindAll%2A>。</span><span class="sxs-lookup"><span data-stu-id="867c1-107">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="867c1-108">第一種技術往往會有更快，[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]控制項，但第二個是更快，Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="867c1-108">The first technique tends to be faster for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="867c1-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="867c1-109">See Also</span></span>  
 [<span data-ttu-id="867c1-110">取得 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="867c1-110">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
