---
title: 如何：套用繪圖至立體模型
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 311a3ac1d9fa219a3a365d506d9d0c3e8b6bc229
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459363"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>如何：套用繪圖至立體模型

這個範例示範如何使用 <xref:System.Windows.Media.DrawingBrush> 做為 <xref:System.Windows.Media.Media3D.Material> 套用至3D 模型的方式。

下列程式碼會將 <xref:System.Windows.Media.DrawingGroup> 定義為 <xref:System.Windows.Media.DrawingBrush>的內容。  <xref:System.Windows.Media.DrawingBrush> 會設定為套用至立體平面之 <xref:System.Windows.Media.Media3D.DiffuseMaterial> 的 <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> 屬性。

> [!NOTE]
> 您通常會想要定義複雜的物件和值，如下圖所示，做為可重複使用並簡化程式碼的資源。 如需詳細資訊，請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>範例

下列程式碼顯示整個範例。

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>請參閱

- [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [建立立體場景](how-to-create-a-3-d-scene.md)
- [繪圖物件概觀](drawing-objects-overview.md)
- [立體圖形概觀](3-d-graphics-overview.md)
