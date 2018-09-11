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
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44341731"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="b89a3-102">使用 TreeWalker 巡覽 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="b89a3-102">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
>  <span data-ttu-id="b89a3-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="b89a3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b89a3-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="b89a3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b89a3-105">本主題包含範例程式碼，示範如何瀏覽[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]使用的項目<xref:System.Windows.Automation.TreeWalker>類別。</span><span class="sxs-lookup"><span data-stu-id="b89a3-105">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b89a3-106">範例</span><span class="sxs-lookup"><span data-stu-id="b89a3-106">Example</span></span>  
 <span data-ttu-id="b89a3-107">下列範例會使用<xref:System.Windows.Automation.TreeWalker.GetParent%2A>可向上查看[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]樹狀目錄，直到它找到的根項目或桌面。</span><span class="sxs-lookup"><span data-stu-id="b89a3-107">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="b89a3-108">正下方的項目是指定之項目的父視窗。</span><span class="sxs-lookup"><span data-stu-id="b89a3-108">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="b89a3-109">範例</span><span class="sxs-lookup"><span data-stu-id="b89a3-109">Example</span></span>  
 <span data-ttu-id="b89a3-110">下列範例會使用<xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A>並<xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A>來建立<xref:System.Windows.Forms.TreeView>，以顯示整個子樹的[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]項目中的控制項檢視和已啟用的。</span><span class="sxs-lookup"><span data-stu-id="b89a3-110">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="b89a3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b89a3-111">See Also</span></span>  
 [<span data-ttu-id="b89a3-112">取得 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="b89a3-112">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
