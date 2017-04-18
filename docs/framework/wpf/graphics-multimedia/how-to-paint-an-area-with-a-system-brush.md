---
title: "如何：使用系統筆刷繪製區域 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "筆刷, 使用系統筆刷繪製"
  - "繪圖, 使用系統筆刷"
  - "系統筆刷, 繪製方式"
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：使用系統筆刷繪製區域
<xref:System.Windows.SystemColors> 類別提供系統筆刷和色彩的存取權，例如 <xref:System.Windows.SystemColors.ControlBrush%2A>、<xref:System.Windows.SystemColors.ControlBrushKey%2A> 和 <xref:System.Windows.SystemColors.DesktopBrush%2A>。  系統筆刷是一種 <xref:System.Windows.Media.SolidColorBrush> 物件，可以使用指定的系統色彩來繪製區域。  系統筆刷一律產生實心填色；不能用來建立漸層效果。  
  
 您可以使用系統筆刷做為靜態或動態資源。  如果您希望在使用者於應用程式執行時變更系統筆刷之後，筆刷能夠自動更新，請使用動態資源，否則請使用靜態資源。  SystemColors 類別包含各種靜態屬性，而這些屬性全都遵守嚴格的命名慣例：  
  
-   *\<SystemColor\>*Brush  
  
     取得指定之系統色彩的 <xref:System.Windows.Media.SolidColorBrush> 的靜態參考。  
  
-   *\<SystemColor\>*BrushKey  
  
     取得指定之系統色彩的 <xref:System.Windows.Media.SolidColorBrush> 的動態參考。  
  
-   *\<SystemColor\>*Color  
  
     取得指定之系統色彩的 <xref:System.Windows.Media.Color> 結構的靜態參考。  
  
-   *\<SystemColor\>*ColorKey  
  
     取得指定之系統色彩的 <xref:System.Windows.Media.Color> 結構的動態參考。  
  
 系統色彩是可以用來設定筆刷的 <xref:System.Windows.Media.Color> 結構。  例如，您可以使用系統色彩建立漸層效果，方法是利用系統色彩設定 <xref:System.Windows.Media.LinearGradientBrush> 物件之漸層停駐點的 <xref:System.Windows.Media.GradientStop.Color%2A> 屬性。  如需範例，請參閱 [在漸層中使用系統色彩](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)。  
  
## 範例  
 下列範例使用動態系統筆刷參考來設定按鈕的背景。  
  
 [!code-xml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 下一個範例使用靜態系統筆刷參考來設定按鈕的背景。  
  
 [!code-xml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 如需示範如何在漸層中使用系統色彩的範例，請參閱 [在漸層中使用系統色彩](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)。  
  
## 請參閱  
 [在漸層中使用系統色彩](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)   
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)