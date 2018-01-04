---
title: "如何：將快取的項目當做筆刷使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f463c15855e267a4c246625a8d06e627852f48a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="f86de-102">如何：將快取的項目當做筆刷使用</span><span class="sxs-lookup"><span data-stu-id="f86de-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="f86de-103">使用<xref:System.Windows.Media.BitmapCacheBrush>有效率地重複使用快取之元素的類別。</span><span class="sxs-lookup"><span data-stu-id="f86de-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="f86de-104">若要快取項目，建立的新執行個體<xref:System.Windows.Media.BitmapCache>類別，並將它指派給項目的<xref:System.Windows.UIElement.CacheMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f86de-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f86de-105">範例</span><span class="sxs-lookup"><span data-stu-id="f86de-105">Example</span></span>  
 <span data-ttu-id="f86de-106">下列程式碼範例示範如何重複使用快取的項目。</span><span class="sxs-lookup"><span data-stu-id="f86de-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="f86de-107">快取項目，則<xref:System.Windows.Controls.Image>顯示大型影像的控制項。</span><span class="sxs-lookup"><span data-stu-id="f86de-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="f86de-108"><xref:System.Windows.Controls.Image>控制項使用快取為點陣圖<xref:System.Windows.Media.BitmapCache>類別和快取會重複使用所指派到<xref:System.Windows.Media.BitmapCacheBrush>。</span><span class="sxs-lookup"><span data-stu-id="f86de-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="f86de-109">筆刷顯示有效率地重複使用指派給 25 個按鈕的背景。</span><span class="sxs-lookup"><span data-stu-id="f86de-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="f86de-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="f86de-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="f86de-111">操作說明：透過快取元素改善轉譯效能</span><span class="sxs-lookup"><span data-stu-id="f86de-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
