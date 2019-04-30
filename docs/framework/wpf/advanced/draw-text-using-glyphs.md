---
title: 使用圖像繪製文字
ms.date: 03/30/2017
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
ms.openlocfilehash: 55bbc50de519d6607a843fcd633f2c07db53109f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010367"
---
# <a name="draw-text-using-glyphs"></a>使用圖像繪製文字
本主題說明如何使用低階<xref:System.Windows.Documents.Glyphs>要顯示的文字物件[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
## <a name="example"></a>範例  
 下列範例示範如何定義的屬性<xref:System.Windows.Documents.Glyphs>物件中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 <xref:System.Windows.Documents.Glyphs>物件所表示的輸出<xref:System.Windows.Media.GlyphRun>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 此範例假設 Arial、Courier New 和 Times New Roman 字型會安裝在本機電腦的 C:\WINDOWS\Fonts 資料夾。  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 此範例示範如何定義的其他屬性<xref:System.Windows.Documents.Glyphs>中的物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>另請參閱

- [WPF 中的印刷樣式](typography-in-wpf.md)
