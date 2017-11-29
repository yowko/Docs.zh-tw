---
title: "如何：處理路由事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83f59f2df9311f30995b18529a733a5569c85ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-a-routed-event"></a>如何：處理路由事件
此範例示範事件反昇事件運作方式，以及如何撰寫可處理路由事件資料的處理常式。  
  
## <a name="example"></a>範例  
 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，項目會以項目樹狀結構排列。 父項目可以參與處理一開始是由項目樹狀結構中子項目所引發的事件。 這可能是事件路由所造成。  
  
 路由事件通常會遵循兩個路由策略中的其中一個：事件反昇或通道。 此範例著重於反昇事件和使用<xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType>事件，以便顯示如何路由的運作。  
  
 下列範例會建立兩個<xref:System.Windows.Controls.Button>控制，並使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性連結到通用的父項目，即在此範例中的 事件處理常式語法<xref:System.Windows.Controls.StackPanel>。 而不是每個附加個別的事件處理常式<xref:System.Windows.Controls.Button>子項目，這個範例會使用屬性語法附加事件處理常式<xref:System.Windows.Controls.StackPanel>父項目。 此事件處理模式示範如何使用事件路由，作為減少已附加處理常式之項目數的技術。 每個的反昇事件<xref:System.Windows.Controls.Button>路由到父項目。  
  
 請注意，在父代上<xref:System.Windows.Controls.StackPanel>項目，<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件名稱指定為屬性部分限定的命名<xref:System.Windows.Controls.Button>類別。 <xref:System.Windows.Controls.Button>類別是<xref:System.Windows.Controls.Primitives.ButtonBase>衍生的類別具有<xref:System.Windows.Controls.Primitives.ButtonBase.Click>中列出其成員的事件。 如果所處理的事件不存在於附加路由事件處理常式之項目的成員清單中，則需要有附加事件處理常式的這個部分限定方法。  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 下列範例會處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  此範例會報告哪些項目處理事件以及哪個項目引發事件。 使用者按一下任一按鈕時，就會執行事件處理常式。  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.RoutedEvent>  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
