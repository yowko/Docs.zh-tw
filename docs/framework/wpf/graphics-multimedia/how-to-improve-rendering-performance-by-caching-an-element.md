---
title: HOW TO：透過快取項目改善轉譯效能
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: 118e8b0cca52c44788c9d5b291d710f765e7af2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947273"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a><span data-ttu-id="1f8e9-102">HOW TO：透過快取項目改善轉譯效能</span><span class="sxs-lookup"><span data-stu-id="1f8e9-102">How to: Improve Rendering Performance by Caching an Element</span></span>
<span data-ttu-id="1f8e9-103">使用<xref:System.Windows.Media.BitmapCache>類別來改善轉譯效能複雜<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="1f8e9-103">Use the <xref:System.Windows.Media.BitmapCache> class to improve rendering performance of a complex <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="1f8e9-104">若要快取項目，建立的新執行個體<xref:System.Windows.Media.BitmapCache>類別，並將它指派給項目的<xref:System.Windows.UIElement.CacheMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1f8e9-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span> <span data-ttu-id="1f8e9-105">您可以重複使用<xref:System.Windows.Media.BitmapCache>有效率地在<xref:System.Windows.Media.BitmapCacheBrush>。</span><span class="sxs-lookup"><span data-stu-id="1f8e9-105">You can reuse a <xref:System.Windows.Media.BitmapCache> efficiently in a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f8e9-106">範例</span><span class="sxs-lookup"><span data-stu-id="1f8e9-106">Example</span></span>  
 <span data-ttu-id="1f8e9-107">下列程式碼範例示範如何建立複雜的項目，並加以快取為點陣圖，進而改善效能，當項目以動畫顯示。</span><span class="sxs-lookup"><span data-stu-id="1f8e9-107">The following code example shows how to create a complex element and cache it as a bitmap, which improves performance when the element is animated.</span></span> <span data-ttu-id="1f8e9-108">元素是包含具有許多頂點的圖形幾何的畫布。</span><span class="sxs-lookup"><span data-stu-id="1f8e9-108">The element is a canvas that holds shape geometries with many vertices.</span></span> <span data-ttu-id="1f8e9-109">A<xref:System.Windows.Media.BitmapCache>使用預設值指派給<xref:System.Windows.UIElement.CacheMode%2A>畫布範圍，請和動畫顯示的快取的點陣圖 smooth 縮放比例。</span><span class="sxs-lookup"><span data-stu-id="1f8e9-109">A <xref:System.Windows.Media.BitmapCache> with default values is assigned to the <xref:System.Windows.UIElement.CacheMode%2A> of the canvas, and an animation shows the smooth scaling of the cached bitmap.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a><span data-ttu-id="1f8e9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f8e9-110">See also</span></span>

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="1f8e9-111">如何：使用快取項目當做筆刷</span><span class="sxs-lookup"><span data-stu-id="1f8e9-111">How to: Use a Cached Element as a Brush</span></span>](how-to-use-a-cached-element-as-a-brush.md)
