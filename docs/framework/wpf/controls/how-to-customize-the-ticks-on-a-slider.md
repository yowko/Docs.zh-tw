---
title: 如何：自訂滑桿上的刻度
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 045a2f540a37cdea84d2bf2f3ed1e74e122bdbb5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746106"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="0a778-102">如何：自訂滑桿上的刻度</span><span class="sxs-lookup"><span data-stu-id="0a778-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="0a778-103">此範例示範如何建立<xref:System.Windows.Controls.Slider>具有刻度標記的控制項。</span><span class="sxs-lookup"><span data-stu-id="0a778-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a778-104">範例</span><span class="sxs-lookup"><span data-stu-id="0a778-104">Example</span></span>  
 <span data-ttu-id="0a778-105"><xref:System.Windows.Controls.Primitives.TickBar>顯示當您設定<xref:System.Windows.Controls.Slider.TickPlacement%2A>以外的值的屬性<xref:System.Windows.Controls.Primitives.TickPlacement.None>，這是預設值。</span><span class="sxs-lookup"><span data-stu-id="0a778-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="0a778-106">下列範例示範如何建立<xref:System.Windows.Controls.Slider>與<xref:System.Windows.Controls.Primitives.TickBar>會顯示刻度。</span><span class="sxs-lookup"><span data-stu-id="0a778-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="0a778-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A>和<xref:System.Windows.Controls.Slider.TickFrequency%2A>屬性，定義刻度標記和它們之間的間隔的位置。</span><span class="sxs-lookup"><span data-stu-id="0a778-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="0a778-108">當您移動<xref:System.Windows.Controls.Primitives.Thumb>，工具提示顯示的值<xref:System.Windows.Controls.Slider>。</span><span class="sxs-lookup"><span data-stu-id="0a778-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="0a778-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A>屬性會定義工具提示的發生。</span><span class="sxs-lookup"><span data-stu-id="0a778-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="0a778-110"><xref:System.Windows.Controls.Primitives.Thumb>移動對應到刻度的位置，因為<xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A>設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="0a778-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="0a778-111">下列範例示範如何使用<xref:System.Windows.Controls.Slider.Ticks%2A>屬性，以建立刻度標記沿著<xref:System.Windows.Controls.Slider>以不規則的間隔。</span><span class="sxs-lookup"><span data-stu-id="0a778-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="0a778-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a778-112">See Also</span></span>  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [<span data-ttu-id="0a778-113">滑桿操作說明主題</span><span class="sxs-lookup"><span data-stu-id="0a778-113">Slider How-to Topics</span></span>](https://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
