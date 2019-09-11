---
title: HOW TO：對立體模型套用繪圖
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 14470d0adeb948ea46a0720b5713c20fb7d8e6d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855876"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>作法：對立體模型套用繪圖

這個範例示範如何使用<xref:System.Windows.Media.DrawingBrush>做為3d 模型的。 <xref:System.Windows.Media.Media3D.Material>

下列程式碼會將<xref:System.Windows.Media.DrawingGroup>定義為的內容。 <xref:System.Windows.Media.DrawingBrush>  會設定為套用至立體平面的<xref:System.Windows.Media.Media3D.DiffuseMaterial> 屬性。<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> <xref:System.Windows.Media.DrawingBrush>

> [!NOTE]
> 您通常會想要定義複雜的物件和值，如下圖所示，做為可重複使用並簡化程式碼的資源。 如需詳細資訊，請參閱[XAML 資源](../advanced/xaml-resources.md)。

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>範例

下列程式碼顯示整個範例。

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>另請參閱

- [XAML 資源](../advanced/xaml-resources.md)
- [建立立體場景](how-to-create-a-3-d-scene.md)
- [繪圖物件概觀](drawing-objects-overview.md)
- [立體圖形概觀](3-d-graphics-overview.md)
