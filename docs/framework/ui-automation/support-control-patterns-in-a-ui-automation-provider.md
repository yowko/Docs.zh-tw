---
title: 支援 UI 自動化提供者的控制項模式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
caps.latest.revision: 13
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: c66df9103b1edb43490a7e1a6a9d1a3cc87bfc28
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="1b0c8-102">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="1b0c8-102">Support Control Patterns in a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="1b0c8-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="1b0c8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1b0c8-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="1b0c8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1b0c8-105">本主題說明如何在使用者介面自動化提供者上實作一個或多個控制項模式，讓用戶端應用程式能夠操作控制項並從中取得資料。</span><span class="sxs-lookup"><span data-stu-id="1b0c8-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>  
  
### <a name="support-control-patterns"></a><span data-ttu-id="1b0c8-106">支援控制項模式</span><span class="sxs-lookup"><span data-stu-id="1b0c8-106">Support Control Patterns</span></span>  
  
1.  <span data-ttu-id="1b0c8-107">針對項目應該支援的控制項模式，實作適當的介面，例如適用於 <xref:System.Windows.Automation.Provider.IInvokeProvider> 的 <xref:System.Windows.Automation.InvokePattern>。</span><span class="sxs-lookup"><span data-stu-id="1b0c8-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>  
  
2.  <span data-ttu-id="1b0c8-108">傳回物件，其中包含您的實作中的每個控制項介面的實作 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1b0c8-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>  
  
## <a name="example"></a><span data-ttu-id="1b0c8-109">範例</span><span class="sxs-lookup"><span data-stu-id="1b0c8-109">Example</span></span>  
 <span data-ttu-id="1b0c8-110">下列範例示範單一選取自訂清單方塊的 <xref:System.Windows.Automation.Provider.ISelectionProvider> 實作。</span><span class="sxs-lookup"><span data-stu-id="1b0c8-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="1b0c8-111">它會傳回三個屬性並取得目前選取的項目。</span><span class="sxs-lookup"><span data-stu-id="1b0c8-111">It returns three properties and gets the currently selected item.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a><span data-ttu-id="1b0c8-112">範例</span><span class="sxs-lookup"><span data-stu-id="1b0c8-112">Example</span></span>  
 <span data-ttu-id="1b0c8-113">下列範例示範 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> 的實作，它會傳回實作 <xref:System.Windows.Automation.Provider.ISelectionProvider>的類別。</span><span class="sxs-lookup"><span data-stu-id="1b0c8-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="1b0c8-114">大部分清單方塊控制項會支援其他模式，但在此範例中為 null 參考 (`Nothing`在 Microsoft Visual Basic.NET) 傳回的所有其他模式識別項。</span><span class="sxs-lookup"><span data-stu-id="1b0c8-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a><span data-ttu-id="1b0c8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b0c8-115">See Also</span></span>  
 [<span data-ttu-id="1b0c8-116">UI 自動化提供者概觀</span><span class="sxs-lookup"><span data-stu-id="1b0c8-116">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="1b0c8-117">伺服器端 UI 自動化提供者實作</span><span class="sxs-lookup"><span data-stu-id="1b0c8-117">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
