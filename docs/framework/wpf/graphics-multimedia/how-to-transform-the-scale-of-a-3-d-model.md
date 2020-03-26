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
# <a name="how-to-transform-the-scale-of-a-3d-model"></a>如何：變換 3D 模型的比例
此示例演示如何縮放 3D 物件。 要縮放 3D 物件，請使用<xref:System.Windows.Media.Media3D.ScaleTransform3D>。 和<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>屬性按指定的因數調整元素的大小。 例如，<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>值 1.5 將物件拉伸到其原始寬度的 150%。 值<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>0.5 將物件的高度縮小 50%。 下面的代碼顯示使用 作為<xref:System.Windows.Media.Media3D.ScaleTransform3D>轉換。 <xref:System.Windows.Media.Media3D.GeometryModel3D>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>範例  
 以下代碼顯示整個示例。  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [動畫 3D 翻譯](how-to-animate-3-d-translations.md)
- [創建 3D 場景](how-to-create-a-3-d-scene.md)
- [3D 圖形概述](3-d-graphics-overview.md)
