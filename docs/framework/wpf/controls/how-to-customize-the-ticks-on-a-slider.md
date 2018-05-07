---
title: 操作說明：自訂滑桿上的刻度
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 667ec5d5504e18449800598f0b14548b7463bdf3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a>操作說明：自訂滑桿上的刻度
這個範例示範如何建立<xref:System.Windows.Controls.Slider>有刻度的控制項。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.Primitives.TickBar>顯示當您設定<xref:System.Windows.Controls.Slider.TickPlacement%2A>屬性以外的值為<xref:System.Windows.Controls.Primitives.TickPlacement.None>，這是預設值。  
  
 下列範例示範如何建立<xref:System.Windows.Controls.Slider>與<xref:System.Windows.Controls.Primitives.TickBar>顯示刻度。 <xref:System.Windows.Controls.Slider.TickPlacement%2A>和<xref:System.Windows.Controls.Slider.TickFrequency%2A>屬性，定義刻度和它們之間的間隔的位置。 當您移動<xref:System.Windows.Controls.Primitives.Thumb>，工具提示顯示的值<xref:System.Windows.Controls.Slider>。 <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A>屬性會定義在工具提示的情況。 <xref:System.Windows.Controls.Primitives.Thumb>移動對應到刻度的位置，因為<xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A>設`true`。  
  
 下列範例示範如何使用<xref:System.Windows.Controls.Slider.Ticks%2A>屬性以建立刻度標記沿著<xref:System.Windows.Controls.Slider>不規則的間隔。  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [滑桿操作說明主題](http://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
