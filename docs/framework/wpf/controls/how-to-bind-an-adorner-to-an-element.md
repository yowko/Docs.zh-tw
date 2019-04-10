---
title: HOW TO：將 Adorner 繫結至元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: b6909fec466c2b31a7f4156c43b21a0c724f0217
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307284"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>HOW TO：將 Adorner 繫結至元素
此範例示範如何以程式設計方式將裝飾項繫結至指定<xref:System.Windows.UIElement>。  
  
## <a name="example"></a>範例  
 裝飾項繫結至特定<xref:System.Windows.UIElement>，請遵循下列步驟：  
  
1. 呼叫`static`方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>若要取得<xref:System.Windows.Documents.AdornerLayer>物件<xref:System.Windows.UIElement>裝飾。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 始於指定的視覺化樹狀結構中向上**UIElement**，並傳回第一個找到的裝飾項圖層。 (如果找不到任何裝飾項圖層，方法會傳回 null。)  
  
2. 呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>裝飾項繫結至目標方法**UIElement**。  
  
 下列範例會將 SimpleCircleAdorner （如上所示） 來繫結<xref:System.Windows.Controls.TextBox>名為*myTextBox*。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。  
  
## <a name="see-also"></a>另請參閱

- [裝飾項概觀](adorners-overview.md)
