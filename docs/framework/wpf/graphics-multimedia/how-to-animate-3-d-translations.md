---
title: HOW TO：建立立體轉譯動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 0290beac5a92a955b39d0b8fcc24705346c2964a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351914"
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="b98de-102">HOW TO：建立立體轉譯動畫</span><span class="sxs-lookup"><span data-stu-id="b98de-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="b98de-103">本主題示範如何以動畫顯示上設定的轉譯轉換[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型。</span><span class="sxs-lookup"><span data-stu-id="b98de-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="b98de-104">下列程式碼顯示如何應用<xref:System.Windows.Media.Media3D.TranslateTransform3D>物件至<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>。</span><span class="sxs-lookup"><span data-stu-id="b98de-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="b98de-105"><xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>屬性的<xref:System.Windows.Media.Media3D.TranslateTransform3D>物件以動畫顯示下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="b98de-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="b98de-106">範例</span><span class="sxs-lookup"><span data-stu-id="b98de-106">Example</span></span>  
 <span data-ttu-id="b98de-107">下列程式碼顯示整個範例。</span><span class="sxs-lookup"><span data-stu-id="b98de-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b98de-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b98de-108">See also</span></span>
- [<span data-ttu-id="b98de-109">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="b98de-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="b98de-110">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="b98de-110">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="b98de-111">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="b98de-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="b98de-112">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="b98de-112">Transforms Overview</span></span>](transforms-overview.md)
