---
title: "如何：使用自動配置建立按鈕"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d55dc1330c21e7eb9f7cfd7f554234dccd6f274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="f3317-102">如何：使用自動配置建立按鈕</span><span class="sxs-lookup"><span data-stu-id="f3317-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="f3317-103">此範例說明如何使用自動版面配置方法，以建立可當地語系化之應用程式中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="f3317-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="f3317-104">當地語系化的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]是耗時的程序。</span><span class="sxs-lookup"><span data-stu-id="f3317-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="f3317-105">當地語系化人員除了翻譯文字以外，通常還需要調整項目的大小並重新置放項目。</span><span class="sxs-lookup"><span data-stu-id="f3317-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="f3317-106">在過去每種語言，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]需要調整的已調整。</span><span class="sxs-lookup"><span data-stu-id="f3317-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="f3317-107">現在與功能的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]您可以設計會減少需要調整的項目。</span><span class="sxs-lookup"><span data-stu-id="f3317-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="f3317-108">撰寫應用程式可以更輕鬆地調整大小和重新定位方法會呼叫`automatic layout`。</span><span class="sxs-lookup"><span data-stu-id="f3317-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="f3317-109">下面兩個[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例會建立具現化的按鈕; 一個用於英文字，另一個西班牙文字的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f3317-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="f3317-110">請注意，除了文字之外，其餘程式碼都相同；按鈕會配合文字進行調整。</span><span class="sxs-lookup"><span data-stu-id="f3317-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3317-111">範例</span><span class="sxs-lookup"><span data-stu-id="f3317-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="f3317-112">下圖顯示程式碼範例的輸出。</span><span class="sxs-lookup"><span data-stu-id="f3317-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="f3317-113">![按鈕相同，但文字的語言不同](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="f3317-113">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="f3317-114">可自動調整大小的按鈕</span><span class="sxs-lookup"><span data-stu-id="f3317-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3317-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3317-115">See Also</span></span>  
 [<span data-ttu-id="f3317-116">使用自動配置概觀</span><span class="sxs-lookup"><span data-stu-id="f3317-116">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="f3317-117">針對自動版面配置使用方格</span><span class="sxs-lookup"><span data-stu-id="f3317-117">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
