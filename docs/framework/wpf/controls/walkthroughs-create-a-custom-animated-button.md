---
title: 逐步解說：建立自訂動畫按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
ms.openlocfilehash: a3990a7dc446c264e0865e15dadcdaf3ba0a0ff6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460058"
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="6ed7e-102">逐步解說：建立自訂動畫按鈕</span><span class="sxs-lookup"><span data-stu-id="6ed7e-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="6ed7e-103">正如其名，Windows Presentation Foundation （WPF）非常適合為客戶提供豐富的呈現體驗。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-103">As its name suggests, Windows Presentation Foundation (WPF) is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="6ed7e-104">這些逐步解說示範如何自訂按鈕的外觀和行為（包括動畫）。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="6ed7e-105">這項自訂作業是使用樣式和範本來完成，因此您可以輕鬆地將此自訂按鈕套用至應用程式中的任何按鈕。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="6ed7e-106">下圖顯示您將建立的自訂按鈕。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-106">The following illustration shows the customized button that you will create.</span></span>

 <span data-ttu-id="6ed7e-107">![您將建立的自訂按鈕](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="6ed7e-107">![The customized button that you will create](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>

 <span data-ttu-id="6ed7e-108">組成按鈕外觀的向量圖形是使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]所建立。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="6ed7e-109">類似于 HTML，不同之處在于它更強大且可擴充。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-109">is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="6ed7e-110">可以使用 Visual Studio 或記事本以手動方式輸入，或者您也可以使用像是 Blend for Visual Studio 的視覺化設計工具。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-110">can be typed in manually using Visual Studio or Notepad, or you can use a visual design tool such as Blend for Visual Studio.</span></span> <span data-ttu-id="6ed7e-111">Blend 的運作方式是建立基礎 XAML 程式碼，因此這兩種方法都會建立相同的圖形。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-111">Blend works by creating underlying XAML code, so both methods create the same graphics.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6ed7e-112">本章節內容</span><span class="sxs-lookup"><span data-stu-id="6ed7e-112">In This Section</span></span>
 <span data-ttu-id="6ed7e-113">[使用 Microsoft Expression Blend 建立按鈕](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)示範如何使用 Expression Blend 的設計工具功能，建立具有自訂行為的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-113">[Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md) Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>

 <span data-ttu-id="6ed7e-114">[使用 XAML 建立按鈕](walkthrough-create-a-button-by-using-xaml.md)示範如何使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和 Visual Studio，建立具有自訂行為的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-114">[Create a Button by Using XAML](walkthrough-create-a-button-by-using-xaml.md) Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and Visual Studio.</span></span>

## <a name="related-sections"></a><span data-ttu-id="6ed7e-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="6ed7e-115">Related Sections</span></span>
 <span data-ttu-id="6ed7e-116">[樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)描述如何使用樣式和範本來決定控制項的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-116">[Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md) Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>

 <span data-ttu-id="6ed7e-117">[動畫總覽](../graphics-multimedia/animation-overview.md)描述如何使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 動畫和計時系統來製作物件的動畫。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-117">[Animation Overview](../graphics-multimedia/animation-overview.md) Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>

 <span data-ttu-id="6ed7e-118">[使用純色和漸層繪製的色彩總覽](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)描述如何使用筆刷物件，以純色、線性漸層和放射狀漸層繪製。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-118">[Painting with Solid Colors and Gradients Overview](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>

 <span data-ttu-id="6ed7e-119">[點陣圖效果總覽](../graphics-multimedia/bitmap-effects-overview.md)描述 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 支援的點陣圖效果，並說明如何套用它們。</span><span class="sxs-lookup"><span data-stu-id="6ed7e-119">[Bitmap Effects Overview](../graphics-multimedia/bitmap-effects-overview.md) Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>
