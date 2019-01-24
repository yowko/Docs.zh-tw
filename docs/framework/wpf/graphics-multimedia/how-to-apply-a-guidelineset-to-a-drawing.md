---
title: HOW TO：對圖形套用 GuidelineSet
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 4bd2ee349f2c1855a9af6b4c00f2630cd50a9108
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493374"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>HOW TO：對圖形套用 GuidelineSet
此範例示範如何套用<xref:System.Windows.Media.GuidelineSet>至<xref:System.Windows.Media.DrawingGroup>。  
  
 <xref:System.Windows.Media.DrawingGroup>類別是唯一的類型<xref:System.Windows.Media.Drawing>具有<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>屬性。 若要套用<xref:System.Windows.Media.GuidelineSet>至另一種<xref:System.Windows.Media.Drawing>，將它新增至<xref:System.Windows.Media.DrawingGroup>，然後套用<xref:System.Windows.Media.GuidelineSet>至您<xref:System.Windows.Media.DrawingGroup>。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個<xref:System.Windows.Media.DrawingGroup>幾乎完全相同; 唯一的差別是物件： 第二個<xref:System.Windows.Media.DrawingGroup>具有<xref:System.Windows.Media.GuidelineSet>和第一則否。  
  
 下圖顯示範例的輸出。 因為轉譯兩者之間的差異<xref:System.Windows.Media.DrawingGroup>物件太過精巧、 繪圖的部分會放大。  
  
 ![具有與不具 GuidelineSet 的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
