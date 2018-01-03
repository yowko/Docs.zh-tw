---
title: "取得 UI 自動化項目屬性"
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
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
caps.latest.revision: "5"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f3fcbb25fab616b60a1f60d9443af13b60f2d27a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="5fda3-102">取得 UI 自動化項目屬性</span><span class="sxs-lookup"><span data-stu-id="5fda3-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
>  <span data-ttu-id="5fda3-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="5fda3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5fda3-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="5fda3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5fda3-105">本主題示範如何擷取屬性的[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]項目。</span><span class="sxs-lookup"><span data-stu-id="5fda3-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="5fda3-106">取得目前的屬性值</span><span class="sxs-lookup"><span data-stu-id="5fda3-106">Get a Current Property Value</span></span>  
  
1.  <span data-ttu-id="5fda3-107">取得<xref:System.Windows.Automation.AutomationElement>您想要取得其屬性。</span><span class="sxs-lookup"><span data-stu-id="5fda3-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2.  <span data-ttu-id="5fda3-108">呼叫<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>，或擷取<xref:System.Windows.Automation.AutomationElement.Current%2A>屬性結構，以及如何取得其成員的值。</span><span class="sxs-lookup"><span data-stu-id="5fda3-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="5fda3-109">取得快取的屬性值</span><span class="sxs-lookup"><span data-stu-id="5fda3-109">Get a Cached Property Value</span></span>  
  
1.  <span data-ttu-id="5fda3-110">取得<xref:System.Windows.Automation.AutomationElement>您想要取得其屬性。</span><span class="sxs-lookup"><span data-stu-id="5fda3-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="5fda3-111">屬性必須具有在指定<xref:System.Windows.Automation.CacheRequest>。</span><span class="sxs-lookup"><span data-stu-id="5fda3-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="5fda3-112">呼叫<xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>，或擷取<xref:System.Windows.Automation.AutomationElement.Cached%2A>屬性結構，以及如何取得其成員的值。</span><span class="sxs-lookup"><span data-stu-id="5fda3-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fda3-113">範例</span><span class="sxs-lookup"><span data-stu-id="5fda3-113">Example</span></span>  
 <span data-ttu-id="5fda3-114">下列範例示範各種方式來擷取目前的屬性<xref:System.Windows.Automation.AutomationElement>。</span><span class="sxs-lookup"><span data-stu-id="5fda3-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="5fda3-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="5fda3-115">See Also</span></span>  
 [<span data-ttu-id="5fda3-116">用戶端的 UI 自動化屬性</span><span class="sxs-lookup"><span data-stu-id="5fda3-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [<span data-ttu-id="5fda3-117">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="5fda3-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [<span data-ttu-id="5fda3-118">UI 自動化用戶端中的快取</span><span class="sxs-lookup"><span data-stu-id="5fda3-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
