---
title: "如何：確保 GridSplitter 是可見的"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b7587a093b2b43856a05693bb785a0465211782
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>如何：確保 GridSplitter 是可見的
這個範例示範如何確定<xref:System.Windows.Controls.GridSplitter>中的其他控制項並未隱藏控制項<xref:System.Windows.Controls.Grid>。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.Panel.Children%2A>的<xref:System.Windows.Controls.Grid>控制項以它們在標記或程式碼中定義的順序轉譯。 <xref:System.Windows.Controls.GridSplitter>如果您沒有定義輸出為中的最後一個項目，可以由其他控制項隱藏控制項<xref:System.Windows.Controls.Panel.Children%2A>集合，或若您授與其他控制更高層<xref:System.Windows.Controls.Panel.ZIndexProperty>。  
  
 若要避免隱藏<xref:System.Windows.Controls.GridSplitter>控制項，執行下列其中一項。  
  
-   請確定<xref:System.Windows.Controls.GridSplitter>控制項是最後<xref:System.Windows.Controls.Panel.Children%2A>加入<xref:System.Windows.Controls.Grid>。 下列範例所示<xref:System.Windows.Controls.GridSplitter>中的最後一個項目為<xref:System.Windows.Controls.Panel.Children%2A>集合<xref:System.Windows.Controls.Grid>。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   設定<xref:System.Windows.Controls.Panel.ZIndexProperty>上<xref:System.Windows.Controls.GridSplitter>高於的控制項，否則會隱藏起來。 下列範例會提供<xref:System.Windows.Controls.GridSplitter>控制更高層<xref:System.Windows.Controls.Panel.ZIndexProperty>比<xref:System.Windows.Controls.Button>控制項。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   否則會隱藏在控制項上設定邊界<xref:System.Windows.Controls.GridSplitter>以便<xref:System.Windows.Controls.GridSplitter>公開。 下列範例會設定邊界上的控制項，否則會覆疊和隱藏<xref:System.Windows.Controls.GridSplitter>。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.GridSplitter>  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
