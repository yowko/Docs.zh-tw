---
title: 使用 TreeWalker 巡覽 UI 自動化項目
description: 請參閱程式碼範例，示範如何使用 TreeWalker 類別，在使用者介面自動化專案之間流覽。
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
ms.openlocfilehash: e1784862433083f15d600ea2ec39aee2323bbd12
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168022"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="0b9d5-103">使用 TreeWalker 巡覽 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="0b9d5-103">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
> <span data-ttu-id="0b9d5-104">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="0b9d5-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0b9d5-105">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="0b9d5-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="0b9d5-106">本主題包含範例程式碼，說明如何使用類別在專案之間流覽 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <xref:System.Windows.Automation.TreeWalker> 。</span><span class="sxs-lookup"><span data-stu-id="0b9d5-106">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b9d5-107">範例</span><span class="sxs-lookup"><span data-stu-id="0b9d5-107">Example</span></span>  
 <span data-ttu-id="0b9d5-108">下列範例會使用 <xref:System.Windows.Automation.TreeWalker.GetParent%2A> 來向上流覽 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 樹狀結構，直到找到根項目或 desktop 為止。</span><span class="sxs-lookup"><span data-stu-id="0b9d5-108">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="0b9d5-109">緊接在下面的專案是指定專案的父視窗。</span><span class="sxs-lookup"><span data-stu-id="0b9d5-109">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="0b9d5-110">範例</span><span class="sxs-lookup"><span data-stu-id="0b9d5-110">Example</span></span>  
 <span data-ttu-id="0b9d5-111">下列範例會使用 <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> 和 <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> 來建立 <xref:System.Windows.Forms.TreeView> ，其 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 會顯示在控制項視圖中且已啟用的整個專案子樹。</span><span class="sxs-lookup"><span data-stu-id="0b9d5-111">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="0b9d5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b9d5-112">See also</span></span>

- [<span data-ttu-id="0b9d5-113">取得 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="0b9d5-113">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
