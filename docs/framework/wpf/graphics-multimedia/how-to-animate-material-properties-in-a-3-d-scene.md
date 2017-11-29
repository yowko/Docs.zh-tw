---
title: "如何：在立體場景中建立材質屬性的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Material properties [WPF], animating in 3-D scenes
- animation [WPF], Material properties in 3-D scenes
- 3-D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 273c03fcedbd5e5b2f6a38cb718788d5f8d8fda3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-material-properties-in-a-3-d-scene"></a><span data-ttu-id="8953b-102">如何：在立體場景中建立材質屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="8953b-102">How to: Animate Material Properties in a 3-D Scene</span></span>
<span data-ttu-id="8953b-103">此範例示範如何以動畫方式顯示<xref:System.Windows.Media.Brush.Opacity%2A>屬性<xref:System.Windows.Media.Media3D.Material>套用至[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型。</span><span class="sxs-lookup"><span data-stu-id="8953b-103">This example shows how to animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="8953b-104">下列程式碼範例會定義<xref:System.Windows.Media.LinearGradientBrush>做<xref:System.Windows.Media.Media3D.Material>套用至 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="8953b-104">The following code example defines the <xref:System.Windows.Media.LinearGradientBrush> used as the <xref:System.Windows.Media.Media3D.Material> applied to the 3D object.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <span data-ttu-id="8953b-105"><xref:System.Windows.Media.Brush.Opacity%2A>屬性這<xref:System.Windows.Media.LinearGradientBrush>使用下列程式碼範例會顯示動畫。</span><span class="sxs-lookup"><span data-stu-id="8953b-105">The <xref:System.Windows.Media.Brush.Opacity%2A> property of this <xref:System.Windows.Media.LinearGradientBrush> is animated using the code example below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="8953b-106">範例</span><span class="sxs-lookup"><span data-stu-id="8953b-106">Example</span></span>  
 <span data-ttu-id="8953b-107">下列程式碼顯示完整的範例。</span><span class="sxs-lookup"><span data-stu-id="8953b-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="8953b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8953b-108">See Also</span></span>  
 [<span data-ttu-id="8953b-109">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="8953b-109">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="8953b-110">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="8953b-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
