---
title: "如何：在樣式中建立動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2aabe24b77a9016b5b8119646c80ea84eb73acb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-in-a-style"></a>如何：在樣式中建立動畫
這個範例示範如何建立於樣式中的屬性的動畫。 建立動畫時於樣式中，可以直接目標只定義樣式的 framework 元素。 若要凍結的物件，您必須 「 點向下 」 從已設定樣式的元素的屬性。  
  
 在下列範例中，數個動畫會定義於樣式中，並套用到<xref:System.Windows.Controls.Button>。 當使用者將滑鼠停留在按鈕時，它從不透明的淡半透明再回復到重複。 當使用者移出按鈕的滑鼠時，它會變成完全不透明。 按一下按鈕時，它的背景色彩會從橙色白色並再次變更。 因為<xref:System.Windows.Media.SolidColorBrush>用來繪製不可直接針對目標 按鈕，存取它從按鈕的向下 dotting<xref:System.Windows.Controls.Control.Background%2A>屬性。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 請注意，當動畫樣式，則可能不存在於目標物件。 例如，假設您的風格使用<xref:System.Windows.Media.SolidColorBrush>設定按鈕的背景屬性，但處的樣式會覆寫和按鈕的背景設定<xref:System.Windows.Media.LinearGradientBrush>。  嘗試以動畫顯示<xref:System.Windows.Media.SolidColorBrush>不會擲回的例外狀況，動畫會以無訊息模式失敗。  
  
 如需有關分鏡腳本目標語法的詳細資訊，請參閱[概觀腳本](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。 如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。 如需有關樣式的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。
