---
title: HOW TO：在漸層中使用系統色彩
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 55c99640907a0c372f8c7bbc50b9b45c9f15ef3c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229436"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>HOW TO：在漸層中使用系統色彩
若要使用系統色彩漸層中，您使用 *\<Systemcolor> >* 色彩並 *\<Systemcolor> >* ColorKey 靜態屬性<xref:System.Windows.SystemColors>類別來取得參考的色彩，其中 *\<Systemcolor> >* 是所需的系統色彩的名稱。 使用 *\<Systemcolor> >* ColorKey 屬性，當您想要建立動態參考時，系統佈景主題變更時自動更新。 否則，請使用 *\<Systemcolor> >* Color 屬性。  
  
## <a name="example"></a>範例  
 下列範例使用動態系統色彩資源來建立漸層。  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 下列範例使用靜態系統色彩資源來建立漸層。  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.SystemColors>
- [使用系統筆刷繪製區域](how-to-paint-an-area-with-a-system-brush.md)
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
