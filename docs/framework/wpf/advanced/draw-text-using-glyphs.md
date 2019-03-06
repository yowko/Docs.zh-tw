---
title: 使用圖像繪製文字
ms.date: 03/30/2017
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
ms.openlocfilehash: 155f0b756b43ad8cfd0ddde63a5e86854f5f1624
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363003"
---
# <a name="draw-text-using-glyphs"></a><span data-ttu-id="70ab6-102">使用圖像繪製文字</span><span class="sxs-lookup"><span data-stu-id="70ab6-102">Draw Text Using Glyphs</span></span>
<span data-ttu-id="70ab6-103">本主題說明如何使用低階<xref:System.Windows.Documents.Glyphs>要顯示的文字物件[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="70ab6-103">This topic explains how to use the low-level <xref:System.Windows.Documents.Glyphs> object to display text in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="70ab6-104">範例</span><span class="sxs-lookup"><span data-stu-id="70ab6-104">Example</span></span>  
 <span data-ttu-id="70ab6-105">下列範例示範如何定義的屬性<xref:System.Windows.Documents.Glyphs>物件中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="70ab6-105">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="70ab6-106"><xref:System.Windows.Documents.Glyphs>物件所表示的輸出<xref:System.Windows.Media.GlyphRun>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="70ab6-106">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="70ab6-107">此範例假設 Arial、Courier New 和 Times New Roman 字型會安裝在本機電腦的 C:\WINDOWS\Fonts 資料夾。</span><span class="sxs-lookup"><span data-stu-id="70ab6-107">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the C:\WINDOWS\Fonts folder on the local computer.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="70ab6-108">此範例示範如何定義的其他屬性<xref:System.Windows.Documents.Glyphs>中的物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="70ab6-108">This example shows how to define other properties of <xref:System.Windows.Documents.Glyphs> objects in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="70ab6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70ab6-109">See also</span></span>
- [<span data-ttu-id="70ab6-110">WPF 中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="70ab6-110">Typography in WPF</span></span>](typography-in-wpf.md)
