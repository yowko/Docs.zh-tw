---
title: 如何：針對自動配置使用格線
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 6ea0b64af07924867c2de97baf5a81f8e8da6a56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544618"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="cfeca-102">如何：針對自動配置使用格線</span><span class="sxs-lookup"><span data-stu-id="cfeca-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="cfeca-103">此範例說明如何使用自動版面配置方法中的格線，以建立當地語系化的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cfeca-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="cfeca-104">當地語系化的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]是耗時的程序。</span><span class="sxs-lookup"><span data-stu-id="cfeca-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="cfeca-105">當地語系化人員除了翻譯文字以外，通常還需要重新調整項目的大小並重新定位。</span><span class="sxs-lookup"><span data-stu-id="cfeca-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="cfeca-106">在過去每種語言，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]需要調整的已調整。</span><span class="sxs-lookup"><span data-stu-id="cfeca-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="cfeca-107">現在與功能的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]您可以設計會減少需要調整的項目。</span><span class="sxs-lookup"><span data-stu-id="cfeca-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="cfeca-108">撰寫應用程式可以更輕鬆地重新調整大小和重新定位方法會呼叫`auto layout`。</span><span class="sxs-lookup"><span data-stu-id="cfeca-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="cfeca-109">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例示範如何使用方格來將部分按鈕和文字位置。</span><span class="sxs-lookup"><span data-stu-id="cfeca-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="cfeca-110">請注意，儲存格的寬度與高度設為`Auto`; 的資料格按鈕的影像，因此調整以符合影像。</span><span class="sxs-lookup"><span data-stu-id="cfeca-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="cfeca-111">因為<xref:System.Windows.Controls.Grid>項目可以調整其內容將非常有用設計可以當地語系化的應用程式進行自動配置方法。</span><span class="sxs-lookup"><span data-stu-id="cfeca-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfeca-112">範例</span><span class="sxs-lookup"><span data-stu-id="cfeca-112">Example</span></span>  
 <span data-ttu-id="cfeca-113">下列範例示範如何使用格線。</span><span class="sxs-lookup"><span data-stu-id="cfeca-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="cfeca-114">下圖顯示程式碼範例的輸出。</span><span class="sxs-lookup"><span data-stu-id="cfeca-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="cfeca-115">![格線範例](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="cfeca-115">![Grid example](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="cfeca-116">Grid</span><span class="sxs-lookup"><span data-stu-id="cfeca-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfeca-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfeca-117">See Also</span></span>  
 [<span data-ttu-id="cfeca-118">使用自動配置概觀</span><span class="sxs-lookup"><span data-stu-id="cfeca-118">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="cfeca-119">使用自動版面配置建立按鈕</span><span class="sxs-lookup"><span data-stu-id="cfeca-119">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
