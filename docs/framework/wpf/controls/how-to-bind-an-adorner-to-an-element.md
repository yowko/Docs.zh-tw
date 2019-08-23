---
title: 作法：將 Adorner 繫結至元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: e8c7eb929042bfe1455bfc9bf459fc466de5c397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923500"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>HOW TO：將 Adorner 繫結至元素
這個範例示範如何以程式設計方式將裝飾項系<xref:System.Windows.UIElement>結至指定的。  
  
## <a name="example"></a>範例  
 若要將裝飾項系結<xref:System.Windows.UIElement>至特定, 請遵循下列步驟:  
  
1. <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.UIElement>呼叫方法,<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>以取得要裝飾之的物件。 `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>引導視覺化樹狀結構 (從指定的**UIElement**開始), 並傳回它找到的第一個裝飾項層。 (如果找不到任何裝飾項圖層，方法會傳回 null。)  
  
2. 呼叫方法, 將裝飾項系結至目標**UIElement。** <xref:System.Windows.Documents.AdornerLayer.Add%2A>  
  
 下列範例會將 SimpleCircleAdorner (如上所示) 系結<xref:System.Windows.Controls.TextBox>至名為的*myTextBox*。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> 使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。  
  
## <a name="see-also"></a>另請參閱

- [裝飾項概觀](adorners-overview.md)
