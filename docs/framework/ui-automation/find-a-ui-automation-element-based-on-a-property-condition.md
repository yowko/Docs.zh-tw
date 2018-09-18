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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4c4f14f79960b98618a4f6a3450b1e1a2c05f731
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003538"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="c8a92-102">根據屬性條件尋找 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="c8a92-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
>  <span data-ttu-id="c8a92-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="c8a92-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c8a92-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="c8a92-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="c8a92-105">本主題包含範例程式碼，示範如何找出內的項目[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構會根據特定的屬性或屬性。</span><span class="sxs-lookup"><span data-stu-id="c8a92-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8a92-106">範例</span><span class="sxs-lookup"><span data-stu-id="c8a92-106">Example</span></span>  
 <span data-ttu-id="c8a92-107">在下列範例中，一組屬性的條件，找出感興趣的特定項目 （或項目） 中指定<xref:System.Windows.Automation.AutomationElement>樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="c8a92-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="c8a92-108">搜尋所有相符項目則會使用<xref:System.Windows.Automation.AutomationElement.FindAll%2A>方法，其中包含一系列的<xref:System.Windows.Automation.AndCondition>布林作業，以限制的相符項目數目。</span><span class="sxs-lookup"><span data-stu-id="c8a92-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8a92-109">從搜尋時<xref:System.Windows.Automation.AutomationElement.RootElement%2A>，您應該試著取得直接子系。</span><span class="sxs-lookup"><span data-stu-id="c8a92-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="c8a92-110">如果搜尋子代可能會逐一查看數百或甚至數千個項目，但可能會造成堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="c8a92-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="c8a92-111">如果您嘗試取得較低層級的特定項目，您就應該要從應用程式視窗或較低層級的容器開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="c8a92-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="c8a92-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8a92-112">See Also</span></span>  
 [<span data-ttu-id="c8a92-113">InvokePattern 和 ExpandCollapsePattern 功能表項目範例</span><span class="sxs-lookup"><span data-stu-id="c8a92-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [<span data-ttu-id="c8a92-114">取得 UI 自動化項目</span><span class="sxs-lookup"><span data-stu-id="c8a92-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [<span data-ttu-id="c8a92-115">使用 AutomationID 屬性</span><span class="sxs-lookup"><span data-stu-id="c8a92-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
