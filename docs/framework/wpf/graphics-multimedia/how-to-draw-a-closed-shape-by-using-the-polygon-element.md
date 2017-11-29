---
title: "如何：使用 Polygon 項目繪製封閉的形狀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b38efefa503ec3786b6e40f7b93bac59596b419f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>如何：使用 Polygon 項目繪製封閉的形狀
這個範例示範如何使用來繪製封閉的圖形<xref:System.Windows.Shapes.Polygon>項目。 若要繪製封閉的圖形，請建立<xref:System.Windows.Shapes.Polygon>項目，並使用其<xref:System.Windows.Shapes.Polygon.Points%2A>屬性可指定圖形的頂點。 繪製線條，會自動連接的第一個和最後一個點。 最後，指定<xref:System.Windows.Shapes.Shape.Fill%2A>、 <xref:System.Windows.Shapes.Shape.Stroke%2A>，或兩者。  
  
## <a name="example"></a>範例  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，點的有效語法是以空格分隔清單的逗號分隔 x 和 y 座標組。  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 雖然此範例會使用<xref:System.Windows.Controls.Canvas>包含多邊形，使用多邊形元素 （和其他所有圖形項目） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。  
  
 這個範例是較大範例的一部分如需完整範例，請參閱[圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)。
