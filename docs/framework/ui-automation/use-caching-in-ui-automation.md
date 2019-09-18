---
title: 使用 UI 自動化中的快取
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: dd7506d388ba215f671ee3c7c4bae09baf4cc2b3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040315"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="c5bcf-102">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="c5bcf-102">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="c5bcf-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c5bcf-104">如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="c5bcf-105">本節說明如何實作 <xref:System.Windows.Automation.AutomationElement> 屬性和控制項模式的快取。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="c5bcf-106">啟動快取要求</span><span class="sxs-lookup"><span data-stu-id="c5bcf-106">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="c5bcf-107">建立 <xref:System.Windows.Automation.CacheRequest>。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="c5bcf-108">使用 <xref:System.Windows.Automation.CacheRequest.Add%2A>指定要快取的屬性和模式。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="c5bcf-109">設定 <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> 屬性，以指定快取的範圍。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="c5bcf-110">設定 <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> 屬性，以指定樹狀子目錄的檢視。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="c5bcf-111">如果要提高效率而不擷取物件的完整參考，可以將 <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> 屬性設為 <xref:System.Windows.Automation.AutomationElementMode.None> 。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="c5bcf-112">(如此將無法從這些物件擷取目前值。)</span><span class="sxs-lookup"><span data-stu-id="c5bcf-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="c5bcf-113">在<xref:System.Windows.Automation.CacheRequest.Activate%2A> 區塊`using`內使用（`Using`在 Microsoft Visual Basic .net 中）來啟動要求。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="c5bcf-114">在取得 <xref:System.Windows.Automation.AutomationElement> 物件或訂閱事件之後，使用 <xref:System.Windows.Automation.CacheRequest.Pop%2A> (若使用 <xref:System.Windows.Automation.CacheRequest.Push%2A> ) 或處置 <xref:System.Windows.Automation.CacheRequest.Activate%2A>所建立的物件，以停用要求。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="c5bcf-115">（在<xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` 區塊`Using`中使用（在 Microsoft Visual Basic .net 中）。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="c5bcf-116">快取 AutomationElement 屬性</span><span class="sxs-lookup"><span data-stu-id="c5bcf-116">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="c5bcf-117">當 <xref:System.Windows.Automation.CacheRequest> 在作用中時，使用 <xref:System.Windows.Automation.AutomationElement> 或 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 取得 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>物件；或取得 <xref:System.Windows.Automation.AutomationElement> 做為 <xref:System.Windows.Automation.CacheRequest> 作用中時註冊之事件的來源。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="c5bcf-118">(您也可以將 <xref:System.Windows.Automation.CacheRequest> 傳遞至 GetUpdatedCache 或其中一個 <xref:System.Windows.Automation.TreeWalker> 方法，以此方式建立快取。)</span><span class="sxs-lookup"><span data-stu-id="c5bcf-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="c5bcf-119">使用 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> ，或從 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 的 <xref:System.Windows.Automation.AutomationElement>屬性擷取屬性。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="c5bcf-120">取得快取的模式及其屬性</span><span class="sxs-lookup"><span data-stu-id="c5bcf-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="c5bcf-121">當 <xref:System.Windows.Automation.CacheRequest> 在作用中時，使用 <xref:System.Windows.Automation.AutomationElement> 或 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 取得 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>物件；或取得 <xref:System.Windows.Automation.AutomationElement> 做為 <xref:System.Windows.Automation.CacheRequest> 作用中時註冊之事件的來源。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="c5bcf-122">(您也可以將 <xref:System.Windows.Automation.CacheRequest> 傳遞至 GetUpdatedCache 或其中一個 <xref:System.Windows.Automation.TreeWalker> 方法，以此方式建立快取。)</span><span class="sxs-lookup"><span data-stu-id="c5bcf-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="c5bcf-123">使用 <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> 或 <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> 擷取快取的模式。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="c5bcf-124">從控制項模式的 `Cached` 屬性擷取屬性值。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5bcf-125">範例</span><span class="sxs-lookup"><span data-stu-id="c5bcf-125">Example</span></span>  
 <span data-ttu-id="c5bcf-126">下列程式碼範例使用 <xref:System.Windows.Automation.CacheRequest.Activate%2A> 啟動 <xref:System.Windows.Automation.CacheRequest>，顯示快取的各個方面。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="c5bcf-127">範例</span><span class="sxs-lookup"><span data-stu-id="c5bcf-127">Example</span></span>  
 <span data-ttu-id="c5bcf-128">下列程式碼範例使用 <xref:System.Windows.Automation.CacheRequest.Push%2A> 啟動 <xref:System.Windows.Automation.CacheRequest>，顯示快取的各個方面。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="c5bcf-129">要將快取要求進行巢狀處理時則例外，這時最好使用 <xref:System.Windows.Automation.CacheRequest.Activate%2A>。</span><span class="sxs-lookup"><span data-stu-id="c5bcf-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="c5bcf-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5bcf-130">See also</span></span>

- [<span data-ttu-id="c5bcf-131">UI 自動化用戶端中的快取</span><span class="sxs-lookup"><span data-stu-id="c5bcf-131">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
