---
title: "如何：建立自訂面板項目"
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
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e7cca5b6f7a0d5085e70c4ab6ac33ff83b75217
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="5fffd-102">如何：建立自訂面板項目</span><span class="sxs-lookup"><span data-stu-id="5fffd-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="5fffd-103">範例</span><span class="sxs-lookup"><span data-stu-id="5fffd-103">Example</span></span>  
 <span data-ttu-id="5fffd-104">這個範例示範如何覆寫預設配置行為<xref:System.Windows.Controls.Panel>項目及建立自訂版面配置項目衍生自<xref:System.Windows.Controls.Panel>。</span><span class="sxs-lookup"><span data-stu-id="5fffd-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="5fffd-105">此範例會定義簡單的自訂<xref:System.Windows.Controls.Panel>項目稱為`PlotPanel`，其中放置子項目根據兩個硬式編碼 x 和 y 座標。</span><span class="sxs-lookup"><span data-stu-id="5fffd-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="5fffd-106">在此範例中，`x`和`y`都設定為`50`; 因此，所有子項目會都放置在該位置上的 x 和 y 軸。</span><span class="sxs-lookup"><span data-stu-id="5fffd-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="5fffd-107">若要實作自訂<xref:System.Windows.Controls.Panel>行為，此範例會使用<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="5fffd-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="5fffd-108">每個方法會傳回<xref:System.Windows.Size>定位和呈現子項目所需的資料。</span><span class="sxs-lookup"><span data-stu-id="5fffd-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5fffd-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fffd-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="5fffd-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="5fffd-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="5fffd-111">建立自訂的內容換行面板範例</span><span class="sxs-lookup"><span data-stu-id="5fffd-111">Create a Custom Content-Wrapping Panel Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159979)
