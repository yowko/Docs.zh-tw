---
title: 如何：將繪圖應用於 3D 模型
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112176"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a>如何：將繪圖應用於 3D 模型

此示例演示如何將<xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.Material>

以下代碼將 定義為<xref:System.Windows.Media.DrawingGroup>的內容。 <xref:System.Windows.Media.DrawingBrush>  <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>設置為<xref:System.Windows.Media.Media3D.DiffuseMaterial>應用於 3D 平面的屬性。

> [!NOTE]
> 通常，最好將複雜的物件和值（如下圖）定義為可以重用和簡化代碼的資源。 有關詳細資訊，請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>範例

以下代碼顯示整個示例。

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>另請參閱

- [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [創建 3D 場景](how-to-create-a-3-d-scene.md)
- [繪圖物件概觀](drawing-objects-overview.md)
- [3D 圖形概述](3-d-graphics-overview.md)
