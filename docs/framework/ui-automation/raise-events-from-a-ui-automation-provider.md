---
title: UI 自動化提供者引發事件
description: 請參閱示範如何從消費者介面自動化提供者引發事件的範例。 它會在自訂按鈕控制項的執行期間引發消費者介面自動化事件。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 73be7fd92f3fde90255326c51bed03427fd68e8d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250485"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="2983e-104">UI 自動化提供者引發事件</span><span class="sxs-lookup"><span data-stu-id="2983e-104">Raise Events from a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="2983e-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="2983e-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2983e-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="2983e-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2983e-107">本主題包含範例程式碼，說明如何透過使用者介面自動化提供者來引發事件。</span><span class="sxs-lookup"><span data-stu-id="2983e-107">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2983e-108">範例</span><span class="sxs-lookup"><span data-stu-id="2983e-108">Example</span></span>  

 <span data-ttu-id="2983e-109">下列範例會在自訂按鈕控制項的實作中引發 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="2983e-109">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="2983e-110">該實作可讓使用者介面自動化用戶端應用程式模擬按鈕點選動作。</span><span class="sxs-lookup"><span data-stu-id="2983e-110">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="2983e-111">為了避免不必要的處理，範例會檢查 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> 以查看是否應該引發事件。</span><span class="sxs-lookup"><span data-stu-id="2983e-111">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="2983e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2983e-112">See also</span></span>

- [<span data-ttu-id="2983e-113">UI 自動化提供者概觀</span><span class="sxs-lookup"><span data-stu-id="2983e-113">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
