---
title: HOW TO：建立自訂面板項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 2e778adfb79a64c8f248992aee92de9471906129
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368697"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="3d00f-102">HOW TO：建立自訂面板項目</span><span class="sxs-lookup"><span data-stu-id="3d00f-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="3d00f-103">範例</span><span class="sxs-lookup"><span data-stu-id="3d00f-103">Example</span></span>  
 <span data-ttu-id="3d00f-104">此範例示範如何覆寫預設版面配置行為<xref:System.Windows.Controls.Panel>項目，並建立自訂的版面配置項目衍生自<xref:System.Windows.Controls.Panel>。</span><span class="sxs-lookup"><span data-stu-id="3d00f-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="3d00f-105">此範例會定義簡單的自訂<xref:System.Windows.Controls.Panel>項目稱為`PlotPanel`，其中放置子項目根據兩個硬式編碼 x 和 y 座標。</span><span class="sxs-lookup"><span data-stu-id="3d00f-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="3d00f-106">在此範例中，`x`並`y`都設為`50`; 因此，所有子項目都位於此位置的 x 和 y 軸。</span><span class="sxs-lookup"><span data-stu-id="3d00f-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="3d00f-107">若要實作自訂<xref:System.Windows.Controls.Panel>行為，此範例會使用<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3d00f-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="3d00f-108">每個方法會傳回<xref:System.Windows.Size>定位和呈現子項目所需的資料。</span><span class="sxs-lookup"><span data-stu-id="3d00f-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3d00f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d00f-109">See also</span></span>
- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="3d00f-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="3d00f-110">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="3d00f-111">建立自訂的內容換行面板範例</span><span class="sxs-lookup"><span data-stu-id="3d00f-111">Create a Custom Content-Wrapping Panel Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159979)
