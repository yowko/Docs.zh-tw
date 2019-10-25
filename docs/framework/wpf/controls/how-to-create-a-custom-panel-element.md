---
title: 如何：建立自訂面板項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799141"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="284f0-102">如何：建立自訂面板項目</span><span class="sxs-lookup"><span data-stu-id="284f0-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="284f0-103">範例</span><span class="sxs-lookup"><span data-stu-id="284f0-103">Example</span></span>  
 <span data-ttu-id="284f0-104">這個範例會示範如何覆寫 <xref:System.Windows.Controls.Panel> 專案的預設版面配置行為，並建立衍生自 <xref:System.Windows.Controls.Panel>的自訂配置元素。</span><span class="sxs-lookup"><span data-stu-id="284f0-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="284f0-105">這個範例會定義一個稱為 `PlotPanel`的簡單自訂 <xref:System.Windows.Controls.Panel> 專案，這會根據兩個硬式編碼的 x 和 y 座標來放置子項目。</span><span class="sxs-lookup"><span data-stu-id="284f0-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="284f0-106">在此範例中，`x` 和 `y` 都設定為 `50`;因此，所有子專案都位於 x 和 y 軸的該位置。</span><span class="sxs-lookup"><span data-stu-id="284f0-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="284f0-107">若要執行自訂 <xref:System.Windows.Controls.Panel> 行為，此範例會使用 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="284f0-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="284f0-108">每個方法都會傳回位置和呈現子專案所需的 <xref:System.Windows.Size> 資料。</span><span class="sxs-lookup"><span data-stu-id="284f0-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="284f0-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="284f0-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="284f0-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="284f0-110">Panels Overview</span></span>](panels-overview.md)
