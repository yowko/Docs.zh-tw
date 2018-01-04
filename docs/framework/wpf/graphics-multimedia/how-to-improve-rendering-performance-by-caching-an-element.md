---
title: "如何：透過快取項目改善轉譯效能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cd12b811ae4dd89c645ada1f4f70b06f73b9b13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a><span data-ttu-id="bec7c-102">如何：透過快取項目改善轉譯效能</span><span class="sxs-lookup"><span data-stu-id="bec7c-102">How to: Improve Rendering Performance by Caching an Element</span></span>
<span data-ttu-id="bec7c-103">使用<xref:System.Windows.Media.BitmapCache>類別來改善呈現效能複雜<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="bec7c-103">Use the <xref:System.Windows.Media.BitmapCache> class to improve rendering performance of a complex <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="bec7c-104">若要快取項目，建立的新執行個體<xref:System.Windows.Media.BitmapCache>類別，並將它指派給項目的<xref:System.Windows.UIElement.CacheMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="bec7c-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span> <span data-ttu-id="bec7c-105">您可以重複使用<xref:System.Windows.Media.BitmapCache>有效率地在<xref:System.Windows.Media.BitmapCacheBrush>。</span><span class="sxs-lookup"><span data-stu-id="bec7c-105">You can reuse a <xref:System.Windows.Media.BitmapCache> efficiently in a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bec7c-106">範例</span><span class="sxs-lookup"><span data-stu-id="bec7c-106">Example</span></span>  
 <span data-ttu-id="bec7c-107">下列程式碼範例示範如何建立複雜的項目並快取在稱為點陣圖，進而改善效能時的動畫項目。</span><span class="sxs-lookup"><span data-stu-id="bec7c-107">The following code example shows how to create a complex element and cache it as a bitmap, which improves performance when the element is animated.</span></span> <span data-ttu-id="bec7c-108">元素是保存有許多頂點圖形幾何的畫布。</span><span class="sxs-lookup"><span data-stu-id="bec7c-108">The element is a canvas that holds shape geometries with many vertices.</span></span> <span data-ttu-id="bec7c-109">A<xref:System.Windows.Media.BitmapCache>與預設值指派給<xref:System.Windows.UIElement.CacheMode%2A>畫布範圍，請和動畫顯示的快取點陣圖 smooth 縮放比例。</span><span class="sxs-lookup"><span data-stu-id="bec7c-109">A <xref:System.Windows.Media.BitmapCache> with default values is assigned to the <xref:System.Windows.UIElement.CacheMode%2A> of the canvas, and an animation shows the smooth scaling of the cached bitmap.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a><span data-ttu-id="bec7c-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="bec7c-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="bec7c-111">操作說明：將快取的元素當做筆刷使用</span><span class="sxs-lookup"><span data-stu-id="bec7c-111">How to: Use a Cached Element as a Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
