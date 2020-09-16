---
title: 根據屬性條件尋找 UI 自動化項目
description: 根據屬性條件尋找消費者介面自動化元素。 根據特定屬性或屬性，找出消費者介面自動化樹狀結構中的元素。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 112f38d6bef726f92dbf13da70b88732929175dd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557680"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="a532c-104">根據屬性條件尋找 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="a532c-104">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="a532c-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="a532c-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a532c-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="a532c-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a532c-107">本主題包含範例程式碼，示範如何 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 根據特定屬性或屬性找出樹狀結構中的元素。</span><span class="sxs-lookup"><span data-stu-id="a532c-107">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a532c-108">範例</span><span class="sxs-lookup"><span data-stu-id="a532c-108">Example</span></span>  
 <span data-ttu-id="a532c-109">在下列範例中，指定了一組屬性條件，以識別樹狀結構中所需的特定元素 (或元素) <xref:System.Windows.Automation.AutomationElement> 。</span><span class="sxs-lookup"><span data-stu-id="a532c-109">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="a532c-110">接著，會使用 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 併入一連串布耳運算的方法來執行所有相符專案的搜尋 <xref:System.Windows.Automation.AndCondition> ，以限制相符專案的數目。</span><span class="sxs-lookup"><span data-stu-id="a532c-110">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a532c-111">從搜尋時 <xref:System.Windows.Automation.AutomationElement.RootElement%2A> ，您應該嘗試只取得直接子系。</span><span class="sxs-lookup"><span data-stu-id="a532c-111">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="a532c-112">搜尋子代可能會逐一查看數百或甚至數千個專案，可能會導致堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="a532c-112">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="a532c-113">如果您嘗試取得較低層級的特定項目，您應該從應用程式視窗或較低層級的容器開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="a532c-113">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="a532c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a532c-114">See also</span></span>

- <span data-ttu-id="a532c-115">[InvokePattern 和 ExpandCollapsePattern 功能表項目範例](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a532c-115">[InvokePattern and ExpandCollapsePattern Menu Item Sample](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="a532c-116">取得 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="a532c-116">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="a532c-117">使用 AutomationID 屬性</span><span class="sxs-lookup"><span data-stu-id="a532c-117">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
