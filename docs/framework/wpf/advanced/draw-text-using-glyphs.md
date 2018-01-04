---
title: "使用圖像繪製文字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55ed079116d0f0e0c168984f16c5ff715667442f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="draw-text-using-glyphs"></a><span data-ttu-id="cae1f-102">使用圖像繪製文字</span><span class="sxs-lookup"><span data-stu-id="cae1f-102">Draw Text Using Glyphs</span></span>
<span data-ttu-id="cae1f-103">本主題說明如何使用低階<xref:System.Windows.Documents.Glyphs>物件中的文字顯示[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cae1f-103">This topic explains how to use the low-level <xref:System.Windows.Documents.Glyphs> object to display text in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="cae1f-104">範例</span><span class="sxs-lookup"><span data-stu-id="cae1f-104">Example</span></span>  
 <span data-ttu-id="cae1f-105">下列範例顯示如何定義屬性<xref:System.Windows.Documents.Glyphs>物件存放至[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cae1f-105">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="cae1f-106"><xref:System.Windows.Documents.Glyphs>物件代表的輸出<xref:System.Windows.Media.GlyphRun>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cae1f-106">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="cae1f-107">此範例假設 Arial、Courier New 和 Times New Roman 字型會安裝在本機電腦的 C:\WINDOWS\Fonts 資料夾。</span><span class="sxs-lookup"><span data-stu-id="cae1f-107">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the C:\WINDOWS\Fonts folder on the local computer.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="cae1f-108">此範例示範如何定義的其他屬性<xref:System.Windows.Documents.Glyphs>中的物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cae1f-108">This example shows how to define other properties of <xref:System.Windows.Documents.Glyphs> objects in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cae1f-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="cae1f-109">See Also</span></span>  
 [<span data-ttu-id="cae1f-110">WPF 中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="cae1f-110">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
