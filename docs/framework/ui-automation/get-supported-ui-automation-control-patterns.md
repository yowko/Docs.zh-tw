---
title: "取得支援的 UI 自動化控制項模式"
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
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: "10"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8917890d86f059d85ad9b6a0bcf6d9a41d65585a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="a1073-102">取得支援的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="a1073-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
>  <span data-ttu-id="a1073-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="a1073-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a1073-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="a1073-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a1073-105">本主題示範如何擷取控制項模式物件從[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]項目。</span><span class="sxs-lookup"><span data-stu-id="a1073-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="a1073-106">取得所有控制項模式</span><span class="sxs-lookup"><span data-stu-id="a1073-106">Obtain All Control Patterns</span></span>  
  
1.  <span data-ttu-id="a1073-107">取得<xref:System.Windows.Automation.AutomationElement>您對其控制項模式有興趣。</span><span class="sxs-lookup"><span data-stu-id="a1073-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="a1073-108">呼叫<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>來取得項目的所有控制項模式。</span><span class="sxs-lookup"><span data-stu-id="a1073-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a1073-109">強烈建議用戶端未使用<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>。</span><span class="sxs-lookup"><span data-stu-id="a1073-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="a1073-110">可以被嚴重影響效能，因為這個方法會呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>在內部針對每個現有的控制項模式。</span><span class="sxs-lookup"><span data-stu-id="a1073-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="a1073-111">可能的話，用戶端應該呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>針對感興趣的重要模式。</span><span class="sxs-lookup"><span data-stu-id="a1073-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="a1073-112">取得特定的控制項模式</span><span class="sxs-lookup"><span data-stu-id="a1073-112">Obtain a Specific Control Pattern</span></span>  
  
1.  <span data-ttu-id="a1073-113">取得<xref:System.Windows.Automation.AutomationElement>您對其控制項模式有興趣。</span><span class="sxs-lookup"><span data-stu-id="a1073-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="a1073-114">呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>或<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>以查詢特定模式。</span><span class="sxs-lookup"><span data-stu-id="a1073-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="a1073-115">這些方法很相似，但是，如果找不到模式，<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>引發例外狀況，以及<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="a1073-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1073-116">範例</span><span class="sxs-lookup"><span data-stu-id="a1073-116">Example</span></span>  
 <span data-ttu-id="a1073-117">下列範例會擷取<xref:System.Windows.Automation.AutomationElement>清單項目，並取得<xref:System.Windows.Automation.SelectionItemPattern>從該項目。</span><span class="sxs-lookup"><span data-stu-id="a1073-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="a1073-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1073-118">See Also</span></span>  
 [<span data-ttu-id="a1073-119">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="a1073-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
