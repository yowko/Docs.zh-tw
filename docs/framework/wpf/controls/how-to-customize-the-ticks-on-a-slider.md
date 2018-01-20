---
title: "操作說明：自訂滑桿上的刻度"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d21d2950ed228bf588a202419c222ee86dde5b0d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="bd739-102">操作說明：自訂滑桿上的刻度</span><span class="sxs-lookup"><span data-stu-id="bd739-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="bd739-103">這個範例示範如何建立<xref:System.Windows.Controls.Slider>有刻度的控制項。</span><span class="sxs-lookup"><span data-stu-id="bd739-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd739-104">範例</span><span class="sxs-lookup"><span data-stu-id="bd739-104">Example</span></span>  
 <span data-ttu-id="bd739-105"><xref:System.Windows.Controls.Primitives.TickBar>顯示當您設定<xref:System.Windows.Controls.Slider.TickPlacement%2A>屬性以外的值為<xref:System.Windows.Controls.Primitives.TickPlacement.None>，這是預設值。</span><span class="sxs-lookup"><span data-stu-id="bd739-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="bd739-106">下列範例示範如何建立<xref:System.Windows.Controls.Slider>與<xref:System.Windows.Controls.Primitives.TickBar>顯示刻度。</span><span class="sxs-lookup"><span data-stu-id="bd739-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="bd739-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A>和<xref:System.Windows.Controls.Slider.TickFrequency%2A>屬性，定義刻度和它們之間的間隔的位置。</span><span class="sxs-lookup"><span data-stu-id="bd739-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="bd739-108">當您移動<xref:System.Windows.Controls.Primitives.Thumb>，工具提示顯示的值<xref:System.Windows.Controls.Slider>。</span><span class="sxs-lookup"><span data-stu-id="bd739-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="bd739-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A>屬性會定義在工具提示的情況。</span><span class="sxs-lookup"><span data-stu-id="bd739-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="bd739-110"><xref:System.Windows.Controls.Primitives.Thumb>移動對應到刻度的位置，因為<xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A>設`true`。</span><span class="sxs-lookup"><span data-stu-id="bd739-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="bd739-111">下列範例示範如何使用<xref:System.Windows.Controls.Slider.Ticks%2A>屬性以建立刻度標記沿著<xref:System.Windows.Controls.Slider>不規則的間隔。</span><span class="sxs-lookup"><span data-stu-id="bd739-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="bd739-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd739-112">See Also</span></span>  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [<span data-ttu-id="bd739-113">滑桿操作說明主題</span><span class="sxs-lookup"><span data-stu-id="bd739-113">Slider How-to Topics</span></span>](http://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
