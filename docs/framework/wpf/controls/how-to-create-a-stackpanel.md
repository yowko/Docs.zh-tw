---
title: "操作說明：建立 StackPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5ba089c671fe54afe1c97da0a7bd786949cb5c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-stackpanel"></a><span data-ttu-id="16444-102">操作說明：建立 StackPanel</span><span class="sxs-lookup"><span data-stu-id="16444-102">How to: Create a StackPanel</span></span>
<span data-ttu-id="16444-103">這個範例示範如何建立<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="16444-103">This example shows how to create a <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16444-104">範例</span><span class="sxs-lookup"><span data-stu-id="16444-104">Example</span></span>  
 <span data-ttu-id="16444-105">A<xref:System.Windows.Controls.StackPanel>可讓您在堆疊中指定方向的項目。</span><span class="sxs-lookup"><span data-stu-id="16444-105">A <xref:System.Windows.Controls.StackPanel> allows you to stack elements in a specified direction.</span></span> <span data-ttu-id="16444-106">藉由使用屬性上定義之<xref:System.Windows.Controls.StackPanel>，內容可以垂直兩者，這是預設的設定，或以水平方式。</span><span class="sxs-lookup"><span data-stu-id="16444-106">By using properties that are defined on <xref:System.Windows.Controls.StackPanel>, content can flow both vertically, which is the default setting, or horizontally.</span></span>  
  
 <span data-ttu-id="16444-107">下列範例中，垂直堆疊五個<xref:System.Windows.Controls.TextBlock>控制項，各有不同<xref:System.Windows.Controls.Border>和<xref:System.Windows.Controls.Border.Background%2A>，使用<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="16444-107">The following example vertically stacks five <xref:System.Windows.Controls.TextBlock> controls, each with a different <xref:System.Windows.Controls.Border> and <xref:System.Windows.Controls.Border.Background%2A>, by using <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="16444-108">沒有指定任何子項目<xref:System.Windows.FrameworkElement.Width%2A>伸展以填滿的父視窗; 然而，子元素具有指定<xref:System.Windows.FrameworkElement.Width%2A>，置中對齊視窗內。</span><span class="sxs-lookup"><span data-stu-id="16444-108">The child elements that have no specified <xref:System.Windows.FrameworkElement.Width%2A> stretch to fill the parent window; however, the child elements that have a specified <xref:System.Windows.FrameworkElement.Width%2A>, are centered within the window.</span></span>  
  
 <span data-ttu-id="16444-109">預設的堆疊方向中<xref:System.Windows.Controls.StackPanel>是垂直。</span><span class="sxs-lookup"><span data-stu-id="16444-109">The default stack direction in a <xref:System.Windows.Controls.StackPanel> is vertical.</span></span> <span data-ttu-id="16444-110">中的控制內容流程<xref:System.Windows.Controls.StackPanel>，使用<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="16444-110">To control content flow in a <xref:System.Windows.Controls.StackPanel>, use the <xref:System.Windows.Controls.StackPanel.Orientation%2A> property.</span></span> <span data-ttu-id="16444-111">您可以使用，以控制水平對齊方式<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="16444-111">You can control horizontal alignment by using the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property.</span></span>  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16444-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16444-112">See Also</span></span>  
 <xref:System.Windows.Controls.StackPanel>  
 [<span data-ttu-id="16444-113">面板概觀</span><span class="sxs-lookup"><span data-stu-id="16444-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="16444-114">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="16444-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)
