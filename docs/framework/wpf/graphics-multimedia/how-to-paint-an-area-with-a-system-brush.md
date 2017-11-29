---
title: "操作說明：使用系統筆刷繪製區域"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 355df3718d90768cdfa8bc9780c44c19eb4bf9bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="d09be-102">操作說明：使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="d09be-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="d09be-103"><xref:System.Windows.SystemColors>類別提供的存取權系統筆刷和色彩，例如<xref:System.Windows.SystemColors.ControlBrush%2A>， <xref:System.Windows.SystemColors.ControlBrushKey%2A>，和<xref:System.Windows.SystemColors.DesktopBrush%2A>。</span><span class="sxs-lookup"><span data-stu-id="d09be-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="d09be-104">系統筆刷<xref:System.Windows.Media.SolidColorBrush>使用指定的系統色彩繪製區域的物件。</span><span class="sxs-lookup"><span data-stu-id="d09be-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="d09be-105">系統筆刷只能產生純色填滿，因此無法用於產生漸層。</span><span class="sxs-lookup"><span data-stu-id="d09be-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="d09be-106">您可以將系統筆刷當作靜態或動態資源來使用。</span><span class="sxs-lookup"><span data-stu-id="d09be-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="d09be-107">當應用程式在執行時，如果您想要在使用者變更系統筆刷時自動更新筆刷，請使用動態資源；否則請使用靜態資源。</span><span class="sxs-lookup"><span data-stu-id="d09be-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="d09be-108">SystemColors 類別包含多種遵循嚴格命名慣例的靜態屬性：</span><span class="sxs-lookup"><span data-stu-id="d09be-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="d09be-109">*\<SystemColor>*Brush</span><span class="sxs-lookup"><span data-stu-id="d09be-109">*\<SystemColor>*Brush</span></span>  
  
     <span data-ttu-id="d09be-110">取得靜態參考<xref:System.Windows.Media.SolidColorBrush>之指定的系統色彩。</span><span class="sxs-lookup"><span data-stu-id="d09be-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="d09be-111">*\<SystemColor>*BrushKey</span><span class="sxs-lookup"><span data-stu-id="d09be-111">*\<SystemColor>*BrushKey</span></span>  
  
     <span data-ttu-id="d09be-112">取得動態參考<xref:System.Windows.Media.SolidColorBrush>之指定的系統色彩。</span><span class="sxs-lookup"><span data-stu-id="d09be-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="d09be-113">*\<SystemColor>*Color</span><span class="sxs-lookup"><span data-stu-id="d09be-113">*\<SystemColor>*Color</span></span>  
  
     <span data-ttu-id="d09be-114">取得靜態參考<xref:System.Windows.Media.Color>結構指定的系統色彩。</span><span class="sxs-lookup"><span data-stu-id="d09be-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="d09be-115">*\<SystemColor>*ColorKey</span><span class="sxs-lookup"><span data-stu-id="d09be-115">*\<SystemColor>*ColorKey</span></span>  
  
     <span data-ttu-id="d09be-116">取得動態參考<xref:System.Windows.Media.Color>結構指定的系統色彩。</span><span class="sxs-lookup"><span data-stu-id="d09be-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="d09be-117">系統色彩是<xref:System.Windows.Media.Color>可用來設定筆刷的結構。</span><span class="sxs-lookup"><span data-stu-id="d09be-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="d09be-118">例如，您可以建立使用系統色彩設定為漸層<xref:System.Windows.Media.GradientStop.Color%2A>屬性<xref:System.Windows.Media.LinearGradientBrush>物件的系統色彩與漸層停駐。</span><span class="sxs-lookup"><span data-stu-id="d09be-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="d09be-119">如需範例，請參閱[漸層中使用系統色彩](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)。</span><span class="sxs-lookup"><span data-stu-id="d09be-119">For an example, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d09be-120">範例</span><span class="sxs-lookup"><span data-stu-id="d09be-120">Example</span></span>  
 <span data-ttu-id="d09be-121">下列範例使用動態系統筆刷參考來設定按鈕的 Background。</span><span class="sxs-lookup"><span data-stu-id="d09be-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="d09be-122">下一個範例使用靜態系統筆刷參考來設定按鈕的 Background。</span><span class="sxs-lookup"><span data-stu-id="d09be-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="d09be-123">如需示範如何使用系統色彩漸層中的範例，請參閱[漸層中使用系統色彩](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)。</span><span class="sxs-lookup"><span data-stu-id="d09be-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09be-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d09be-124">See Also</span></span>  
 [<span data-ttu-id="d09be-125">在漸層中使用系統色彩</span><span class="sxs-lookup"><span data-stu-id="d09be-125">Use System Colors in a Gradient</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [<span data-ttu-id="d09be-126">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="d09be-126">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
