---
title: HOW TO：使用快取項目當做筆刷
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: 7ff0e9eb131faaed3874995ee137126eac31f43d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597927"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="0d048-102">HOW TO：使用快取項目當做筆刷</span><span class="sxs-lookup"><span data-stu-id="0d048-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="0d048-103">使用<xref:System.Windows.Media.BitmapCacheBrush>類別，以有效率地重複使用的快取的項目。</span><span class="sxs-lookup"><span data-stu-id="0d048-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="0d048-104">若要快取項目，建立的新執行個體<xref:System.Windows.Media.BitmapCache>類別，並將它指派給項目的<xref:System.Windows.UIElement.CacheMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0d048-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d048-105">範例</span><span class="sxs-lookup"><span data-stu-id="0d048-105">Example</span></span>  
 <span data-ttu-id="0d048-106">下列程式碼範例示範如何重複使用的快取的項目。</span><span class="sxs-lookup"><span data-stu-id="0d048-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="0d048-107">快取的項目是<xref:System.Windows.Controls.Image>顯示大型影像的控制項。</span><span class="sxs-lookup"><span data-stu-id="0d048-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="0d048-108"><xref:System.Windows.Controls.Image>控制項為點陣圖快取使用<xref:System.Windows.Media.BitmapCache>類別，而快取會重複使用將它指派給<xref:System.Windows.Media.BitmapCacheBrush>。</span><span class="sxs-lookup"><span data-stu-id="0d048-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="0d048-109">若要顯示有效重複使用，筆刷會指派給 25 個按鈕的背景。</span><span class="sxs-lookup"><span data-stu-id="0d048-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="0d048-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d048-110">See also</span></span>
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="0d048-111">如何：透過快取元素改善轉譯效能</span><span class="sxs-lookup"><span data-stu-id="0d048-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
