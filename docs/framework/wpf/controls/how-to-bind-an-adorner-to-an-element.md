---
title: 如何：將裝飾項繫結至項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: fb419ee5a57e81e7e3bc72ae04fd200703b80cd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>如何：將裝飾項繫結至項目
這個範例示範如何以程式設計方式將裝飾項繫結至指定<xref:System.Windows.UIElement>。  
  
## <a name="example"></a>範例  
 若要將裝飾項繫結至特定<xref:System.Windows.UIElement>，請遵循下列步驟：  
  
1.  呼叫`static`方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>取得<xref:System.Windows.Documents.AdornerLayer>物件<xref:System.Windows.UIElement>至會裝飾。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 開始於指定的視覺化樹狀結構會進入**UIElement**，並傳回它發現的第一個裝飾項層。 (如果找不到任何裝飾項圖層，方法會傳回 null。)  
  
2.  呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法，以將裝飾項繫結至目標**UIElement**。  
  
 下列範例會將繫結 （如上所示） 以 SimpleCircleAdorner<xref:System.Windows.Controls.TextBox>名為*myTextBox*。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。  
  
## <a name="see-also"></a>另請參閱  
 [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)
