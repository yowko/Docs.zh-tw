---
title: 取得支援的 UI 自動化控制項模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 133dabe861fbbcf5cac3fbb8669b78e582f8b87b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043652"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="2f8e2-102">取得支援的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="2f8e2-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
> <span data-ttu-id="2f8e2-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2f8e2-104">如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="2f8e2-105">本主題顯示如何從 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目擷取控制項模式物件。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="2f8e2-106">取得所有控制項模式</span><span class="sxs-lookup"><span data-stu-id="2f8e2-106">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="2f8e2-107">取得您對其控制項模式有興趣的 <xref:System.Windows.Automation.AutomationElement>。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="2f8e2-108">呼叫 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> 以取得項目的所有控制項模式。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="2f8e2-109">強烈建議用戶端不要使用 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="2f8e2-110">可能會嚴重影響效能，因為這個方法會在內部針對每個現有的控制項模式呼叫 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="2f8e2-111">可能的話，用戶端應該針對感興趣的重要模式呼叫 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="2f8e2-112">取得特定的控制項模式</span><span class="sxs-lookup"><span data-stu-id="2f8e2-112">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="2f8e2-113">取得您對其控制項模式有興趣的 <xref:System.Windows.Automation.AutomationElement>。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="2f8e2-114">呼叫 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> 或 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> 以查詢特定模式。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="2f8e2-115">這些方法很相似，但如果找不到模式，<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> 會引發例外狀況，且 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> 會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f8e2-116">範例</span><span class="sxs-lookup"><span data-stu-id="2f8e2-116">Example</span></span>  
 <span data-ttu-id="2f8e2-117">下列範例會擷取清單項目的 <xref:System.Windows.Automation.AutomationElement>，並從該項目取得 <xref:System.Windows.Automation.SelectionItemPattern>。</span><span class="sxs-lookup"><span data-stu-id="2f8e2-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="2f8e2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f8e2-118">See also</span></span>

- [<span data-ttu-id="2f8e2-119">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="2f8e2-119">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
