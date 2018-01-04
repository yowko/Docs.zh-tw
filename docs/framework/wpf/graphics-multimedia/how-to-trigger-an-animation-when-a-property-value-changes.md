---
title: "如何：當屬性值變更時觸發動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0eb4542d8baf86f01417eb1925028a00471b40b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="3babe-102">如何：當屬性值變更時觸發動畫</span><span class="sxs-lookup"><span data-stu-id="3babe-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="3babe-103">這個範例示範如何使用<xref:System.Windows.Trigger>啟動<xref:System.Windows.Media.Animation.Storyboard>屬性值變更時。</span><span class="sxs-lookup"><span data-stu-id="3babe-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="3babe-104">您可以使用<xref:System.Windows.Trigger>內<xref:System.Windows.Style>， <xref:System.Windows.Controls.ControlTemplate>，或<xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="3babe-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3babe-105">範例</span><span class="sxs-lookup"><span data-stu-id="3babe-105">Example</span></span>  
 <span data-ttu-id="3babe-106">下列範例會使用<xref:System.Windows.Trigger>以動畫方式顯示<xref:System.Windows.UIElement.Opacity%2A>的<xref:System.Windows.Controls.Button>時其<xref:System.Windows.UIElement.IsMouseOver%2A>屬性變成`true`。</span><span class="sxs-lookup"><span data-stu-id="3babe-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="3babe-107">屬性所套用的動畫<xref:System.Windows.Trigger>物件的行為會以更複雜的方式比<xref:System.Windows.EventTrigger>動畫開始使用<xref:System.Windows.Media.Animation.Storyboard>方法。</span><span class="sxs-lookup"><span data-stu-id="3babe-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="3babe-108">這些 「 遞交"動畫定義其他<xref:System.Windows.Trigger>物件，但以此撰寫<xref:System.Windows.EventTrigger>和方法觸發動畫。</span><span class="sxs-lookup"><span data-stu-id="3babe-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3babe-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="3babe-109">See Also</span></span>  
 <xref:System.Windows.Trigger>  
 [<span data-ttu-id="3babe-110">屬性動畫技術概觀</span><span class="sxs-lookup"><span data-stu-id="3babe-110">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="3babe-111">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="3babe-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
