---
title: HOW TO：取得或設定 Canvas 定位屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: b7dd64959148b8c2361992fb7cd2f23073693dd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705854"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a>HOW TO：取得或設定 Canvas 定位屬性
此範例示範如何使用的定位方法<xref:System.Windows.Controls.Canvas>放置子內容項目。 這個範例會使用中的內容<xref:System.Windows.Controls.ListBoxItem>來代表定位值，並將值轉換成的執行個體<xref:System.Double>，這是必要的引數的位置。 值是再轉換回字串，而且顯示為中的文字<xref:System.Windows.Controls.TextBlock>使用的項目<xref:System.Windows.Controls.Canvas.GetLeft%2A>方法。  
  
## <a name="example"></a>範例  
 下列範例會建立<xref:System.Windows.Controls.ListBox>擁有十一個可選取的項目<xref:System.Windows.Controls.ListBoxItem>項目。 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>事件觸發程序`ChangeLeft`後續的程式碼區塊會定義中的自訂方法。  
  
 每個<xref:System.Windows.Controls.ListBoxItem>代表<xref:System.Double>值，也就是其中一個引數所<xref:System.Windows.Controls.Canvas.SetLeft%2A>方法<xref:System.Windows.Controls.Canvas>接受。 若要使用<xref:System.Windows.Controls.ListBoxItem>代表的執行個體<xref:System.Double>，您必須先轉換<xref:System.Windows.Controls.ListBoxItem>為正確的資料型別。  
  
 [!code-xaml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 當使用者變更<xref:System.Windows.Controls.ListBox>選取項目，它會叫用`ChangeLeft`自訂方法。 此方法會傳遞<xref:System.Windows.Controls.ListBoxItem>要<xref:System.Windows.LengthConverter>物件，然後將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Double>(請注意，這個值已經轉換成<xref:System.String>使用<xref:System.Windows.Controls.Control.ToString%2A>方法）。 此值接著會傳回到<xref:System.Windows.Controls.Canvas.SetLeft%2A>並<xref:System.Windows.Controls.Canvas.GetLeft%2A>方法<xref:System.Windows.Controls.Canvas>若要變更的位置`text1`物件。  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.ListBoxItem>
- <xref:System.Windows.LengthConverter>
- [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
