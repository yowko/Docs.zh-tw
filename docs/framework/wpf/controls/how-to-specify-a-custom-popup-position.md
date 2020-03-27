---
title: 如何：指定自訂 Popup 的位置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: ea8d73c51dd018608b95104f00bf341ff434225c
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344957"
---
# <a name="how-to-specify-a-custom-popup-position"></a>如何：指定自訂 Popup 的位置
此示例演示如何在<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設置為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>時為控制項指定自訂位置。  
  
## <a name="example"></a>範例  
 當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設置為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>時，<xref:System.Windows.Controls.Primitives.Popup>調用<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委託的已定義實例。 此委託返回一組相對於目的地區域左上角和 左<xref:System.Windows.Controls.Primitives.Popup>上角的可能點。 放置<xref:System.Windows.Controls.Primitives.Popup>發生在提供最佳可見度的點。  
  
 下面的示例演示如何通過將<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設置為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>來定義 的位置。 它還演示如何創建和分配<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委託，以便定位 。 <xref:System.Windows.Controls.Primitives.Popup>  回檔委託返回兩<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>個物件。  <xref:System.Windows.Controls.Primitives.Popup>如果在第一個位置由螢幕邊緣隱藏，<xref:System.Windows.Controls.Primitives.Popup>則 將放置在第二個位置。  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 有關完整示例，請參閱[彈出放置示例](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Primitives.Popup>
- [快顯功能表概觀](popup-overview.md)
- [HOW TO 主題](popup-how-to-topics.md)
