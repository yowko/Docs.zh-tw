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
# <a name="how-to-animate-3-d-translations"></a>HOW TO：建立立體轉譯動畫
本主題示範如何以動畫顯示上設定的轉譯轉換[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型。  
  
 下列程式碼顯示如何應用<xref:System.Windows.Media.Media3D.TranslateTransform3D>物件至<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>屬性的<xref:System.Windows.Media.Media3D.TranslateTransform3D>物件以動畫顯示下列程式碼。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>範例  
 下列程式碼顯示整個範例。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱
- [動畫概觀](animation-overview.md)
- [建立立體場景](how-to-create-a-3-d-scene.md)
- [立體圖形概觀](3-d-graphics-overview.md)
- [轉換概觀](transforms-overview.md)
