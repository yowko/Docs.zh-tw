---
title: 訂閱 UI 自動化事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 576c883a0600c84a45503c013f0d60152628f52e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688073"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="5f73e-102">訂閱 UI 自動化事件</span><span class="sxs-lookup"><span data-stu-id="5f73e-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
>  <span data-ttu-id="5f73e-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="5f73e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5f73e-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="5f73e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5f73e-105">本主題說明如何訂閱使用者介面自動化提供者所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="5f73e-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f73e-106">範例</span><span class="sxs-lookup"><span data-stu-id="5f73e-106">Example</span></span>  
 <span data-ttu-id="5f73e-107">下列範例程式碼會註冊如按鈕等控制項叫用時所引發之事件的事件處理常式，並在應用程式表單關閉時將它移除。</span><span class="sxs-lookup"><span data-stu-id="5f73e-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="5f73e-108">此事件由 <xref:System.Windows.Automation.AutomationEvent> 當做參數傳遞給 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>。</span><span class="sxs-lookup"><span data-stu-id="5f73e-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="5f73e-109">範例</span><span class="sxs-lookup"><span data-stu-id="5f73e-109">Example</span></span>  
 <span data-ttu-id="5f73e-110">下列範例示範如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 訂閱當焦點變更時所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="5f73e-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="5f73e-111">事件處理常式會在應用程式關閉或已不再需要使用者介面事件通知時呼叫的方法中移除註冊。</span><span class="sxs-lookup"><span data-stu-id="5f73e-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="5f73e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f73e-112">See also</span></span>
- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="5f73e-113">UI 自動化事件概觀</span><span class="sxs-lookup"><span data-stu-id="5f73e-113">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
