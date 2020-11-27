---
title: 尋找清單項目的 UI 自動化項目
description: 若要瞭解如何在已知專案的索引時尋找清單專案的消費者介面自動化專案，請參閱範例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 95f6b558cc53b00701232f247f8de7f8c603e3ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276473"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="44e9c-103">尋找清單項目的 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="44e9c-103">Find a UI Automation Element for a List Item</span></span>

> [!NOTE]
> <span data-ttu-id="44e9c-104">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="44e9c-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="44e9c-105">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="44e9c-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="44e9c-106">本主題說明如何在 <xref:System.Windows.Automation.AutomationElement> 已知專案的索引時，針對清單中的專案取得。</span><span class="sxs-lookup"><span data-stu-id="44e9c-106">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44e9c-107">範例</span><span class="sxs-lookup"><span data-stu-id="44e9c-107">Example</span></span>  

 <span data-ttu-id="44e9c-108">下列範例示範兩種從清單中取出指定專案的方式，一個使用， <xref:System.Windows.Automation.TreeWalker> 另一個使用 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 。</span><span class="sxs-lookup"><span data-stu-id="44e9c-108">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="44e9c-109">第一個技巧對 Win32 控制項來說可能比較快，但第二個技巧更快 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="44e9c-109">The first technique tends to be faster for Win32 controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="44e9c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44e9c-110">See also</span></span>

- [<span data-ttu-id="44e9c-111">取得 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="44e9c-111">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
