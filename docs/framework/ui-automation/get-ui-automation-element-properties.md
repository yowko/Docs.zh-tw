---
title: 取得 UI 自動化項目屬性
description: 請參閱指示和範例，其中顯示如何取得使用者介面自動化專案的目前或快取屬性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 277822c9d89046bfbad50df16bce83da7dd45b3b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164111"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="df920-103">取得 UI 自動化項目屬性</span><span class="sxs-lookup"><span data-stu-id="df920-103">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="df920-104">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="df920-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="df920-105">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="df920-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="df920-106">本主題說明如何抓取元素的屬性 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="df920-106">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="df920-107">取得目前的屬性值</span><span class="sxs-lookup"><span data-stu-id="df920-107">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="df920-108">取得 <xref:System.Windows.Automation.AutomationElement> 您想要取得其屬性的。</span><span class="sxs-lookup"><span data-stu-id="df920-108">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="df920-109">呼叫 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> 或取出 <xref:System.Windows.Automation.AutomationElement.Current%2A> 屬性結構，並從它的其中一個成員取得值。</span><span class="sxs-lookup"><span data-stu-id="df920-109">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="df920-110">取得快取的屬性值</span><span class="sxs-lookup"><span data-stu-id="df920-110">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="df920-111">取得 <xref:System.Windows.Automation.AutomationElement> 您想要取得其屬性的。</span><span class="sxs-lookup"><span data-stu-id="df920-111">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="df920-112">屬性必須已在中指定 <xref:System.Windows.Automation.CacheRequest> 。</span><span class="sxs-lookup"><span data-stu-id="df920-112">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="df920-113">呼叫 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> 或取出 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 屬性結構，並從它的其中一個成員取得值。</span><span class="sxs-lookup"><span data-stu-id="df920-113">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df920-114">範例</span><span class="sxs-lookup"><span data-stu-id="df920-114">Example</span></span>  
 <span data-ttu-id="df920-115">下列範例示範各種可取得之目前屬性的方式 <xref:System.Windows.Automation.AutomationElement> 。</span><span class="sxs-lookup"><span data-stu-id="df920-115">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="df920-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df920-116">See also</span></span>

- [<span data-ttu-id="df920-117">用戶端的 UI 自動化屬性</span><span class="sxs-lookup"><span data-stu-id="df920-117">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="df920-118">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="df920-118">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="df920-119">UI 自動化用戶端中的快取</span><span class="sxs-lookup"><span data-stu-id="df920-119">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
