---
title: 取得 UI 自動化項目屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: e3b3b118c3db95f55c67c2b27149734efc8cbea8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968958"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="a77aa-102">取得 UI 自動化項目屬性</span><span class="sxs-lookup"><span data-stu-id="a77aa-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="a77aa-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="a77aa-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a77aa-104">如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。</span><span class="sxs-lookup"><span data-stu-id="a77aa-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a77aa-105">本主題說明如何抓取[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="a77aa-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="a77aa-106">取得目前的屬性值</span><span class="sxs-lookup"><span data-stu-id="a77aa-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="a77aa-107">取得您<xref:System.Windows.Automation.AutomationElement>想要取得其屬性的。</span><span class="sxs-lookup"><span data-stu-id="a77aa-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="a77aa-108">呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>或<xref:System.Windows.Automation.AutomationElement.Current%2A>取出屬性結構, 並從它的其中一個成員取得值。</span><span class="sxs-lookup"><span data-stu-id="a77aa-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="a77aa-109">取得快取的屬性值</span><span class="sxs-lookup"><span data-stu-id="a77aa-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="a77aa-110">取得您<xref:System.Windows.Automation.AutomationElement>想要取得其屬性的。</span><span class="sxs-lookup"><span data-stu-id="a77aa-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="a77aa-111">屬性必須已在中<xref:System.Windows.Automation.CacheRequest>指定。</span><span class="sxs-lookup"><span data-stu-id="a77aa-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="a77aa-112">呼叫<xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>或<xref:System.Windows.Automation.AutomationElement.Cached%2A>取出屬性結構, 並從它的其中一個成員取得值。</span><span class="sxs-lookup"><span data-stu-id="a77aa-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a77aa-113">範例</span><span class="sxs-lookup"><span data-stu-id="a77aa-113">Example</span></span>  
 <span data-ttu-id="a77aa-114">下列範例示範各種可取得之目前屬性的<xref:System.Windows.Automation.AutomationElement>方式。</span><span class="sxs-lookup"><span data-stu-id="a77aa-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="a77aa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a77aa-115">See also</span></span>

- [<span data-ttu-id="a77aa-116">用戶端的 UI 自動化屬性</span><span class="sxs-lookup"><span data-stu-id="a77aa-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [<span data-ttu-id="a77aa-117">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="a77aa-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [<span data-ttu-id="a77aa-118">UI 自動化用戶端中的快取</span><span class="sxs-lookup"><span data-stu-id="a77aa-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
