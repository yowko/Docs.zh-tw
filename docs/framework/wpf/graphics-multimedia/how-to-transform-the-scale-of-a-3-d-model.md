---
title: "如何：轉換立體模型的比例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14f650d968ca715e47269e0765d791856b681237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a>如何：轉換立體模型的比例
此範例顯示如何調整 3d 物件。 若要調整規模 3d 物件，請使用<xref:System.Windows.Media.Media3D.ScaleTransform3D>。 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>， <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>，和<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>屬性調整元素大小依您指定的比例。 例如，<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>值為 1.5 延伸到其原始寬度的 150%的物件。 A<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>值為 0.5 百分之 50 壓縮物件的高度。 下列程式碼示範如何使用<xref:System.Windows.Media.Media3D.ScaleTransform3D>針對轉換為<xref:System.Windows.Media.Media3D.GeometryModel3D>。  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>範例  
 下列程式碼顯示完整的範例。  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>請參閱  
 [建立立體轉譯動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)  
 [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
