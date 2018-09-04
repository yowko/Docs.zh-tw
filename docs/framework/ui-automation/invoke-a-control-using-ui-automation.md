---
title: 使用 UI 自動化叫用控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 6f023a16d431e0a92d7d0068b9a6a014b6f17db8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521653"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="95437-102">使用 UI 自動化叫用控制項</span><span class="sxs-lookup"><span data-stu-id="95437-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="95437-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="95437-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="95437-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="95437-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="95437-105">本主題示範如何執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="95437-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="95437-106">藉由查核目標應用程式之 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的控制項檢視，尋找符合特定屬性條件的控制項。</span><span class="sxs-lookup"><span data-stu-id="95437-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
-   <span data-ttu-id="95437-107">建立每個控制項的 <xref:System.Windows.Automation.AutomationElement> 。</span><span class="sxs-lookup"><span data-stu-id="95437-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
-   <span data-ttu-id="95437-108">從任何找到可支援 <xref:System.Windows.Automation.InvokePattern> 控制項模式的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目中，取得 <xref:System.Windows.Automation.InvokePattern> 物件。</span><span class="sxs-lookup"><span data-stu-id="95437-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
-   <span data-ttu-id="95437-109">使用 <xref:System.Windows.Automation.InvokePattern.Invoke%2A> 以叫用來自用戶端事件處理常式的控制項。</span><span class="sxs-lookup"><span data-stu-id="95437-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95437-110">範例</span><span class="sxs-lookup"><span data-stu-id="95437-110">Example</span></span>  
 <span data-ttu-id="95437-111">此範例使用 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> 類別的 <xref:System.Windows.Automation.AutomationElement> 方法，產生 <xref:System.Windows.Automation.InvokePattern> 物件並利用 <xref:System.Windows.Automation.InvokePattern.Invoke%2A> 方法叫用控制項。</span><span class="sxs-lookup"><span data-stu-id="95437-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="95437-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95437-112">See Also</span></span>  
 [<span data-ttu-id="95437-113">InvokePattern 和 ExpandCollapsePattern 功能表項目範例</span><span class="sxs-lookup"><span data-stu-id="95437-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
