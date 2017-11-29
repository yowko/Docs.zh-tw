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
ms.openlocfilehash: 5d266d85e10ca8e77cd32338096cf3a3b761c188
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="2f6a6-102">操作說明：自訂滑桿上的刻度</span><span class="sxs-lookup"><span data-stu-id="2f6a6-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="2f6a6-103">這個範例示範如何建立<xref:System.Windows.Controls.Slider>有刻度的控制項。</span><span class="sxs-lookup"><span data-stu-id="2f6a6-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f6a6-104">範例</span><span class="sxs-lookup"><span data-stu-id="2f6a6-104">Example</span></span>  
 <span data-ttu-id="2f6a6-105"><xref:System.Windows.Controls.Primitives.TickBar>顯示當您設定<xref:System.Windows.Controls.Slider.TickPlacement%2A>屬性以外的值為<xref:System.Windows.Controls.Primitives.TickPlacement.None>，這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2f6a6-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="2f6a6-106">下列範例示範如何建立<xref:System.Windows.Controls.Slider>與<xref:System.Windows.Controls.Primitives.TickBar>顯示刻度。</span><span class="sxs-lookup"><span data-stu-id="2f6a6-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="2f6a6-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A>和<xref:System.Windows.Controls.Slider.TickFrequency%2A>屬性，定義刻度和它們之間的間隔的位置。</span><span class="sxs-lookup"><span data-stu-id="2f6a6-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="2f6a6-108">當您移動<xref:System.Windows.Controls.Primitives.Thumb>，工具提示顯示的值<xref:System.Windows.Controls.Slider>。</span><span class="sxs-lookup"><span data-stu-id="2f6a6-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="2f6a6-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A>屬性會定義在工具提示的情況。</span><span class="sxs-lookup"><span data-stu-id="2f6a6-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="2f6a6-110"><xref:System.Windows.Controls.Primitives.Thumb>移動對應到刻度的位置，因為<xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A>設`true`。</span><span class="sxs-lookup"><span data-stu-id="2f6a6-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="2f6a6-111">下列範例示範如何使用<xref:System.Windows.Controls.Slider.Ticks%2A>屬性以建立刻度標記沿著<xref:System.Windows.Controls.Slider>不規則的間隔。</span><span class="sxs-lookup"><span data-stu-id="2f6a6-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2f6a6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f6a6-112">See Also</span></span>  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [<span data-ttu-id="2f6a6-113">滑桿操作說明主題</span><span class="sxs-lookup"><span data-stu-id="2f6a6-113">Slider How-to Topics</span></span>](http://msdn.microsoft.com/en-us/534be86c-afb2-425d-8186-631278a9925e)
