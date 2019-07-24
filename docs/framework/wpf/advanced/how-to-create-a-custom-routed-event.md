---
title: 作法：建立自訂路由事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: cbfb88af4e35e3f090248982bb14d6b7a3a03cef
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401462"
---
# <a name="how-to-create-a-custom-routed-event"></a>作法：建立自訂路由事件
若要讓您的自訂事件支援事件路由, 您必須<xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>使用方法來註冊。 此範例示範建立自訂路由事件的基本概念。  
  
## <a name="example"></a>範例  
 如下列範例所示, 您會先<xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>使用方法來註冊。 依照慣例, <xref:System.Windows.RoutedEvent>靜態功能變數名稱應以後綴***事件***結尾。 在此範例中, 事件的名稱是`Tap` , 而事件的路由策略是。 <xref:System.Windows.RoutingStrategy.Bubble> 在註冊呼叫之後, 您可以為事件提供 add 和 remove common language runtime (CLR) 事件存取子。  
  
 請注意，即使透過此特定範例中的 `OnTap` 虛擬方法引發事件，引發事件或事件回應變更的方式還是取決於您的需求。  
  
 另請注意, 此範例基本上會執行的<xref:System.Windows.Controls.Button>整個子類別; 該子類別會建立為個別的元件, 然後在另[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]一個頁面上具現化為自訂類別。 這是為了說明下列概念：可將子類別控制項插入包含其他控制項的樹狀結構；然後，在此情況下，這些控制項上的自訂事件就會具有與任何原生 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 項目極為相同的事件路由功能。  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 通道事件的建立方式相同, 但<xref:System.Windows.RoutedEvent.RoutingStrategy%2A>在註冊呼叫中設定為。 <xref:System.Windows.RoutingStrategy.Tunnel> 依照慣例，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的通道事件前面會加上 "Preview" 這個字。  
  
 若要查看事件反昇事件運作方式的範例，請參閱[處理路由事件](how-to-handle-a-routed-event.md)。  
  
## <a name="see-also"></a>另請參閱

- [路由事件概觀](routed-events-overview.md)
- [輸入概觀](input-overview.md)
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
