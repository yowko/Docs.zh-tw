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
ms.openlocfilehash: 87090709068ced015ba607005678995c25bf3403
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679642"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="2d0d9-102">取得 UI 自動化項目屬性</span><span class="sxs-lookup"><span data-stu-id="2d0d9-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
>  <span data-ttu-id="2d0d9-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="2d0d9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2d0d9-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="2d0d9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="2d0d9-105">本主題示範如何擷取屬性的[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]項目。</span><span class="sxs-lookup"><span data-stu-id="2d0d9-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="2d0d9-106">取得目前的屬性值</span><span class="sxs-lookup"><span data-stu-id="2d0d9-106">Get a Current Property Value</span></span>  
  
1.  <span data-ttu-id="2d0d9-107">取得<xref:System.Windows.Automation.AutomationElement>您想要取得其屬性。</span><span class="sxs-lookup"><span data-stu-id="2d0d9-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2.  <span data-ttu-id="2d0d9-108">呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>，或擷取<xref:System.Windows.Automation.AutomationElement.Current%2A>屬性結構，以及如何取得其成員之一的值。</span><span class="sxs-lookup"><span data-stu-id="2d0d9-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="2d0d9-109">取得快取的屬性值</span><span class="sxs-lookup"><span data-stu-id="2d0d9-109">Get a Cached Property Value</span></span>  
  
1.  <span data-ttu-id="2d0d9-110">取得<xref:System.Windows.Automation.AutomationElement>您想要取得其屬性。</span><span class="sxs-lookup"><span data-stu-id="2d0d9-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="2d0d9-111">屬性必須具有在指定<xref:System.Windows.Automation.CacheRequest>。</span><span class="sxs-lookup"><span data-stu-id="2d0d9-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="2d0d9-112">呼叫<xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>，或擷取<xref:System.Windows.Automation.AutomationElement.Cached%2A>屬性結構，以及如何取得其成員之一的值。</span><span class="sxs-lookup"><span data-stu-id="2d0d9-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d0d9-113">範例</span><span class="sxs-lookup"><span data-stu-id="2d0d9-113">Example</span></span>  
 <span data-ttu-id="2d0d9-114">下列範例示範各種方式來擷取目前的屬性<xref:System.Windows.Automation.AutomationElement>。</span><span class="sxs-lookup"><span data-stu-id="2d0d9-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="2d0d9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d0d9-115">See also</span></span>
- [<span data-ttu-id="2d0d9-116">用戶端的 UI 自動化屬性</span><span class="sxs-lookup"><span data-stu-id="2d0d9-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [<span data-ttu-id="2d0d9-117">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="2d0d9-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [<span data-ttu-id="2d0d9-118">UI 自動化用戶端中的快取</span><span class="sxs-lookup"><span data-stu-id="2d0d9-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
