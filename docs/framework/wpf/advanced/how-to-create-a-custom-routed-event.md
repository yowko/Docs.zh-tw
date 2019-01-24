---
title: HOW TO：建立自訂路由事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: f6d043dc2975770fe9111c6266096eefb3fe15b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671690"
---
# <a name="how-to-create-a-custom-routed-event"></a>HOW TO：建立自訂路由事件
針對您自訂事件，以支援事件路由，您必須向<xref:System.Windows.RoutedEvent>使用<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>方法。 此範例示範建立自訂路由事件的基本概念。  
  
## <a name="example"></a>範例  
 下列範例所示，您第一次註冊<xref:System.Windows.RoutedEvent>使用<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>方法。 依照慣例，<xref:System.Windows.RoutedEvent>靜態欄位名稱結尾應為後置詞***事件***。 在此範例中，事件的名稱是`Tap`和事件路由策略是<xref:System.Windows.RoutingStrategy.Bubble>。 註冊呼叫之後，您可以提供事件的新增和移除 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 事件存取子。  
  
 請注意，即使透過此特定範例中的 `OnTap` 虛擬方法引發事件，引發事件或事件回應變更的方式還是取決於您的需求。  
  
 也請注意，此範例基本上會實作的整個子類別<xref:System.Windows.Controls.Button>; 該子類別會建立為個別的組件，然後具現化為個別上的自訂類別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]頁面。 這是為了說明下列概念：可將子類別控制項插入包含其他控制項的樹狀結構；然後，在此情況下，這些控制項上的自訂事件就會具有與任何原生 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 項目極為相同的事件路由功能。  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 通道會建立事件相同，但具有<xref:System.Windows.RoutedEvent.RoutingStrategy%2A>設定為<xref:System.Windows.RoutingStrategy.Tunnel>註冊呼叫中。 依照慣例，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的通道事件前面會加上 "Preview" 這個字。  
  
 若要查看事件反昇事件運作方式的範例，請參閱[處理路由事件](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)。  
  
## <a name="see-also"></a>另請參閱
- [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)
- [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
