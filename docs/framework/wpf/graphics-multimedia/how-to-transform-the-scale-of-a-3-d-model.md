---
title: 如何：轉換立體模型的比例
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 3cca1a210a7dbe410ebaacaaf89c08de8c31c40e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561094"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a><span data-ttu-id="9b6d5-102">如何：轉換立體模型的比例</span><span class="sxs-lookup"><span data-stu-id="9b6d5-102">How to: Transform the Scale of a 3-D Model</span></span>
<span data-ttu-id="9b6d5-103">此範例顯示如何調整 3d 物件。</span><span class="sxs-lookup"><span data-stu-id="9b6d5-103">This example shows how to scale a 3-D object.</span></span> <span data-ttu-id="9b6d5-104">若要調整規模 3d 物件，請使用<xref:System.Windows.Media.Media3D.ScaleTransform3D>。</span><span class="sxs-lookup"><span data-stu-id="9b6d5-104">To scale a 3-D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="9b6d5-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>， <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>，和<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>屬性調整元素大小依您指定的比例。</span><span class="sxs-lookup"><span data-stu-id="9b6d5-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="9b6d5-106">例如，<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>值為 1.5 延伸到其原始寬度的 150%的物件。</span><span class="sxs-lookup"><span data-stu-id="9b6d5-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="9b6d5-107">A<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>值為 0.5 百分之 50 壓縮物件的高度。</span><span class="sxs-lookup"><span data-stu-id="9b6d5-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="9b6d5-108">下列程式碼示範如何使用<xref:System.Windows.Media.Media3D.ScaleTransform3D>針對轉換為<xref:System.Windows.Media.Media3D.GeometryModel3D>。</span><span class="sxs-lookup"><span data-stu-id="9b6d5-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="9b6d5-109">範例</span><span class="sxs-lookup"><span data-stu-id="9b6d5-109">Example</span></span>  
 <span data-ttu-id="9b6d5-110">下列程式碼顯示完整的範例。</span><span class="sxs-lookup"><span data-stu-id="9b6d5-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9b6d5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b6d5-111">See Also</span></span>  
 [<span data-ttu-id="9b6d5-112">建立立體轉譯動畫</span><span class="sxs-lookup"><span data-stu-id="9b6d5-112">Animate 3-D Translations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)  
 [<span data-ttu-id="9b6d5-113">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="9b6d5-113">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="9b6d5-114">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="9b6d5-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
