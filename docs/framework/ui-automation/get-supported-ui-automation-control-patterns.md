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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: d948ff2f71ff7d4335cacc0fa3815dd75af4ad45
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231373"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="b2d86-102">取得支援的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="b2d86-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
>  <span data-ttu-id="b2d86-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="b2d86-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b2d86-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="b2d86-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b2d86-105">本主題示範如何擷取控制項模式物件從[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]項目。</span><span class="sxs-lookup"><span data-stu-id="b2d86-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="b2d86-106">取得所有控制項模式</span><span class="sxs-lookup"><span data-stu-id="b2d86-106">Obtain All Control Patterns</span></span>  
  
1.  <span data-ttu-id="b2d86-107">取得<xref:System.Windows.Automation.AutomationElement>其控制項模式，您有興趣。</span><span class="sxs-lookup"><span data-stu-id="b2d86-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="b2d86-108">呼叫<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>從項目中取得所有控制項模式。</span><span class="sxs-lookup"><span data-stu-id="b2d86-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b2d86-109">強烈建議的用戶端不使用<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>。</span><span class="sxs-lookup"><span data-stu-id="b2d86-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="b2d86-110">可能會嚴重影響效能，這個方法會呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>在內部針對每個現有的控制項模式。</span><span class="sxs-lookup"><span data-stu-id="b2d86-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="b2d86-111">可能的話，用戶端應該呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>感興趣的索引鍵的模式。</span><span class="sxs-lookup"><span data-stu-id="b2d86-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="b2d86-112">取得特定的控制項模式</span><span class="sxs-lookup"><span data-stu-id="b2d86-112">Obtain a Specific Control Pattern</span></span>  
  
1.  <span data-ttu-id="b2d86-113">取得<xref:System.Windows.Automation.AutomationElement>其控制項模式，您有興趣。</span><span class="sxs-lookup"><span data-stu-id="b2d86-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="b2d86-114">呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>或<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>特定模式的查詢。</span><span class="sxs-lookup"><span data-stu-id="b2d86-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="b2d86-115">這些方法很相似，但是，如果找不到模式，<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>引發例外狀況，並<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="b2d86-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2d86-116">範例</span><span class="sxs-lookup"><span data-stu-id="b2d86-116">Example</span></span>  
 <span data-ttu-id="b2d86-117">下列範例會擷取<xref:System.Windows.Automation.AutomationElement>的清單項目，並取得<xref:System.Windows.Automation.SelectionItemPattern>從該項目。</span><span class="sxs-lookup"><span data-stu-id="b2d86-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="b2d86-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2d86-118">See Also</span></span>  
 [<span data-ttu-id="b2d86-119">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="b2d86-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
