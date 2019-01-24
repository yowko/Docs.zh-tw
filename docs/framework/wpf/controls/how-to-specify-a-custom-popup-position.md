---
title: HOW TO：指定自訂 Popup 的位置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b61ab6ab02d65d0549941b0055f7aef480d7d644
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726789"
---
# <a name="how-to-specify-a-custom-popup-position"></a>HOW TO：指定自訂 Popup 的位置
此範例示範如何指定的自訂位置<xref:System.Windows.Controls.Primitives.Popup>控制何時<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。  
  
## <a name="example"></a>範例  
 當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>，則<xref:System.Windows.Controls.Primitives.Popup>呼叫定義的執行個體<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委派。 這個委派會傳回一組相對於目標區域的左上的角和的左上的角的可能點<xref:System.Windows.Controls.Primitives.Popup>。 <xref:System.Windows.Controls.Primitives.Popup>放置之處發生可提供最佳的可見性。  
  
 下列範例示範如何定義的位置<xref:System.Windows.Controls.Primitives.Popup>splittunneling<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。 它也會示範如何建立並指派<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委派，以便放置<xref:System.Windows.Controls.Primitives.Popup>。  回呼委派，會傳回兩個<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>物件。  如果<xref:System.Windows.Controls.Primitives.Popup>隱藏的畫面邊緣的第一個位置，<xref:System.Windows.Controls.Primitives.Popup>放在第二個位置。  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 如需完整的範例，請參閱[快顯位置範例](https://go.microsoft.com/fwlink/?LinkID=160032)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.Primitives.Popup>
- [快顯功能表概觀](../../../../docs/framework/wpf/controls/popup-overview.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
