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
ms.openlocfilehash: 4cc4c976f8e9eb7f1779139f8266e22477d269e4
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673765"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="4241a-102">尋找清單項目的 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="4241a-102">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
>  <span data-ttu-id="4241a-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="4241a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4241a-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="4241a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4241a-105">本主題示範如何擷取<xref:System.Windows.Automation.AutomationElement>已知的項目索引時，在清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="4241a-105">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4241a-106">範例</span><span class="sxs-lookup"><span data-stu-id="4241a-106">Example</span></span>  
 <span data-ttu-id="4241a-107">下列範例顯示兩個方式來擷取指定的項目從清單中，使用<xref:System.Windows.Automation.TreeWalker>及其他使用<xref:System.Windows.Automation.AutomationElement.FindAll%2A>。</span><span class="sxs-lookup"><span data-stu-id="4241a-107">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="4241a-108">第一個技巧通常是快速[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]控制項，但是第二個是針對 Windows Presentation Foundation (WPF) 控制項，更快。</span><span class="sxs-lookup"><span data-stu-id="4241a-108">The first technique tends to be faster for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="4241a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4241a-109">See also</span></span>
- [<span data-ttu-id="4241a-110">取得 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="4241a-110">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
