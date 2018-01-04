---
title: "如何：將裝飾項繫結至項目"
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
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3c657cde9da19f8ebc6b6d4d05077ed027781b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>如何：將裝飾項繫結至項目
這個範例示範如何以程式設計方式將裝飾項繫結至指定<xref:System.Windows.UIElement>。  
  
## <a name="example"></a>範例  
 若要將裝飾項繫結至特定<xref:System.Windows.UIElement>，請遵循下列步驟：  
  
1.  呼叫`static`方法<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>取得<xref:System.Windows.Documents.AdornerLayer>物件<xref:System.Windows.UIElement>至會裝飾。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>開始於指定的視覺化樹狀結構會進入**UIElement**，並傳回它發現的第一個裝飾項層。 (如果找不到任何裝飾項圖層，方法會傳回 null。)  
  
2.  呼叫<xref:System.Windows.Documents.AdornerLayer.Add%2A>方法，以將裝飾項繫結至目標**UIElement**。  
  
 下列範例會將繫結 （如上所示） 以 SimpleCircleAdorner<xref:System.Windows.Controls.TextBox>名為*myTextBox*。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 將裝飾項繫結至另一個目前不支援的項目。  
  
## <a name="see-also"></a>請參閱  
 [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)
