---
title: "如何：覆寫 Panel 的 OnRender 方法"
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 774c612b09d5cb0ffdf36024a7e6a543f407cf67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="b83f9-102">如何：覆寫 Panel 的 OnRender 方法</span><span class="sxs-lookup"><span data-stu-id="b83f9-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="b83f9-103">這個範例示範如何覆寫<xref:System.Windows.Controls.Panel.OnRender%2A>方法<xref:System.Windows.Controls.Panel>以便將自訂的圖形效果新增至版面配置項目。</span><span class="sxs-lookup"><span data-stu-id="b83f9-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b83f9-104">範例</span><span class="sxs-lookup"><span data-stu-id="b83f9-104">Example</span></span>  
 <span data-ttu-id="b83f9-105">使用<xref:System.Windows.Controls.Panel.OnRender%2A>方法，以將圖形效果加入至轉譯的面板項目。</span><span class="sxs-lookup"><span data-stu-id="b83f9-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="b83f9-106">例如，您可以使用這個方法將自訂框線或背景效果。</span><span class="sxs-lookup"><span data-stu-id="b83f9-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="b83f9-107">A<xref:System.Windows.Media.DrawingContext>物件會傳遞做為引數，提供方法來繪製圖形、 文字、 影像或視訊。</span><span class="sxs-lookup"><span data-stu-id="b83f9-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="b83f9-108">如此一來，這個方法可用於自訂的面板物件。</span><span class="sxs-lookup"><span data-stu-id="b83f9-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b83f9-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b83f9-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="b83f9-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="b83f9-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="b83f9-111">自訂放射狀面板範例</span><span class="sxs-lookup"><span data-stu-id="b83f9-111">Custom Radial Panel Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [<span data-ttu-id="b83f9-112">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="b83f9-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
