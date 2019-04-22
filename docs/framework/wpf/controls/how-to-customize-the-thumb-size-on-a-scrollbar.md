---
title: HOW TO：自訂 ScrollBar 上的 Thumb 大小
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 60ae7c4e95801036c5deb0c485645297509b830c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207275"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a>HOW TO：自訂 ScrollBar 上的 Thumb 大小
本主題說明如何設定<xref:System.Windows.Controls.Primitives.Thumb>的<xref:System.Windows.Controls.Primitives.ScrollBar>至固定的大小，以及指定的最小大小<xref:System.Windows.Controls.Primitives.Thumb>的<xref:System.Windows.Controls.Primitives.ScrollBar>。  
  
## <a name="example"></a>範例  
  
## <a name="description"></a>描述  
 下列範例會建立<xref:System.Windows.Controls.Primitives.ScrollBar>具有<xref:System.Windows.Controls.Primitives.Thumb>具有固定大小。 範例會設定<xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A>的屬性<xref:System.Windows.Controls.Primitives.Thumb>要<xref:System.Double.NaN>設定的高度和<xref:System.Windows.Controls.Primitives.Thumb>。  若要建立水平<xref:System.Windows.Controls.Primitives.ScrollBar>具有<xref:System.Windows.Controls.Primitives.Thumb>，都有固定的寬度，請將設定的寬度<xref:System.Windows.Controls.Primitives.Thumb>。  
  
## <a name="code"></a>程式碼  
 [!code-xaml[ScrollBarCustomThumbSize#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a>描述  
 下列範例會建立<xref:System.Windows.Controls.Primitives.ScrollBar>具有<xref:System.Windows.Controls.Primitives.Thumb>大小下限。 此範例設定的值<xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>。 若要建立水平<xref:System.Windows.Controls.Primitives.ScrollBar>具有<xref:System.Windows.Controls.Primitives.Thumb>的最小寬度時，設定<xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>。  
  
## <a name="code"></a>程式碼  
 [!code-xaml[ScrollBarCustomThumbSize#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a>另請參閱

- [ScrollBar 樣式和範本](scrollbar-styles-and-templates.md)
