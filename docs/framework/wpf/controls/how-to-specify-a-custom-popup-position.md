---
title: 如何：指定自訂 Popup 的位置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: e6e81a6e0819ba3eb39a1c568e6872414e671544
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261299"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="dbc40-102">如何：指定自訂 Popup 的位置</span><span class="sxs-lookup"><span data-stu-id="dbc40-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="dbc40-103">此範例示範如何指定的自訂位置<xref:System.Windows.Controls.Primitives.Popup>控制何時<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。</span><span class="sxs-lookup"><span data-stu-id="dbc40-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbc40-104">範例</span><span class="sxs-lookup"><span data-stu-id="dbc40-104">Example</span></span>  
 <span data-ttu-id="dbc40-105">當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>，則<xref:System.Windows.Controls.Primitives.Popup>呼叫定義的執行個體<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委派。</span><span class="sxs-lookup"><span data-stu-id="dbc40-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="dbc40-106">這個委派會傳回一組相對於目標區域的左上的角和的左上的角的可能點<xref:System.Windows.Controls.Primitives.Popup>。</span><span class="sxs-lookup"><span data-stu-id="dbc40-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="dbc40-107"><xref:System.Windows.Controls.Primitives.Popup>放置之處發生可提供最佳的可見性。</span><span class="sxs-lookup"><span data-stu-id="dbc40-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="dbc40-108">下列範例示範如何定義的位置<xref:System.Windows.Controls.Primitives.Popup>splittunneling<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。</span><span class="sxs-lookup"><span data-stu-id="dbc40-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="dbc40-109">它也會示範如何建立並指派<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委派，以便放置<xref:System.Windows.Controls.Primitives.Popup>。</span><span class="sxs-lookup"><span data-stu-id="dbc40-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="dbc40-110">回呼委派，會傳回兩個<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>物件。</span><span class="sxs-lookup"><span data-stu-id="dbc40-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="dbc40-111">如果<xref:System.Windows.Controls.Primitives.Popup>隱藏的畫面邊緣的第一個位置，<xref:System.Windows.Controls.Primitives.Popup>放在第二個位置。</span><span class="sxs-lookup"><span data-stu-id="dbc40-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="dbc40-112">如需完整的範例，請參閱[快顯位置範例](https://go.microsoft.com/fwlink/?LinkID=160032)。</span><span class="sxs-lookup"><span data-stu-id="dbc40-112">For the complete sample, see [Popup Placement Sample](https://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc40-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbc40-113">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="dbc40-114">快顯功能表概觀</span><span class="sxs-lookup"><span data-stu-id="dbc40-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [<span data-ttu-id="dbc40-115">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="dbc40-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
