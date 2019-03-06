---
title: HOW TO：建立 StackPanel
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: 46b037e3f1626e77a61dca787b705a63ccd28ba0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360433"
---
# <a name="how-to-create-a-stackpanel"></a>HOW TO：建立 StackPanel
此範例示範如何建立<xref:System.Windows.Controls.StackPanel>。  
  
## <a name="example"></a>範例  
 A<xref:System.Windows.Controls.StackPanel>可讓您指定的方向堆疊元素。 藉由使用屬性上定義之<xref:System.Windows.Controls.StackPanel>，方向可以垂直，這是預設設定，或水平。  
  
 下例垂直堆疊五<xref:System.Windows.Controls.TextBlock>控制每個都有不同<xref:System.Windows.Controls.Border>並<xref:System.Windows.Controls.Border.Background%2A>，使用<xref:System.Windows.Controls.StackPanel>。 沒有指定任何子項目<xref:System.Windows.FrameworkElement.Width%2A>伸展以填滿父視窗; 然而，子項目具有指定<xref:System.Windows.FrameworkElement.Width%2A>，置中對齊的範圍內。  
  
 預設堆疊方向<xref:System.Windows.Controls.StackPanel>為垂直。 控制項中的內容流程<xref:System.Windows.Controls.StackPanel>，使用<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性。 您可以使用來控制水平對齊<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性。  
  
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
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.StackPanel>
- [面板概觀](panels-overview.md)
- [HOW-TO 主題](stackpanel-how-to-topics.md)
