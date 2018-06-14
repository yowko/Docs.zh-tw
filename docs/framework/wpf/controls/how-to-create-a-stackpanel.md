---
title: 操作說明：建立 StackPanel
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: 30f24d8dba7c09271a5957822439af6b64e05aca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553023"
---
# <a name="how-to-create-a-stackpanel"></a>操作說明：建立 StackPanel
這個範例示範如何建立<xref:System.Windows.Controls.StackPanel>。  
  
## <a name="example"></a>範例  
 A<xref:System.Windows.Controls.StackPanel>可讓您在堆疊中指定方向的項目。 藉由使用屬性上定義之<xref:System.Windows.Controls.StackPanel>，內容可以垂直兩者，這是預設的設定，或以水平方式。  
  
 下列範例中，垂直堆疊五個<xref:System.Windows.Controls.TextBlock>控制項，各有不同<xref:System.Windows.Controls.Border>和<xref:System.Windows.Controls.Border.Background%2A>，使用<xref:System.Windows.Controls.StackPanel>。 沒有指定任何子項目<xref:System.Windows.FrameworkElement.Width%2A>伸展以填滿的父視窗; 然而，子元素具有指定<xref:System.Windows.FrameworkElement.Width%2A>，置中對齊視窗內。  
  
 預設的堆疊方向中<xref:System.Windows.Controls.StackPanel>是垂直。 中的控制內容流程<xref:System.Windows.Controls.StackPanel>，使用<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性。 您可以使用，以控制水平對齊方式<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性。  
  
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
 <xref:System.Windows.Controls.StackPanel>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)
