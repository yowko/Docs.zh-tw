---
title: 如何：指定自訂 Popup 的位置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b48dedc044b418062642af5c5bb40afab78a3c97
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635742"
---
# <a name="how-to-specify-a-custom-popup-position"></a>如何：指定自訂 Popup 的位置
此示例演示如何在<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設置<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>為 時為控件指定自定義位置。  
  
## <a name="example"></a>範例  
 當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設置<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>為<xref:System.Windows.Controls.Primitives.Popup>時,<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>調用 委託的已定義實例。 此委託返回一組相對於目標區域左上角和<xref:System.Windows.Controls.Primitives.Popup>左上角的可能點。 放置<xref:System.Windows.Controls.Primitives.Popup>發生在提供最佳可見性的點。  
  
 下面的範例展示如何透過將<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>為 來定義的位置。 此您可以展示如何建立與<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>分配 委託,以便<xref:System.Windows.Controls.Primitives.Popup>定位 。  回調委託返回兩<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>個物件。  <xref:System.Windows.Controls.Primitives.Popup>如果在第一個位置由螢幕邊緣隱藏,<xref:System.Windows.Controls.Primitives.Popup>則將放置在第二個位置。  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 有關完整範例,請參閱[彈出放置範例](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Primitives.Popup>
- [彈出視窗概述](popup-overview.md)
- [如何使用的文章](popup-how-to-topics.md)
