---
title: "如何：指定自訂 Popup 的位置"
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
helpviewer_keywords: Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ab9baca1103adf8de96204bdb1b3353a5456b94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-a-custom-popup-position"></a>如何：指定自訂 Popup 的位置
這個範例示範如何指定的自訂位置<xref:System.Windows.Controls.Primitives.Popup>負責控制何時<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。  
  
## <a name="example"></a>範例  
 當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>、<xref:System.Windows.Controls.Primitives.Popup>呼叫定義的執行個體的<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委派。 這個委派會傳回一組目標區域的左上的角和的左上的角相對的可能點<xref:System.Windows.Controls.Primitives.Popup>。 <xref:System.Windows.Controls.Primitives.Popup>放置某處，提供最佳的可見性。  
  
 下列範例示範如何定義的位置<xref:System.Windows.Controls.Primitives.Popup>藉由設定<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。 它也示範如何建立並指派<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>才能將委派<xref:System.Windows.Controls.Primitives.Popup>。  回呼委派會傳回兩個<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>物件。  如果<xref:System.Windows.Controls.Primitives.Popup>螢幕的邊緣的第一個位置，隱藏<xref:System.Windows.Controls.Primitives.Popup>會放在第二個位置。  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 如需完整範例，請參閱[快顯功能表放置範例](http://go.microsoft.com/fwlink/?LinkID=160032)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [快顯功能表概觀](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
