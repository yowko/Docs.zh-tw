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
# <a name="how-to-animate-3d-translations"></a>如何：動畫 3D 翻譯
本主題演示如何在 3D 模型上為轉換轉換集設置動畫。  
  
 下面的代碼顯示了<xref:System.Windows.Media.Media3D.TranslateTransform3D>物件對<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>的應用。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 此<xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A><xref:System.Windows.Media.Media3D.TranslateTransform3D>物件的屬性使用以下代碼進行動畫處理。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>範例  
 以下代碼顯示整個示例。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [創建 3D 場景](how-to-create-a-3-d-scene.md)
- [3D 圖形概述](3-d-graphics-overview.md)
- [轉換概觀](transforms-overview.md)
