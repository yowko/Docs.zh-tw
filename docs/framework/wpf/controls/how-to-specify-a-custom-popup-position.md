---
title: 如何：指定自訂 Popup 的位置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: ea8d73c51dd018608b95104f00bf341ff434225c
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344957"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="160dd-102">如何：指定自訂 Popup 的位置</span><span class="sxs-lookup"><span data-stu-id="160dd-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="160dd-103">此示例演示如何在<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設置為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>時為控制項指定自訂位置。</span><span class="sxs-lookup"><span data-stu-id="160dd-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="160dd-104">範例</span><span class="sxs-lookup"><span data-stu-id="160dd-104">Example</span></span>  
 <span data-ttu-id="160dd-105">當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設置為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>時，<xref:System.Windows.Controls.Primitives.Popup>調用<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委託的已定義實例。</span><span class="sxs-lookup"><span data-stu-id="160dd-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="160dd-106">此委託返回一組相對於目的地區域左上角和 左<xref:System.Windows.Controls.Primitives.Popup>上角的可能點。</span><span class="sxs-lookup"><span data-stu-id="160dd-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="160dd-107">放置<xref:System.Windows.Controls.Primitives.Popup>發生在提供最佳可見度的點。</span><span class="sxs-lookup"><span data-stu-id="160dd-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="160dd-108">下面的示例演示如何通過將<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設置為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>來定義 的位置。</span><span class="sxs-lookup"><span data-stu-id="160dd-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="160dd-109">它還演示如何創建和分配<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委託，以便定位 。 <xref:System.Windows.Controls.Primitives.Popup></span><span class="sxs-lookup"><span data-stu-id="160dd-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="160dd-110">回檔委託返回兩<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>個物件。</span><span class="sxs-lookup"><span data-stu-id="160dd-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="160dd-111"><xref:System.Windows.Controls.Primitives.Popup>如果在第一個位置由螢幕邊緣隱藏，<xref:System.Windows.Controls.Primitives.Popup>則 將放置在第二個位置。</span><span class="sxs-lookup"><span data-stu-id="160dd-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="160dd-112">有關完整示例，請參閱[彈出放置示例](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)。</span><span class="sxs-lookup"><span data-stu-id="160dd-112">For the complete sample, see [Popup Placement Sample](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="160dd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="160dd-113">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="160dd-114">快顯功能表概觀</span><span class="sxs-lookup"><span data-stu-id="160dd-114">Popup Overview</span></span>](popup-overview.md)
- [<span data-ttu-id="160dd-115">HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="160dd-115">How-to Topics</span></span>](popup-how-to-topics.md)
