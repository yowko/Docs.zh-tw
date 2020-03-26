---
title: 如何：變換 3D 模型的比例
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111981"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a><span data-ttu-id="265c9-102">如何：變換 3D 模型的比例</span><span class="sxs-lookup"><span data-stu-id="265c9-102">How to: Transform the Scale of a 3D Model</span></span>
<span data-ttu-id="265c9-103">此示例演示如何縮放 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="265c9-103">This example shows how to scale a 3D object.</span></span> <span data-ttu-id="265c9-104">要縮放 3D 物件，請使用<xref:System.Windows.Media.Media3D.ScaleTransform3D>。</span><span class="sxs-lookup"><span data-stu-id="265c9-104">To scale a 3D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="265c9-105">和<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>屬性按指定的因數調整元素的大小。</span><span class="sxs-lookup"><span data-stu-id="265c9-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="265c9-106">例如，<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>值 1.5 將物件拉伸到其原始寬度的 150%。</span><span class="sxs-lookup"><span data-stu-id="265c9-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="265c9-107">值<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>0.5 將物件的高度縮小 50%。</span><span class="sxs-lookup"><span data-stu-id="265c9-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="265c9-108">下面的代碼顯示使用 作為<xref:System.Windows.Media.Media3D.ScaleTransform3D>轉換。 <xref:System.Windows.Media.Media3D.GeometryModel3D></span><span class="sxs-lookup"><span data-stu-id="265c9-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="265c9-109">範例</span><span class="sxs-lookup"><span data-stu-id="265c9-109">Example</span></span>  
 <span data-ttu-id="265c9-110">以下代碼顯示整個示例。</span><span class="sxs-lookup"><span data-stu-id="265c9-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="265c9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="265c9-111">See also</span></span>

- [<span data-ttu-id="265c9-112">動畫 3D 翻譯</span><span class="sxs-lookup"><span data-stu-id="265c9-112">Animate 3D Translations</span></span>](how-to-animate-3-d-translations.md)
- [<span data-ttu-id="265c9-113">創建 3D 場景</span><span class="sxs-lookup"><span data-stu-id="265c9-113">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="265c9-114">3D 圖形概述</span><span class="sxs-lookup"><span data-stu-id="265c9-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
