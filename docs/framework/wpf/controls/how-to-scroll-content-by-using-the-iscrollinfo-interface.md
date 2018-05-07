---
title: 如何：使用 IScrollInfo 介面捲動內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 8154a626c6bf48a59be0540f857c0c51d59a26c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>如何：使用 IScrollInfo 介面捲動內容
這個範例示範如何使用捲動內容<xref:System.Windows.Controls.Primitives.IScrollInfo>介面。  
  
## <a name="example"></a>範例  
 下列範例示範的功能<xref:System.Windows.Controls.Primitives.IScrollInfo>介面。 此範例會建立<xref:System.Windows.Controls.StackPanel>中的項目[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]父系中的巢狀<xref:System.Windows.Controls.ScrollViewer>。 子項目的<xref:System.Windows.Controls.StackPanel>可使用所定義之方法以邏輯方式捲動<xref:System.Windows.Controls.Primitives.IScrollInfo>介面，並轉換成執行個體<xref:System.Windows.Controls.StackPanel>(`sp1`) 程式碼中。  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 每個<xref:System.Windows.Controls.Button>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案觸發程序的相關聯的自訂方法，控制捲動行為中的<xref:System.Windows.Controls.StackPanel>。 下列範例示範如何使用<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>和<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>方法; 它通常也會示範如何使用所有定位的方法，<xref:System.Windows.Controls.Primitives.IScrollInfo>類別定義。  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 <xref:System.Windows.Controls.StackPanel>  
 [ScrollViewer 概觀](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
