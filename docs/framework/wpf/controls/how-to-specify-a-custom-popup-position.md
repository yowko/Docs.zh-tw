---
title: "如何：指定自訂 Popup 的位置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae10153f31b79a220b84cae7a6525eca0ce0bd9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="f3d37-102">如何：指定自訂 Popup 的位置</span><span class="sxs-lookup"><span data-stu-id="f3d37-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="f3d37-103">這個範例示範如何指定的自訂位置<xref:System.Windows.Controls.Primitives.Popup>負責控制何時<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。</span><span class="sxs-lookup"><span data-stu-id="f3d37-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3d37-104">範例</span><span class="sxs-lookup"><span data-stu-id="f3d37-104">Example</span></span>  
 <span data-ttu-id="f3d37-105">當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>、<xref:System.Windows.Controls.Primitives.Popup>呼叫定義的執行個體的<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委派。</span><span class="sxs-lookup"><span data-stu-id="f3d37-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="f3d37-106">這個委派會傳回一組目標區域的左上的角和的左上的角相對的可能點<xref:System.Windows.Controls.Primitives.Popup>。</span><span class="sxs-lookup"><span data-stu-id="f3d37-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="f3d37-107"><xref:System.Windows.Controls.Primitives.Popup>放置某處，提供最佳的可見性。</span><span class="sxs-lookup"><span data-stu-id="f3d37-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="f3d37-108">下列範例示範如何定義的位置<xref:System.Windows.Controls.Primitives.Popup>藉由設定<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。</span><span class="sxs-lookup"><span data-stu-id="f3d37-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="f3d37-109">它也示範如何建立並指派<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>才能將委派<xref:System.Windows.Controls.Primitives.Popup>。</span><span class="sxs-lookup"><span data-stu-id="f3d37-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="f3d37-110">回呼委派會傳回兩個<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>物件。</span><span class="sxs-lookup"><span data-stu-id="f3d37-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="f3d37-111">如果<xref:System.Windows.Controls.Primitives.Popup>螢幕的邊緣的第一個位置，隱藏<xref:System.Windows.Controls.Primitives.Popup>會放在第二個位置。</span><span class="sxs-lookup"><span data-stu-id="f3d37-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="f3d37-112">如需完整範例，請參閱[快顯功能表放置範例](http://go.microsoft.com/fwlink/?LinkID=160032)。</span><span class="sxs-lookup"><span data-stu-id="f3d37-112">For the complete sample, see [Popup Placement Sample](http://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d37-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3d37-113">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="f3d37-114">快顯功能表概觀</span><span class="sxs-lookup"><span data-stu-id="f3d37-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [<span data-ttu-id="f3d37-115">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="f3d37-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
