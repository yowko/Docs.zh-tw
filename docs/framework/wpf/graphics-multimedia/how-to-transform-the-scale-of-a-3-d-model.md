---
title: HOW TO：轉換立體模型的比例
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 6d668de08201d819ce9f8752bedf6c388a6bc718
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769326"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a><span data-ttu-id="26621-102">HOW TO：轉換立體模型的比例</span><span class="sxs-lookup"><span data-stu-id="26621-102">How to: Transform the Scale of a 3-D Model</span></span>
<span data-ttu-id="26621-103">此範例示範如何調整 3d 物件。</span><span class="sxs-lookup"><span data-stu-id="26621-103">This example shows how to scale a 3-D object.</span></span> <span data-ttu-id="26621-104">若要調整的 3d 物件，使用<xref:System.Windows.Media.Media3D.ScaleTransform3D>。</span><span class="sxs-lookup"><span data-stu-id="26621-104">To scale a 3-D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="26621-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>， <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>，和<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>所指定的因數調整元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="26621-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="26621-106">比方說，<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>的 1.5 倍的值會自動縮放其原始寬度的 150%的物件。</span><span class="sxs-lookup"><span data-stu-id="26621-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="26621-107">A<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>值為 0.5 百分之 50 壓縮物件的高度。</span><span class="sxs-lookup"><span data-stu-id="26621-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="26621-108">下列程式碼示範使用<xref:System.Windows.Media.Media3D.ScaleTransform3D>轉換為<xref:System.Windows.Media.Media3D.GeometryModel3D>。</span><span class="sxs-lookup"><span data-stu-id="26621-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="26621-109">範例</span><span class="sxs-lookup"><span data-stu-id="26621-109">Example</span></span>  
 <span data-ttu-id="26621-110">下列程式碼顯示整個範例。</span><span class="sxs-lookup"><span data-stu-id="26621-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="26621-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26621-111">See also</span></span>

- [<span data-ttu-id="26621-112">建立立體轉譯動畫</span><span class="sxs-lookup"><span data-stu-id="26621-112">Animate 3-D Translations</span></span>](how-to-animate-3-d-translations.md)
- [<span data-ttu-id="26621-113">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="26621-113">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="26621-114">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="26621-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
