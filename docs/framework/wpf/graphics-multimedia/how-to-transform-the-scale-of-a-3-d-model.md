---
title: HOW TO：轉換立體模型的比例
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 13f718451cb1b753a41304efde7db55360d3f687
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672884"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a><span data-ttu-id="90ead-102">HOW TO：轉換立體模型的比例</span><span class="sxs-lookup"><span data-stu-id="90ead-102">How to: Transform the Scale of a 3-D Model</span></span>
<span data-ttu-id="90ead-103">此範例示範如何調整 3d 物件。</span><span class="sxs-lookup"><span data-stu-id="90ead-103">This example shows how to scale a 3-D object.</span></span> <span data-ttu-id="90ead-104">若要調整的 3d 物件，使用<xref:System.Windows.Media.Media3D.ScaleTransform3D>。</span><span class="sxs-lookup"><span data-stu-id="90ead-104">To scale a 3-D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="90ead-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>， <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>，和<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>所指定的因數調整元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="90ead-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="90ead-106">比方說，<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>的 1.5 倍的值會自動縮放其原始寬度的 150%的物件。</span><span class="sxs-lookup"><span data-stu-id="90ead-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="90ead-107">A<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>值為 0.5 百分之 50 壓縮物件的高度。</span><span class="sxs-lookup"><span data-stu-id="90ead-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="90ead-108">下列程式碼示範使用<xref:System.Windows.Media.Media3D.ScaleTransform3D>轉換為<xref:System.Windows.Media.Media3D.GeometryModel3D>。</span><span class="sxs-lookup"><span data-stu-id="90ead-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="90ead-109">範例</span><span class="sxs-lookup"><span data-stu-id="90ead-109">Example</span></span>  
 <span data-ttu-id="90ead-110">下列程式碼顯示整個範例。</span><span class="sxs-lookup"><span data-stu-id="90ead-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="90ead-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90ead-111">See also</span></span>
- [<span data-ttu-id="90ead-112">建立立體轉譯動畫</span><span class="sxs-lookup"><span data-stu-id="90ead-112">Animate 3-D Translations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)
- [<span data-ttu-id="90ead-113">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="90ead-113">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="90ead-114">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="90ead-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
