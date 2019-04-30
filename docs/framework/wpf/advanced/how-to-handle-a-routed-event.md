---
title: HOW TO：處理路由事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: edb3d6724af89b7e85986c50b579084e3c4e5070
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001503"
---
# <a name="how-to-handle-a-routed-event"></a>HOW TO：處理路由事件
此範例示範事件反昇事件運作方式，以及如何撰寫可處理路由事件資料的處理常式。  
  
## <a name="example"></a>範例  
 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，項目會以項目樹狀結構排列。 父項目可以參與處理一開始是由項目樹狀結構中子項目所引發的事件。 這可能是事件路由所造成。  
  
 路由事件通常會遵循兩個路由策略中的其中一個：事件反昇或通道。 此範例著重於事件反昇事件，並使用<xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType>事件，以顯示路由運作方式。  
  
 下列範例會建立兩個<xref:System.Windows.Controls.Button>控制項，並使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性語法，以將事件處理常式附加至通用的父項目，這在此範例中是<xref:System.Windows.Controls.StackPanel>。 而不是每個附加個別的事件處理常式<xref:System.Windows.Controls.Button>子元素，此範例使用屬性語法來附加事件處理常式<xref:System.Windows.Controls.StackPanel>父項目。 此事件處理模式示範如何使用事件路由，作為減少已附加處理常式之項目數的技術。 每個的所有事件反昇事件<xref:System.Windows.Controls.Button>路由到父項目。  
  
 請注意，其父系<xref:System.Windows.Controls.StackPanel>項目，<xref:System.Windows.Controls.Primitives.ButtonBase.Click>指定為部分限定屬性所命名的事件名稱<xref:System.Windows.Controls.Button>類別。 <xref:System.Windows.Controls.Button>類別是<xref:System.Windows.Controls.Primitives.ButtonBase>衍生的類別具有<xref:System.Windows.Controls.Primitives.ButtonBase.Click>的成員清單中的事件。 如果所處理的事件不存在於附加路由事件處理常式之項目的成員清單中，則需要有附加事件處理常式的這個部分限定方法。  
  
 [!code-xaml[RoutedEventHandle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 下列範例會處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  此範例會報告哪些項目處理事件以及哪個項目引發事件。 使用者按一下任一按鈕時，就會執行事件處理常式。  
  
 [!code-csharp[RoutedEventHandle#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.RoutedEvent>
- [輸入概觀](input-overview.md)
- [路由事件概觀](routed-events-overview.md)
- [HOW-TO 主題](events-how-to-topics.md)
- [XAML 語法詳細資料](xaml-syntax-in-detail.md)
