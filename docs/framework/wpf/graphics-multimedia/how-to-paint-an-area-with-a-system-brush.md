---
title: HOW TO：使用系統筆刷繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: e713903e2cfbb63cb64ceb94621317f9e76dea70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195042"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a>HOW TO：使用系統筆刷繪製區域
<xref:System.Windows.SystemColors>類別提供存取系統筆刷和色彩，例如<xref:System.Windows.SystemColors.ControlBrush%2A>， <xref:System.Windows.SystemColors.ControlBrushKey%2A>，和<xref:System.Windows.SystemColors.DesktopBrush%2A>。 系統筆刷是<xref:System.Windows.Media.SolidColorBrush>使用指定的系統色彩繪製區域的物件。 系統筆刷只能產生純色填滿，因此無法用於產生漸層。  
  
 您可以將系統筆刷當作靜態或動態資源來使用。 當應用程式在執行時，如果您想要在使用者變更系統筆刷時自動更新筆刷，請使用動態資源；否則請使用靜態資源。 SystemColors 類別包含多種遵循嚴格命名慣例的靜態屬性：  
  
-   *\<SystemColor>* Brush  
  
     取得的靜態參考<xref:System.Windows.Media.SolidColorBrush>指定的系統色彩。  
  
-   *\<SystemColor>* BrushKey  
  
     取得動態參考<xref:System.Windows.Media.SolidColorBrush>指定的系統色彩。  
  
-   *\<SystemColor>* Color  
  
     取得的靜態參考<xref:System.Windows.Media.Color>指定的系統色彩的結構。  
  
-   *\<SystemColor>* ColorKey  
  
     取得動態參考<xref:System.Windows.Media.Color>指定的系統色彩的結構。  
  
 系統色彩是<xref:System.Windows.Media.Color>結構，可用於設定筆刷。 比方說，您可以在其中建立所將使用系統色彩的漸層<xref:System.Windows.Media.GradientStop.Color%2A>的屬性<xref:System.Windows.Media.LinearGradientBrush>物件的系統色彩的漸層停駐點。 如需範例，請參閱[漸層中使用系統色彩](how-to-use-system-colors-in-a-gradient.md)。  
  
## <a name="example"></a>範例  
 下列範例使用動態系統筆刷參考來設定按鈕的 Background。  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 下一個範例使用靜態系統筆刷參考來設定按鈕的 Background。  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 如需示範如何使用系統色彩漸層中的範例，請參閱[漸層中使用系統色彩](how-to-use-system-colors-in-a-gradient.md)。  
  
## <a name="see-also"></a>另請參閱

- [在漸層中使用系統色彩](how-to-use-system-colors-in-a-gradient.md)
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
