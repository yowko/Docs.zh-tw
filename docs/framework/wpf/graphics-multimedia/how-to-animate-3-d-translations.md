---
title: 如何：動畫 3D 翻譯
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations
- 3D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 7d4fff9c74663bd220ad5d15a983bcb639621afd
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112254"
---
# <a name="how-to-animate-3d-translations"></a><span data-ttu-id="de716-102">如何：動畫 3D 翻譯</span><span class="sxs-lookup"><span data-stu-id="de716-102">How to: Animate 3D Translations</span></span>
<span data-ttu-id="de716-103">本主題演示如何在 3D 模型上為轉換轉換集設置動畫。</span><span class="sxs-lookup"><span data-stu-id="de716-103">This topic demonstrates how to animate a translation transformation set on a 3D model.</span></span>  
  
 <span data-ttu-id="de716-104">下面的代碼顯示了<xref:System.Windows.Media.Media3D.TranslateTransform3D>物件對<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>的應用。</span><span class="sxs-lookup"><span data-stu-id="de716-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="de716-105">此<xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A><xref:System.Windows.Media.Media3D.TranslateTransform3D>物件的屬性使用以下代碼進行動畫處理。</span><span class="sxs-lookup"><span data-stu-id="de716-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="de716-106">範例</span><span class="sxs-lookup"><span data-stu-id="de716-106">Example</span></span>  
 <span data-ttu-id="de716-107">以下代碼顯示整個示例。</span><span class="sxs-lookup"><span data-stu-id="de716-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="de716-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de716-108">See also</span></span>

- [<span data-ttu-id="de716-109">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="de716-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="de716-110">創建 3D 場景</span><span class="sxs-lookup"><span data-stu-id="de716-110">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="de716-111">3D 圖形概述</span><span class="sxs-lookup"><span data-stu-id="de716-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="de716-112">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="de716-112">Transforms Overview</span></span>](transforms-overview.md)
