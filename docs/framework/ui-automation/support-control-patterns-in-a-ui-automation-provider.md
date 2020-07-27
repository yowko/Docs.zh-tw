---
title: 支援 UI 自動化提供者的控制項模式
description: 瞭解如何在使用者介面自動化提供者上執行支援控制項模式，讓用戶端應用程式可以操控控制項並從中取得資料。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: 82300499520be6b820b361ebdeb56bbf3716afab
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163509"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="b341d-103">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="b341d-103">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="b341d-104">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="b341d-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b341d-105">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="b341d-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="b341d-106">本主題說明如何在使用者介面自動化提供者上實作一個或多個控制項模式，讓用戶端應用程式能夠操作控制項並從中取得資料。</span><span class="sxs-lookup"><span data-stu-id="b341d-106">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="b341d-107">支援控制項模式</span><span class="sxs-lookup"><span data-stu-id="b341d-107">Support Control Patterns</span></span>

1. <span data-ttu-id="b341d-108">針對項目應該支援的控制項模式，實作適當的介面，例如適用於 <xref:System.Windows.Automation.Provider.IInvokeProvider> 的 <xref:System.Windows.Automation.InvokePattern>。</span><span class="sxs-lookup"><span data-stu-id="b341d-108">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="b341d-109">在 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>實作中，傳回包含每個控制項介面實作的物件</span><span class="sxs-lookup"><span data-stu-id="b341d-109">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="b341d-110">範例</span><span class="sxs-lookup"><span data-stu-id="b341d-110">Example</span></span>

<span data-ttu-id="b341d-111">下列範例示範單一選取自訂清單方塊的 <xref:System.Windows.Automation.Provider.ISelectionProvider> 實作。</span><span class="sxs-lookup"><span data-stu-id="b341d-111">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="b341d-112">它會傳回三個屬性並取得目前選取的項目。</span><span class="sxs-lookup"><span data-stu-id="b341d-112">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="b341d-113">範例</span><span class="sxs-lookup"><span data-stu-id="b341d-113">Example</span></span>

<span data-ttu-id="b341d-114">下列範例示範 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> 的實作，它會傳回實作 <xref:System.Windows.Automation.Provider.ISelectionProvider>的類別。</span><span class="sxs-lookup"><span data-stu-id="b341d-114">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="b341d-115">大部分的清單方塊控制項也會支援其他模式，但是在此範例中， `Nothing` 會針對所有其他模式識別碼傳回 null 參考（在 Microsoft Visual Basic .net 中）。</span><span class="sxs-lookup"><span data-stu-id="b341d-115">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="b341d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b341d-116">See also</span></span>

- [<span data-ttu-id="b341d-117">UI 自動化提供者概觀</span><span class="sxs-lookup"><span data-stu-id="b341d-117">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="b341d-118">伺服器端 UI 自動化提供者實作</span><span class="sxs-lookup"><span data-stu-id="b341d-118">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
