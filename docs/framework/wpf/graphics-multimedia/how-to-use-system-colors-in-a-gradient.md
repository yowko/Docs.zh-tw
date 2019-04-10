---
title: HOW TO：在漸層中使用系統色彩
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 55c99640907a0c372f8c7bbc50b9b45c9f15ef3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229436"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="a08b0-102">HOW TO：在漸層中使用系統色彩</span><span class="sxs-lookup"><span data-stu-id="a08b0-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="a08b0-103">若要使用系統色彩漸層中，您使用 *\<Systemcolor> >* 色彩並 *\<Systemcolor> >* ColorKey 靜態屬性<xref:System.Windows.SystemColors>類別來取得參考的色彩，其中 *\<Systemcolor> >* 是所需的系統色彩的名稱。</span><span class="sxs-lookup"><span data-stu-id="a08b0-103">To use a system color in a gradient, you use the *\<SystemColor>* Color and *\<SystemColor>* ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="a08b0-104">使用 *\<Systemcolor> >* ColorKey 屬性，當您想要建立動態參考時，系統佈景主題變更時自動更新。</span><span class="sxs-lookup"><span data-stu-id="a08b0-104">Use the *\<SystemColor>* ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="a08b0-105">否則，請使用 *\<Systemcolor> >* Color 屬性。</span><span class="sxs-lookup"><span data-stu-id="a08b0-105">Otherwise, use the *\<SystemColor>* Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a08b0-106">範例</span><span class="sxs-lookup"><span data-stu-id="a08b0-106">Example</span></span>  
 <span data-ttu-id="a08b0-107">下列範例使用動態系統色彩資源來建立漸層。</span><span class="sxs-lookup"><span data-stu-id="a08b0-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="a08b0-108">下列範例使用靜態系統色彩資源來建立漸層。</span><span class="sxs-lookup"><span data-stu-id="a08b0-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a08b0-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a08b0-109">See also</span></span>

- <xref:System.Windows.SystemColors>
- [<span data-ttu-id="a08b0-110">使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="a08b0-110">Paint an Area with a System Brush</span></span>](how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="a08b0-111">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="a08b0-111">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
