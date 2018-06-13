---
title: 如何：自訂 ScrollBar 上捲動方塊的大小
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 689b73eb58cdfceb2ce5d4e76cbbc3d6c5af8967
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551800"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a>如何：自訂 ScrollBar 上捲動方塊的大小
本主題說明如何設定<xref:System.Windows.Controls.Primitives.Thumb>的<xref:System.Windows.Controls.Primitives.ScrollBar>固定的大小，以及如何指定的最小大小<xref:System.Windows.Controls.Primitives.Thumb>的<xref:System.Windows.Controls.Primitives.ScrollBar>。  
  
## <a name="example"></a>範例  
  
## <a name="description"></a>描述  
 下列範例會建立<xref:System.Windows.Controls.Primitives.ScrollBar>具有<xref:System.Windows.Controls.Primitives.Thumb>具有固定大小。 範例會設定<xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A>屬性<xref:System.Windows.Controls.Primitives.Thumb>至<xref:System.Double.NaN>和設定的高度<xref:System.Windows.Controls.Primitives.Thumb>。  若要建立水平<xref:System.Windows.Controls.Primitives.ScrollBar>與<xref:System.Windows.Controls.Primitives.Thumb>固定的寬度時，設定寬度<xref:System.Windows.Controls.Primitives.Thumb>。  
  
## <a name="code"></a>程式碼  
 [!code-xaml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a>描述  
 下列範例會建立<xref:System.Windows.Controls.Primitives.ScrollBar>具有<xref:System.Windows.Controls.Primitives.Thumb>具有最小大小。 此範例設定的值<xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>。 若要建立水平<xref:System.Windows.Controls.Primitives.ScrollBar>與<xref:System.Windows.Controls.Primitives.Thumb>最小寬度時，設定<xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>。  
  
## <a name="code"></a>程式碼  
 [!code-xaml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a>另請參閱  
 [ScrollBar 樣式和範本](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)
