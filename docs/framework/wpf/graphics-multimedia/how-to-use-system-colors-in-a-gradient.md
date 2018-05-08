---
title: 操作說明：在漸層中使用系統色彩
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 4c3fca1db031b0dc397e9db58195b9714ff8aa9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>操作說明：在漸層中使用系統色彩
若要使用系統色彩漸層中，您使用 *\<SystemColor >* 色彩和 *\<SystemColor >* ColorKey 的靜態屬性<xref:System.Windows.SystemColors>類別來取得參考的色彩，其中 *\<SystemColor >* 是所需的系統色彩的名稱。 使用 *\<SystemColor >* ColorKey 屬性，當您想要建立動態參考系統佈景主題變更時自動更新。 否則，請使用 *\<SystemColor >* 色彩屬性。  
  
## <a name="example"></a>範例  
 下列範例使用動態系統色彩資源來建立漸層。  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 下列範例使用靜態系統色彩資源來建立漸層。  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.SystemColors>  
 [使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
