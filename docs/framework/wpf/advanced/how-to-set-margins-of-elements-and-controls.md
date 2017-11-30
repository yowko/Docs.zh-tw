---
title: "如何：設定項目和控制項的邊界"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 965e2061d6457084e4f316d27e29865109f62e34
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-margins-of-elements-and-controls"></a><span data-ttu-id="ffb9b-102">如何：設定項目和控制項的邊界</span><span class="sxs-lookup"><span data-stu-id="ffb9b-102">How to: Set Margins of Elements and Controls</span></span>
<span data-ttu-id="ffb9b-103">這個範例說明如何設定<xref:System.Windows.FrameworkElement.Margin%2A>屬性，藉由變更任何現有的屬性值的程式碼後置中的邊界。</span><span class="sxs-lookup"><span data-stu-id="ffb9b-103">This example describes how to set the <xref:System.Windows.FrameworkElement.Margin%2A> property, by changing any existing property value for the margin in code-behind.</span></span> <span data-ttu-id="ffb9b-104"><xref:System.Windows.FrameworkElement.Margin%2A>屬性是屬性的<xref:System.Windows.FrameworkElement>基底項目，而且會因此繼承各種控制項和其他項目。</span><span class="sxs-lookup"><span data-stu-id="ffb9b-104">The <xref:System.Windows.FrameworkElement.Margin%2A> property is a property of the <xref:System.Windows.FrameworkElement> base element, and is thus inherited by a variety of controls and other elements.</span></span>  
  
 <span data-ttu-id="ffb9b-105">這個範例以撰寫[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，與程式碼後置檔案，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]參考。</span><span class="sxs-lookup"><span data-stu-id="ffb9b-105">This example is written in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], with a code-behind file that the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] refers to.</span></span> <span data-ttu-id="ffb9b-106">程式碼後置會同時顯示[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]和[!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]版本。</span><span class="sxs-lookup"><span data-stu-id="ffb9b-106">The code-behind is shown in both a [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] and a [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] version.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffb9b-107">範例</span><span class="sxs-lookup"><span data-stu-id="ffb9b-107">Example</span></span>  
 [!code-xaml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
