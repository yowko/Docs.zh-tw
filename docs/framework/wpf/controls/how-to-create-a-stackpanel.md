---
title: HOW TO：建立 StackPanel
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: bcf6decff2fbc012b5f8b62794f0d7b2cd9f29fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121806"
---
# <a name="how-to-create-a-stackpanel"></a><span data-ttu-id="0965a-102">HOW TO：建立 StackPanel</span><span class="sxs-lookup"><span data-stu-id="0965a-102">How to: Create a StackPanel</span></span>
<span data-ttu-id="0965a-103">此範例示範如何建立<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="0965a-103">This example shows how to create a <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0965a-104">範例</span><span class="sxs-lookup"><span data-stu-id="0965a-104">Example</span></span>  
 <span data-ttu-id="0965a-105">A<xref:System.Windows.Controls.StackPanel>可讓您指定的方向堆疊元素。</span><span class="sxs-lookup"><span data-stu-id="0965a-105">A <xref:System.Windows.Controls.StackPanel> allows you to stack elements in a specified direction.</span></span> <span data-ttu-id="0965a-106">藉由使用屬性上定義之<xref:System.Windows.Controls.StackPanel>，方向可以垂直，這是預設設定，或水平。</span><span class="sxs-lookup"><span data-stu-id="0965a-106">By using properties that are defined on <xref:System.Windows.Controls.StackPanel>, content can flow both vertically, which is the default setting, or horizontally.</span></span>  
  
 <span data-ttu-id="0965a-107">下例垂直堆疊五<xref:System.Windows.Controls.TextBlock>控制每個都有不同<xref:System.Windows.Controls.Border>並<xref:System.Windows.Controls.Border.Background%2A>，使用<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="0965a-107">The following example vertically stacks five <xref:System.Windows.Controls.TextBlock> controls, each with a different <xref:System.Windows.Controls.Border> and <xref:System.Windows.Controls.Border.Background%2A>, by using <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="0965a-108">沒有指定任何子項目<xref:System.Windows.FrameworkElement.Width%2A>伸展以填滿父視窗; 然而，子項目具有指定<xref:System.Windows.FrameworkElement.Width%2A>，置中對齊的範圍內。</span><span class="sxs-lookup"><span data-stu-id="0965a-108">The child elements that have no specified <xref:System.Windows.FrameworkElement.Width%2A> stretch to fill the parent window; however, the child elements that have a specified <xref:System.Windows.FrameworkElement.Width%2A>, are centered within the window.</span></span>  
  
 <span data-ttu-id="0965a-109">預設堆疊方向<xref:System.Windows.Controls.StackPanel>為垂直。</span><span class="sxs-lookup"><span data-stu-id="0965a-109">The default stack direction in a <xref:System.Windows.Controls.StackPanel> is vertical.</span></span> <span data-ttu-id="0965a-110">控制項中的內容流程<xref:System.Windows.Controls.StackPanel>，使用<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0965a-110">To control content flow in a <xref:System.Windows.Controls.StackPanel>, use the <xref:System.Windows.Controls.StackPanel.Orientation%2A> property.</span></span> <span data-ttu-id="0965a-111">您可以使用來控制水平對齊<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0965a-111">You can control horizontal alignment by using the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0965a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0965a-112">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- [<span data-ttu-id="0965a-113">面板概觀</span><span class="sxs-lookup"><span data-stu-id="0965a-113">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="0965a-114">HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="0965a-114">How-to Topics</span></span>](stackpanel-how-to-topics.md)
