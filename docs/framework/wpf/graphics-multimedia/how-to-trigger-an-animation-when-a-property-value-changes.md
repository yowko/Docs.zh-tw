---
title: HOW TO：在屬性值變更時觸發動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 7e3eecedf7d464eeb8e4f60f2f05fa06d2e23e09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080705"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="7ca02-102">HOW TO：在屬性值變更時觸發動畫</span><span class="sxs-lookup"><span data-stu-id="7ca02-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="7ca02-103">此範例示範如何使用<xref:System.Windows.Trigger>啟動<xref:System.Windows.Media.Animation.Storyboard>屬性值變更時。</span><span class="sxs-lookup"><span data-stu-id="7ca02-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="7ca02-104">您可以使用<xref:System.Windows.Trigger>內<xref:System.Windows.Style>， <xref:System.Windows.Controls.ControlTemplate>，或<xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="7ca02-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ca02-105">範例</span><span class="sxs-lookup"><span data-stu-id="7ca02-105">Example</span></span>  
 <span data-ttu-id="7ca02-106">下列範例會使用<xref:System.Windows.Trigger>來建立動畫<xref:System.Windows.UIElement.Opacity%2A>的<xref:System.Windows.Controls.Button>當其<xref:System.Windows.UIElement.IsMouseOver%2A>屬性會變成`true`。</span><span class="sxs-lookup"><span data-stu-id="7ca02-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="7ca02-107">套用屬性的動畫<xref:System.Windows.Trigger>物件的行為更複雜的方式比<xref:System.Windows.EventTrigger>動畫開始使用<xref:System.Windows.Media.Animation.Storyboard>方法。</span><span class="sxs-lookup"><span data-stu-id="7ca02-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="7ca02-108">這些 「 傳遞 」 與動畫定義其他<xref:System.Windows.Trigger>物件，但以此撰寫<xref:System.Windows.EventTrigger>和方法觸發動畫。</span><span class="sxs-lookup"><span data-stu-id="7ca02-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca02-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ca02-109">See also</span></span>

- <xref:System.Windows.Trigger>
- [<span data-ttu-id="7ca02-110">屬性動畫技術概觀</span><span class="sxs-lookup"><span data-stu-id="7ca02-110">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="7ca02-111">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="7ca02-111">Storyboards Overview</span></span>](storyboards-overview.md)
