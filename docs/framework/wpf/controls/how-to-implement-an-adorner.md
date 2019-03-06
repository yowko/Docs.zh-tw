---
title: HOW TO：實作裝飾項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: 53a25396ba5d8a5c78e850e636b7c882c03d5152
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362639"
---
# <a name="how-to-implement-an-adorner"></a>HOW TO：實作裝飾項
此範例中顯示的最小的裝飾項實作。  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 請務必注意，裝飾項並不包括任何繼承的轉譯行為。裝飾項實作者必須負責確定裝飾項轉譯器。   實作轉譯行為的常見方式是覆寫<xref:System.Windows.UIElement.OnRender%2A>方法，並使用一或多個<xref:System.Windows.Media.DrawingContext>轉譯裝飾項的視覺效果所需 （如本範例所示） 的物件。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 藉由實作繼承自抽象類別來建立自訂裝飾項<xref:System.Windows.Documents.Adorner>類別。  裝飾項範例只會裝飾的邊角<xref:System.Windows.UIElement>具有藉由覆寫的圓圈<xref:System.Windows.UIElement.OnRender%2A>方法。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>另請參閱
- [裝飾項概觀](adorners-overview.md)
