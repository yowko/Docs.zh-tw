---
title: 逐步解說：建立自訂動畫按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
ms.openlocfilehash: 3c601641a0eb1024722b4f449f0ab23e54fe93dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024465"
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="7c355-102">逐步解說：建立自訂動畫按鈕</span><span class="sxs-lookup"><span data-stu-id="7c355-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="7c355-103">正如其名，Windows Presentation Foundation (WPF) 也很適合讓客戶的豐富的呈現體驗。</span><span class="sxs-lookup"><span data-stu-id="7c355-103">As its name suggests, Windows Presentation Foundation (WPF) is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="7c355-104">這些逐步解說會示範如何自訂外觀和行為 （包括動畫） 的按鈕。</span><span class="sxs-lookup"><span data-stu-id="7c355-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="7c355-105">完成這項自訂，讓您可以套用這個自訂的按鈕輕鬆地為任何按鈕應用程式中使用的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="7c355-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="7c355-106">下圖顯示 [自訂] 按鈕，您將建立。</span><span class="sxs-lookup"><span data-stu-id="7c355-106">The following illustration shows the customized button that you will create.</span></span>  
  
 <span data-ttu-id="7c355-107">![您將建立的自訂的按鈕](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="7c355-107">![The customized button that you will create](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>  
  
 <span data-ttu-id="7c355-108">向量圖形組成按鈕的外觀藉由使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7c355-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="7c355-109">除非它是功能更強大且可延伸，則會是類似於 HTML。</span><span class="sxs-lookup"><span data-stu-id="7c355-109">is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="7c355-110">可以在使用 Microsoft Visual Studio 或 「 記事本 」 中，以手動方式輸入，或者您可以使用視覺化設計工具，例如 Microsoft Expression Blend。</span><span class="sxs-lookup"><span data-stu-id="7c355-110">can be typed in manually using Microsoft Visual Studio or Notepad, or you can use a visual design tool such as Microsoft Expression Blend.</span></span> <span data-ttu-id="7c355-111">Expression Blend 的運作方式是建立基礎[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]撰寫程式碼，因此這兩種方法建立相同的圖形。</span><span class="sxs-lookup"><span data-stu-id="7c355-111">Expression Blend works by creating underlying [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code, so both methods create the same graphics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c355-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="7c355-112">In This Section</span></span>  
 [<span data-ttu-id="7c355-113">使用 Microsoft Expression Blend 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="7c355-113">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 <span data-ttu-id="7c355-114">示範如何建立具有自訂行為的按鈕，使用 Expression blend 設計工具的功能。</span><span class="sxs-lookup"><span data-stu-id="7c355-114">Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>  
  
 [<span data-ttu-id="7c355-115">使用 XAML 建立按鈕</span><span class="sxs-lookup"><span data-stu-id="7c355-115">Create a Button by Using XAML</span></span>](walkthrough-create-a-button-by-using-xaml.md)  
 <span data-ttu-id="7c355-116">示範如何建立具有自訂行為的按鈕，使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7c355-116">Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and Visual Studio.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7c355-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="7c355-117">Related Sections</span></span>  
 [<span data-ttu-id="7c355-118">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="7c355-118">Styling and Templating</span></span>](styling-and-templating.md)  
 <span data-ttu-id="7c355-119">描述如何判斷的外觀和行為的控制項使用樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="7c355-119">Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>  
  
 [<span data-ttu-id="7c355-120">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="7c355-120">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)  
 <span data-ttu-id="7c355-121">描述如何動畫的物件，使用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]動畫和計時系統。</span><span class="sxs-lookup"><span data-stu-id="7c355-121">Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>  
  
 [<span data-ttu-id="7c355-122">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="7c355-122">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 <span data-ttu-id="7c355-123">描述如何使用來以純色、 線形漸層及放射狀漸層繪製的筆刷物件。</span><span class="sxs-lookup"><span data-stu-id="7c355-123">Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>  
  
 [<span data-ttu-id="7c355-124">點陣圖效果概觀</span><span class="sxs-lookup"><span data-stu-id="7c355-124">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)  
 <span data-ttu-id="7c355-125">描述所支援的點陣圖效果[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]並說明如何套用它們。</span><span class="sxs-lookup"><span data-stu-id="7c355-125">Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>
