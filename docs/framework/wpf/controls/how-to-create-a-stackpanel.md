---
title: "如何：建立 StackPanel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StackPanel 控制項建立"
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：建立 StackPanel
這個範例示範如何建立<xref:System.Windows.Controls.StackPanel>。  
  
## <a name="example"></a>範例  
 A <xref:System.Windows.Controls.StackPanel>可讓您以堆疊項目中指定的方向。 藉由使用屬性上定義之<xref:System.Windows.Controls.StackPanel>，方向可以垂直，這是預設設定，或水平。  
  
 下列範例中，垂直堆疊五個<xref:System.Windows.Controls.TextBlock>控制項，各有不同的<xref:System.Windows.Controls.Border>和<xref:System.Windows.Controls.Border.Background%2A>，使用<xref:System.Windows.Controls.StackPanel>。 沒有指定任何子項目<xref:System.Windows.FrameworkElement.Width%2A>伸展以填滿父視窗，不過，子元素，指定<xref:System.Windows.FrameworkElement.Width%2A>，置中對齊視窗內。  
  
 在預設的堆疊方向<xref:System.Windows.Controls.StackPanel>是垂直。 在控制內容流程<xref:System.Windows.Controls.StackPanel>，使用<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性。 您可以使用，以控制水平對齊<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性。  
  
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
 [How to 主題](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)