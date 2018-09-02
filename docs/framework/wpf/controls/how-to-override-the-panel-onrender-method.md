---
title: 如何：覆寫 Panel 的 OnRender 方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: 8f3b65bdfe96efdc57c6b8d30991439d3bdb0bc5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404432"
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="c68ce-102">如何：覆寫 Panel 的 OnRender 方法</span><span class="sxs-lookup"><span data-stu-id="c68ce-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="c68ce-103">此範例示範如何覆寫<xref:System.Windows.Controls.Panel.OnRender%2A>方法的<xref:System.Windows.Controls.Panel>才能將自訂的圖形效果加入至版面配置項目。</span><span class="sxs-lookup"><span data-stu-id="c68ce-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c68ce-104">範例</span><span class="sxs-lookup"><span data-stu-id="c68ce-104">Example</span></span>  
 <span data-ttu-id="c68ce-105">使用<xref:System.Windows.Controls.Panel.OnRender%2A>方法，以新增至呈現的面板元素的圖形化的效果。</span><span class="sxs-lookup"><span data-stu-id="c68ce-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="c68ce-106">例如，您可以使用這個方法將自訂的框線或背景效果。</span><span class="sxs-lookup"><span data-stu-id="c68ce-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="c68ce-107">A<xref:System.Windows.Media.DrawingContext>物件會傳遞做為引數會提供方法來繪製圖形、 文字、 影像或影片。</span><span class="sxs-lookup"><span data-stu-id="c68ce-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="c68ce-108">如此一來，這個方法可用於自訂的面板物件。</span><span class="sxs-lookup"><span data-stu-id="c68ce-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c68ce-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c68ce-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="c68ce-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="c68ce-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="c68ce-111">自訂放射狀面板範例</span><span class="sxs-lookup"><span data-stu-id="c68ce-111">Custom Radial Panel Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159982)  
 [<span data-ttu-id="c68ce-112">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="c68ce-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
