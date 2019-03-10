---
title: 限制 GDI+ 中的繪圖介面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: da12ece815d8ae9d1f974b02198498b250885843
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717111"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>限制 GDI+ 中的繪圖介面
裁剪是指限制為特定的矩形或區域的繪製。 下圖顯示的字串"Hello"裁剪到心形區域。  
  
 ![受限制的繪圖介面](./media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>使用區域的裁剪  
 區域可以建構從路徑，以及路徑可以包含字串的外框輪廓，因此您可以使用裁剪外框的文字。 下圖顯示一份同心橢圓形內部的文字字串。  
  
 ![受限制的繪圖介面](./media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 若要繪製的裁剪，建立<xref:System.Drawing.Graphics>物件，將其<xref:System.Drawing.Graphics.Clip%2A>屬性，然後呼叫繪製方法的相同<xref:System.Drawing.Graphics>物件：  
  
 [!code-csharp[LinesCurvesAndShapes#91](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [使用區域](using-regions.md)
