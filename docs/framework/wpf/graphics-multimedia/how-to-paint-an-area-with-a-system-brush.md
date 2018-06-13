---
title: 操作說明：使用系統筆刷繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: f8a66ffc283016d65a17b33e98ce28fe4cd1c242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561143"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="eae71-102">操作說明：使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="eae71-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="eae71-103"><xref:System.Windows.SystemColors>類別提供的存取權系統筆刷和色彩，例如<xref:System.Windows.SystemColors.ControlBrush%2A>， <xref:System.Windows.SystemColors.ControlBrushKey%2A>，和<xref:System.Windows.SystemColors.DesktopBrush%2A>。</span><span class="sxs-lookup"><span data-stu-id="eae71-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="eae71-104">系統筆刷<xref:System.Windows.Media.SolidColorBrush>使用指定的系統色彩繪製區域的物件。</span><span class="sxs-lookup"><span data-stu-id="eae71-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="eae71-105">系統筆刷只能產生純色填滿，因此無法用於產生漸層。</span><span class="sxs-lookup"><span data-stu-id="eae71-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="eae71-106">您可以將系統筆刷當作靜態或動態資源來使用。</span><span class="sxs-lookup"><span data-stu-id="eae71-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="eae71-107">當應用程式在執行時，如果您想要在使用者變更系統筆刷時自動更新筆刷，請使用動態資源；否則請使用靜態資源。</span><span class="sxs-lookup"><span data-stu-id="eae71-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="eae71-108">SystemColors 類別包含多種遵循嚴格命名慣例的靜態屬性：</span><span class="sxs-lookup"><span data-stu-id="eae71-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="eae71-109">*\<SystemColor>* Brush</span><span class="sxs-lookup"><span data-stu-id="eae71-109">*\<SystemColor>* Brush</span></span>  
  
     <span data-ttu-id="eae71-110">取得靜態參考<xref:System.Windows.Media.SolidColorBrush>之指定的系統色彩。</span><span class="sxs-lookup"><span data-stu-id="eae71-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="eae71-111">*\<SystemColor>* BrushKey</span><span class="sxs-lookup"><span data-stu-id="eae71-111">*\<SystemColor>* BrushKey</span></span>  
  
     <span data-ttu-id="eae71-112">取得動態參考<xref:System.Windows.Media.SolidColorBrush>之指定的系統色彩。</span><span class="sxs-lookup"><span data-stu-id="eae71-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="eae71-113">*\<SystemColor>* Color</span><span class="sxs-lookup"><span data-stu-id="eae71-113">*\<SystemColor>* Color</span></span>  
  
     <span data-ttu-id="eae71-114">取得靜態參考<xref:System.Windows.Media.Color>結構指定的系統色彩。</span><span class="sxs-lookup"><span data-stu-id="eae71-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="eae71-115">*\<SystemColor>* ColorKey</span><span class="sxs-lookup"><span data-stu-id="eae71-115">*\<SystemColor>* ColorKey</span></span>  
  
     <span data-ttu-id="eae71-116">取得動態參考<xref:System.Windows.Media.Color>結構指定的系統色彩。</span><span class="sxs-lookup"><span data-stu-id="eae71-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="eae71-117">系統色彩是<xref:System.Windows.Media.Color>可用來設定筆刷的結構。</span><span class="sxs-lookup"><span data-stu-id="eae71-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="eae71-118">例如，您可以建立使用系統色彩設定為漸層<xref:System.Windows.Media.GradientStop.Color%2A>屬性<xref:System.Windows.Media.LinearGradientBrush>物件的系統色彩與漸層停駐。</span><span class="sxs-lookup"><span data-stu-id="eae71-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="eae71-119">如需範例，請參閱[漸層中使用系統色彩](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)。</span><span class="sxs-lookup"><span data-stu-id="eae71-119">For an example, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eae71-120">範例</span><span class="sxs-lookup"><span data-stu-id="eae71-120">Example</span></span>  
 <span data-ttu-id="eae71-121">下列範例使用動態系統筆刷參考來設定按鈕的 Background。</span><span class="sxs-lookup"><span data-stu-id="eae71-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="eae71-122">下一個範例使用靜態系統筆刷參考來設定按鈕的 Background。</span><span class="sxs-lookup"><span data-stu-id="eae71-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="eae71-123">如需示範如何使用系統色彩漸層中的範例，請參閱[漸層中使用系統色彩](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)。</span><span class="sxs-lookup"><span data-stu-id="eae71-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae71-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eae71-124">See Also</span></span>  
 [<span data-ttu-id="eae71-125">在漸層中使用系統色彩</span><span class="sxs-lookup"><span data-stu-id="eae71-125">Use System Colors in a Gradient</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [<span data-ttu-id="eae71-126">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="eae71-126">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
