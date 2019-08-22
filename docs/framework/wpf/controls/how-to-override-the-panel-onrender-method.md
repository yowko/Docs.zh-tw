---
title: HOW TO：覆寫 Panel 的 OnRender 方法
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
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666708"
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="1c9c3-102">作法：覆寫 Panel 的 OnRender 方法</span><span class="sxs-lookup"><span data-stu-id="1c9c3-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="1c9c3-103">這個範例會示範如何覆寫<xref:System.Windows.Controls.Panel.OnRender%2A>的<xref:System.Windows.Controls.Panel>方法, 以便將自訂圖形效果加入至版面配置元素。</span><span class="sxs-lookup"><span data-stu-id="1c9c3-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c9c3-104">範例</span><span class="sxs-lookup"><span data-stu-id="1c9c3-104">Example</span></span>  
 <span data-ttu-id="1c9c3-105"><xref:System.Windows.Controls.Panel.OnRender%2A>使用方法, 即可將圖形效果加入至呈現的面板專案。</span><span class="sxs-lookup"><span data-stu-id="1c9c3-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="1c9c3-106">例如, 您可以使用這個方法來新增自訂框線或背景效果。</span><span class="sxs-lookup"><span data-stu-id="1c9c3-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="1c9c3-107"><xref:System.Windows.Media.DrawingContext>物件會當做引數傳遞, 以提供繪製圖形、文字、影像或影片的方法。</span><span class="sxs-lookup"><span data-stu-id="1c9c3-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="1c9c3-108">因此, 這個方法對於面板物件的自訂很有用。</span><span class="sxs-lookup"><span data-stu-id="1c9c3-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1c9c3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c9c3-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="1c9c3-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="1c9c3-110">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="1c9c3-111">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="1c9c3-111">How-to Topics</span></span>](panel-how-to-topics.md)
