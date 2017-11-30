---
title: "如何：建立立體轉譯動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0477943b715a23a1d6992f7e9da885ffa01061c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="7cf0a-102">如何：建立立體轉譯動畫</span><span class="sxs-lookup"><span data-stu-id="7cf0a-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="7cf0a-103">本主題示範如何建立動畫上設定的轉譯轉換[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型。</span><span class="sxs-lookup"><span data-stu-id="7cf0a-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="7cf0a-104">下列程式碼顯示如何應用<xref:System.Windows.Media.Media3D.TranslateTransform3D>物件<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>。</span><span class="sxs-lookup"><span data-stu-id="7cf0a-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="7cf0a-105"><xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>屬性這<xref:System.Windows.Media.Media3D.TranslateTransform3D>物件動畫使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cf0a-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="7cf0a-106">範例</span><span class="sxs-lookup"><span data-stu-id="7cf0a-106">Example</span></span>  
 <span data-ttu-id="7cf0a-107">下列程式碼顯示完整的範例。</span><span class="sxs-lookup"><span data-stu-id="7cf0a-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="7cf0a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cf0a-108">See Also</span></span>  
 [<span data-ttu-id="7cf0a-109">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="7cf0a-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="7cf0a-110">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="7cf0a-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="7cf0a-111">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="7cf0a-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="7cf0a-112">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="7cf0a-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
