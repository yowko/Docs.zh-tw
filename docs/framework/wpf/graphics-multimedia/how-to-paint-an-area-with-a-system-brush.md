---
title: 操作說明：使用系統筆刷繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: f8a66ffc283016d65a17b33e98ce28fe4cd1c242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a>操作說明：使用系統筆刷繪製區域
<xref:System.Windows.SystemColors>類別提供的存取權系統筆刷和色彩，例如<xref:System.Windows.SystemColors.ControlBrush%2A>， <xref:System.Windows.SystemColors.ControlBrushKey%2A>，和<xref:System.Windows.SystemColors.DesktopBrush%2A>。 系統筆刷<xref:System.Windows.Media.SolidColorBrush>使用指定的系統色彩繪製區域的物件。 系統筆刷只能產生純色填滿，因此無法用於產生漸層。  
  
 您可以將系統筆刷當作靜態或動態資源來使用。 當應用程式在執行時，如果您想要在使用者變更系統筆刷時自動更新筆刷，請使用動態資源；否則請使用靜態資源。 SystemColors 類別包含多種遵循嚴格命名慣例的靜態屬性：  
  
-   *\<SystemColor>* Brush  
  
     取得靜態參考<xref:System.Windows.Media.SolidColorBrush>之指定的系統色彩。  
  
-   *\<SystemColor>* BrushKey  
  
     取得動態參考<xref:System.Windows.Media.SolidColorBrush>之指定的系統色彩。  
  
-   *\<SystemColor>* Color  
  
     取得靜態參考<xref:System.Windows.Media.Color>結構指定的系統色彩。  
  
-   *\<SystemColor>* ColorKey  
  
     取得動態參考<xref:System.Windows.Media.Color>結構指定的系統色彩。  
  
 系統色彩是<xref:System.Windows.Media.Color>可用來設定筆刷的結構。 例如，您可以建立使用系統色彩設定為漸層<xref:System.Windows.Media.GradientStop.Color%2A>屬性<xref:System.Windows.Media.LinearGradientBrush>物件的系統色彩與漸層停駐。 如需範例，請參閱[漸層中使用系統色彩](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)。  
  
## <a name="example"></a>範例  
 下列範例使用動態系統筆刷參考來設定按鈕的 Background。  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 下一個範例使用靜態系統筆刷參考來設定按鈕的 Background。  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 如需示範如何使用系統色彩漸層中的範例，請參閱[漸層中使用系統色彩](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在漸層中使用系統色彩](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
