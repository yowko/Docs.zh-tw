---
title: 根據屬性條件尋找 UI 自動化項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 3ca609551955b32ad8b63296975ce10f097d9c30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433595"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="6f1c9-102">根據屬性條件尋找 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="6f1c9-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="6f1c9-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="6f1c9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6f1c9-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="6f1c9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="6f1c9-105">本主題包含範例程式碼，示範如何根據特定的屬性或屬性，在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構中尋找元素。</span><span class="sxs-lookup"><span data-stu-id="6f1c9-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f1c9-106">範例</span><span class="sxs-lookup"><span data-stu-id="6f1c9-106">Example</span></span>  
 <span data-ttu-id="6f1c9-107">在下列範例中，會指定一組屬性條件，以識別 <xref:System.Windows.Automation.AutomationElement> 樹狀目錄中感興趣的特定專案（或元素）。</span><span class="sxs-lookup"><span data-stu-id="6f1c9-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="6f1c9-108">接著會使用 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 方法來搜尋所有相符的專案，其中包含一系列 <xref:System.Windows.Automation.AndCondition> 的布耳運算，以限制相符的元素數目。</span><span class="sxs-lookup"><span data-stu-id="6f1c9-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f1c9-109">從 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>搜尋時，您應該嘗試只取得直接子系。</span><span class="sxs-lookup"><span data-stu-id="6f1c9-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="6f1c9-110">搜尋子代可能會逐一查看數百個或甚至數千個專案，可能會導致堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="6f1c9-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="6f1c9-111">如果您嘗試取得較低層級的特定項目，您就應該要從應用程式視窗或較低層級的容器開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="6f1c9-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="6f1c9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f1c9-112">See also</span></span>

- <span data-ttu-id="6f1c9-113">[InvokePattern 和 ExpandCollapsePattern 功能表項目範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6f1c9-113">[InvokePattern and ExpandCollapsePattern Menu Item Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="6f1c9-114">Obtaining UI Automation Elements</span><span class="sxs-lookup"><span data-stu-id="6f1c9-114">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="6f1c9-115">使用 AutomationID 屬性</span><span class="sxs-lookup"><span data-stu-id="6f1c9-115">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
