---
title: 逐步解說：建立自訂動畫按鈕
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10d723f8a685d76cc739ac88770aad3e1de982ca
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="ead69-102">逐步解說：建立自訂動畫按鈕</span><span class="sxs-lookup"><span data-stu-id="ead69-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="ead69-103">如其名所示，Windows Presentation Foundation (WPF) 適合用來對客戶的豐富經驗。</span><span class="sxs-lookup"><span data-stu-id="ead69-103">As its name suggests, Windows Presentation Foundation (WPF) is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="ead69-104">這些逐步解說會示範如何自訂的外觀和行為 （包括動畫） 的按鈕。</span><span class="sxs-lookup"><span data-stu-id="ead69-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="ead69-105">完成這項自訂，讓您可以套用這個自訂按鈕輕鬆地至任何按鈕在應用程式中使用的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="ead69-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="ead69-106">下圖將顯示您將建立的自訂的按鈕。</span><span class="sxs-lookup"><span data-stu-id="ead69-106">The following illustration shows the customized button that you will create.</span></span>  
  
 <span data-ttu-id="ead69-107">![您將建立的自訂的按鈕](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="ead69-107">![The customized button that you will create](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>  
  
 <span data-ttu-id="ead69-108">向量圖形組成按鈕的外觀會建立使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ead69-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="ead69-109"> 將會功能更強大且可延伸，則會是類似於 HTML。</span><span class="sxs-lookup"><span data-stu-id="ead69-109"> is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="ead69-110"> 您可以在使用 Microsoft Visual Studio 或在 [記事本]，以手動方式輸入，或者您可以使用視覺化設計工具，例如 Microsoft Expression Blend。</span><span class="sxs-lookup"><span data-stu-id="ead69-110"> can be typed in manually using Microsoft Visual Studio or Notepad, or you can use a visual design tool such as Microsoft Expression Blend.</span></span> <span data-ttu-id="ead69-111">Expression Blend 的運作方式是建立基礎[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]程式碼，因此這兩種方法建立相同的圖形。</span><span class="sxs-lookup"><span data-stu-id="ead69-111">Expression Blend works by creating underlying [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code, so both methods create the same graphics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ead69-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="ead69-112">In This Section</span></span>  
 [<span data-ttu-id="ead69-113">使用 Microsoft Expression Blend 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="ead69-113">Create a Button by Using Microsoft Expression Blend</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 <span data-ttu-id="ead69-114">示範如何建立具有自訂行為的按鈕，使用 Expression Blend 設計工具功能。</span><span class="sxs-lookup"><span data-stu-id="ead69-114">Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>  
  
 [<span data-ttu-id="ead69-115">使用 XAML 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="ead69-115">Create a Button by Using XAML</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 <span data-ttu-id="ead69-116">示範如何建立具有自訂行為的按鈕，使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ead69-116">Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and Visual Studio.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ead69-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="ead69-117">Related Sections</span></span>  
 [<span data-ttu-id="ead69-118">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="ead69-118">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 <span data-ttu-id="ead69-119">描述如何判斷的外觀和行為的控制項使用樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="ead69-119">Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>  
  
 [<span data-ttu-id="ead69-120">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="ead69-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 <span data-ttu-id="ead69-121">描述如何繪製物件，使用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]動畫和計時系統。</span><span class="sxs-lookup"><span data-stu-id="ead69-121">Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>  
  
 [<span data-ttu-id="ead69-122">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="ead69-122">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 <span data-ttu-id="ead69-123">描述如何使用筆刷物件來使用純色，線性漸層和放射狀漸層繪製。</span><span class="sxs-lookup"><span data-stu-id="ead69-123">Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>  
  
 [<span data-ttu-id="ead69-124">點陣圖效果概觀</span><span class="sxs-lookup"><span data-stu-id="ead69-124">Bitmap Effects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)  
 <span data-ttu-id="ead69-125">描述所支援的點陣圖效果[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]並說明如何將其套用。</span><span class="sxs-lookup"><span data-stu-id="ead69-125">Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>
