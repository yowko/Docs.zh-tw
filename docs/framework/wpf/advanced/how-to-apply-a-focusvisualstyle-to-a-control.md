---
title: "如何：對控制項套用 FocusVisualStyle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41895974b7e6c128d979e362f2dcef1c68e0a5c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>如何：對控制項套用 FocusVisualStyle
此範例將示範如何建立資源中的焦點視覺化樣式，並套用樣式至控制項，使用<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>屬性。  
  
## <a name="example"></a>範例  
 下列範例會定義建立複合只適用於該控制項時的焦點的鍵盤的其他控制項的樣式[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 這會透過定義的樣式<xref:System.Windows.Controls.ControlTemplate>，然後設定時，該樣式參考做為資源<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>屬性。  
  
 類似框線外部矩形被位於外部的矩形區域。 調整大小樣式的修改，除非使用<xref:System.Windows.FrameworkElement.ActualHeight%2A>和<xref:System.Windows.FrameworkElement.ActualWidth%2A>的矩形的控制項焦點視覺化樣式套用的位置。 此範例會設定為負數值<xref:System.Windows.FrameworkElement.Margin%2A>使稍微顯示取得焦點的控制項外框線。  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 A<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>是附加至任何控制項範本樣式出現明確樣式或佈景主題樣式; 從主控制項的樣式可以仍會建立使用<xref:System.Windows.Controls.ControlTemplate>並將該樣式設定為<xref:System.Windows.FrameworkElement.Style%2A>屬性。  
  
 焦點視覺樣式應該一致使用跨主題或 UI，而不是使用不同的另一個用於每個可設定焦點的項目。 如需詳細資訊，請參閱[樣式的焦點在控制項和 FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [設定控制項中焦點的樣式和 FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
